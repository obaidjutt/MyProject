pipeline {
    agent any  // This specifies that the pipeline can run on any available agent (machine)

    environment {
        // Define environment variables, like paths, credentials, etc.
        NODE_HOME = "/usr/local/node"
        PATH = "${env.PATH}:${NODE_HOME}/bin"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                git'https://github.com/obaidjutt/MyProject.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // Run commands to install dependencies
                script {
                    // Example: installing dependencies using npm (if you're working with Node.js)
                    sh 'npm install'
                }
            }
        }

        stage('Run Tests') {
            steps {
                // Run the tests
                script {
                    // Example: running tests with npm
                    sh 'npm test'
                }
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Archive any build artifacts (such as JAR, WAR, or other files)
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }
    }

    post {
        success {
            // Actions to take after the pipeline succeeds
            echo 'Pipeline succeeded!'
        }
        failure {
            // Actions to take after the pipeline fails
            echo 'Pipeline failed!'
        }
    }
}
