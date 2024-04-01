//DECLARATIVE

pipeline {
	agent any
	//agent {docker {image 'maven:3.6.3'}}
	environment{
		dockerHome =tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout') {
			steps{
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "BUILD_JOB - $env.JOB_NAME"
				echo "BUILD_URL - $env.BUILD_URL"
				echo "BUILD_TAG - $env.BUILD_TAG"
			}
		}
		stage('Compile') {
			steps{
				sh "mvn clean compile"
			}
		}
				stage('Test') {
			steps{
				sh "mvn test"
			}
		}
				stage('Integration Test') {
			steps{
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
	}
	post {
		always {
			echo 'I am awesome. I run always'
		}
		success {
			echo 'I run on success'
		}
		failure {
			echo 'I run on failure'
		}
		/*changed{
			echo 'Build status changed'
		}*/
	}
}

//SCRIPTED
/*node {
		echo "Build"
		echo "Test"
		echo "Integration Test"
	}
*/
