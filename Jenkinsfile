pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'hostname;uptime;ip a'
                sh 'env'
            }
        }
    }
    post {
        always {
            emailext (
                subject: "Jenkins: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """<p>${env.BUILD_STATUS}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
                <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
                to: "sun76459@gmail.com"
            )
        }
        success {
            echo 'success - This will run only if successful'
        }
        failure {
            echo 'failure - This will run only if failed'
        }
        unstable {
            echo 'unstable - This will run only if the run was marked as unstable'
        }
        changed {
            echo 'changed - This will run only if the state of the Pipeline has changed\nFor example, if the Pipeline was previously failing but is now successful'
        }
    }
}
