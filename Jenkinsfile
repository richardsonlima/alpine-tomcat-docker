pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t richardsonlima/alpine-tomcat:jdk8tomcat8 .'
            }
        }
        stage('Push to dockerhub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                sh 'docker push richardsonlima/alpine-tomcat:jdk8tomcat8'
            }
         }
      }
   }
}
