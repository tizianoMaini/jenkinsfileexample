pipeline {
    agent any
    stages {
        stage('clean docker images') {
            steps{
                sh 'docker rmi $(docker images | grep "<none>" | awk \'{print $3}\')'
            }
        }

    }
    post {
        failure {
            mail to: 'tiziano.maini@euei.it',
                 subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
}
