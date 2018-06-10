pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
					sh 'echo "failures, successes, skipped, errors\n1, 5, 2, 3" > summary.csv'
					sh 'echo "failures, successes, skipped, errors\n10, 50, 20, 30" > summary2.csv'

					sh "curl http://localhost:8000/async-load.json --output async-load.json"
					sh "curl http://localhost:8000/sync-load.json --output sync-load.json"
            }
        }
    }
    post {
        always {
            arestocats resultsDatafilesPattern: "*.csv", metricsDatafilesPattern: "*.json", numBuilds: 15
        }
    }
}
