pipeline {
    agent any
    stages {
        stage('One') {
                steps {
                        echo 'Hi, this is Sukhbeer'
                }
        }
	      stage('Two'){  
                steps {
                  input('Do you want to proceed?')
                }
	      }
        stage('Three') {
                when {
                        not {
                                branch "master"
                        }
                }
                steps {
			                  echo "Hello from non master"
                }
        }
        stage('Four') {
                parallel {
                        stage('Unit Test') {
                                steps{
                                        echo "Running the unit test in parallel..."
                                }
                        }
                        stage('Integration test') {
                          agent {
                                  docker {
                                          reuseNode true
                                          image 'ubuntu'
                                  }
                          }
                          steps {
                            echo 'Running the integration test..'
                          }                 
			          }  
        }
      }
   }
}
