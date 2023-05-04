pipeline {
    agent any
    stages{
        stage('One'){
            steps {
                echo 'Hi thei is Sudu'
            }
        }
        stage('Two'){
            steps {
                input('Do you want to proceed?')
            }
        }
        stage('Three') {
            when {
                not {
                    branch "master"
                }
            }
            steps {
                echo 'Hello'
            }
        }
        stage('Four'){
            parallel {
                stage('Unit test'){
                    steps {
                        echo "Running the unit test......"
                    }
                }
                stage('Integration test'){
                    agent{
                        docker {
                            reuseNode false
                            image 'ubuntu'
                        }
                    }
                    steps{
                        echo "Running the integration test.."
                    }
                }
            }
        }
    }
}