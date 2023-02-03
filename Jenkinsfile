/* Requires the Docker Pipeline plugin */
pipeline {
    agent { any { image 'python:3.10.7-alpine' } }
    stages {
        stage('build') {
            steps {
                retry(3) {
                    sh './flakey-deploy.sh'
                }

                timeout(time: 3, unit: 'MINUTES') {
                    sh './health-check.sh'
                }
            }
        }
    }
}
