pipeline {
      environment {
            registry = "omaralaoui1999/app_test_argocd"
            registryCredential = 'dockerhub_id'
            dockerImage = ''
                  }
      agent any
      stages {
              stage('Cloning our Git') {
              steps {
                     git 'https://github.com/omaralaoui1/simple-web-app-with-Docker.git'
                      }
               }
              stage('Building our image') {
              steps{
                 script {
                         app = docker.build("app_web/test")
                        }
                     }
                }
              stage('Deploy our image') {
                        steps{
                            script {
                                  docker.withRegistry('https://registry.hub.docker.com', 'git') {                  
                                             app.push("${env.BUILD_NUMBER}")            
                                             app.push("latest")        
                                            } 
                                      }
                               }
                      }
}
}

