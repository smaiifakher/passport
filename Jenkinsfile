pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            credentialsId: '312f845b-c93f-40bf-989e-b0db8200e41a',
                            url: 'https://github.com/smaiifakher/passport']]])
                }
            }
        }
        stage('Composer') {
             steps{
                script{
                    sh "composer install"
                }
            }
        }
        stage('Npm') {
            steps{
                script{
                    sh "npm install"
                }
            }
        }
        stage ('code quality'){
            steps{
                sh 'cp .env.example .env'
            }
        }

        stage('Generate') {
            steps{
                script{
                    sh "php artisan key:generate"
                }
            }
        }

        stage('Serve') {
            steps{
                script{
                    sh "php artisan serve"
                }
            }
        }
    }
}
