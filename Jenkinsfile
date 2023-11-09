pipeline {
    agent { node { label 'AGENT-1' } }
    stages {
        stage('Get Version') {
            steps{
                script{
                    def packageJson = readJSON(file: 'package.json')
                    def packageVersion = packageJSON.version
                    echo "${packageJSONVersion}"
                }
            }
        }
        stage('Install depdencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Unit test') {
            steps {
                echo "unit testing is done here"
            }
        }
     //   sonar-scanner command expect sonar-project.properties should be available
        // stage('Sonar Scan') {
        //     steps {
        //         sh 'ls -ltr'
        //         sh 'sonar-scanner'
        //     }
        // }
        stage('Build') {
            steps {
                // sh 'ls -ltr'
                // sh 'zip -r catalogue.zip ./* --exclude=.git --exclude=.zip'
                echo "Sonar scan done"
            }
        }
        stage('Sast') {
            steps {
                echo "Sast done"
            }
        }
        // install pipeline utility steps plugin, if not installed.
        // stage('Publish Artifact') {
        //     steps {
        //         nexusArtifactUploader(
        //             nexusVersion: 'nexus3',
        //             protocol: 'http',
        //             nexusUrl: '172.31.85.33:8081/',
        //             groupId: 'com.roboshop',
        //             version: '1.0.0',
        //             repository: 'catalogue',
        //             credentialsId: 'nexus-auth',
        //             artifacts: [
        //                 [artifactId: 'catalogue',
        //                 classifier: '',
        //                 file: 'catalogue.zip',
        //                 type: 'zip']
        //             ]
        //         )
        //     }
        // }
        stage('Deploy') {
            steps {
                echo "Deployment"
            }
        }
    }

    post{
        always{
            echo 'cleaning up workspace'
            deleteDir()
        }
    }
}