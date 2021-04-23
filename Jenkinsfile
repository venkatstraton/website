pipeline {
    
    agent any

        stages {

           stage ("Getting Souce Code From Git") {
               steps {
                git 'https://github.com/venkatstraton/MavenBuild.git'
                }
            }

          stage ("cleaning build classes") {
              steps {
                sh 'mvn clean'
               }
            }

            stage ("Compiling The Source Code") {
            steps {
                sh 'mvn compile'
                }
            }

            stage ("Testing The Source Code") {
              steps {
                sh 'mvn test'
                }
            }

            stage ("Generating Artifact") {
              steps {
                sh 'mvn package'
                }
            }

           stage ("Deploying Artifact On Tomcat Server") {
              steps {
               deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://34.227.65.239:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
                }
            }
        }
}
