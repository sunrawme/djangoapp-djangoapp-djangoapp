@Library("shared") _

pipeline {
    agent any

    stages {

        stage("Hello") {
            steps {
                script {
                    hello()
                }
            }
        }

        stage("Code") {
            steps {
                clone(
                    "https://github.com/sunrawme/djangoapp-djangoapp-djangoapp.git",
                    "main"
                )
            }
        }

        stage("Build") {
            steps {
                script {
                    docker_build("notes-app", "latest", "sunraw")
                }
            }
        }

        stage("Push to DockerHub") {
            steps {
                script {
                    docker_push("notes-app", "latest", "sunraw")
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "This echoes the deploy"

                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
