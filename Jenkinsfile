pipeline {
    agent none
    options {
        skipDefaultCheckout() 
    }
    stages {
        stage ('Build') {
            agent {
                    label 'dind'
            }
            steps {
                sh 'curl -L https://github.com/docker/compose/releases/download/1.14.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose'
                sh 'chmod +x /usr/local/bin/docker-compose'
                sh 'docker-compose up'
            }
            post {
                success {
                    echo "Build stage completed"
                }
                failure {
                    echo "Build stage failed"
                }
            }
        }
    }
    post {
        success {
            echo 'Your predix-cicd-java pipeline has completed.'
        }
        failure {
            echo "There was an error in the predix-cdcd-java pipeline build"
        }
    }
}
