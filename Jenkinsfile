pipeline {
    agent any
        stages{
            stage('Git Checkout'){
                steps{
                    git 'https://github.com/samridhi97/parking_frontend.git'
                }
            }
            stage('Build') {
                steps{
                    sh 'npm install'
                    sh 'npm run build'
                    sh 'npm audit fix'
                }
            }
            stage('Deploy'){
                steps{
                    sh 'cp -r $WORKSPACE/builds /opt/apache-tomcat-9.0.31/webapps'
                    sh 'curl -u admin:admin http://3.133.113.126:8888/manager/reload?path=/builds'
                }
            }
            }
        }
