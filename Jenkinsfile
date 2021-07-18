pipeline {
	agent any
	environment {
		DOCKERHUB = 'chenqi830521'
	}

	stages {
        stage('Build Docker Image') {
             steps {
                echo 'Buidling Docker image...'
                   sh 'docker build . -t servian/techchallengeapp:latest'
				   sh 'docker images'
                   // sh 'docker tag techchallengeapp:latest $AWS_ECR/jr_oap_repo:$BUILD_NUMBER'
             }
        }
        // stage('AWS ECR and Docker Login') {
        //     steps{
        //         script {
        //                echo 'Retrieve an authentication token to registry'
        //                sh 'aws ecr get-login-password --region ap-southeast-2 | docker login --username AWS --password-stdin $AWS_ECR'

        //         }
        //     }
        // }
		stage('Push Docker Image') {
			steps {
				echo 'Pushing to DockerHub...'
				sh 'docker pull servian/techchallengeapp:latest'
			}
		}

    //    stage('Executing Gradle Tool'){
    //         steps {
    //             echo 'executing gradle...'
    //             sh 'pwd'
    //             sh 'cd /var/jenkins_home/workspace/oap-backend-springboot'
    //             sh 'chmod +x gradlew'
    //             sh './gradlew -v'
    //         }
    //    }

    //    stage('Deploy to ECS') {
    //         steps {
    //             withAWS(credentials: 'aws-credentials-xiaokai', region: env.AWS_REGION) {
    //                 echo 'Deleting Cloudformation Stack...'
    //                 //如果要删除则使用此命令 sh './gradlew awsCfnDeleteStack awsCfnWaitStackComplete'
    //                 echo 'Creating Cloudformation Stack...'
    //                 sh './gradlew awsCfnMigrateStack awsCfnWaitStackComplete -Penv=uat -Ptag=$BUILD_NUMBER -PVpcId=vpc-d8909dbc -Psubnet1Id=$SUBNET_1ID -Psubnet2Id=$SUBNET_2ID -Pecr=$AWS_ECR -Pregion=$AWS_REGION -PoverNightShutdown=true'
    //             }
    //         }
    //     }
    }

    post {
         success {
             echo "well done"
         }
         failure {
             echo "FAILED"
         }
    }
}