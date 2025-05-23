pipeline {
    agent none
    stages {
        stage('Checkout Code') {
            agent any
            steps {
                git branch: 'source', url:'https://github.com/sofiane1234/cicd_perso.git'
                sh 'ls -R ${WORKSPACE}'
                stash name: 'source-code', includes: '**'
            }
        }
        stage('Build') {

            agent {
                label 'perso-docker-agent-python'
            }
            steps {
                unstash 'source-code'
                sh 'ls -R ${WORKSPACE}'
                sh 'pip install -r back/requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
}
