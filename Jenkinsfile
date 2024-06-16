pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo building with version
                ls -al
                npm --version
                npm ci
                npm run build
                ls -al
                '''
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo Testing The Build
                ls -al
                test -f build/index.html    
                npm test
                ls -al
                '''
            }
        }

    }
}