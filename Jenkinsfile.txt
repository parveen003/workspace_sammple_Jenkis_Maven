
Conversation opened. 3 messages. All messages read.

Skip to content
Using Gmail with screen readers

8 of 1,530
 
Fwd: Please make sure that you installed Plugins below in Jenkins 
Inbox
x 

Sudhakar Vaddi <sudhakarvaddi11@gmail.com>
Feb 23 (6 days ago)
to ARVIND, me, Rajesh, nanigovvala114. 



Inline image 1

On Mon, Nov 27, 2017 at 12:12 PM, Sudhakar Vaddi <sudhakarvaddi11@gmail.com> wrote:


On Mon, Nov 27, 2017 at 10:52 AM, Sudhakar Vaddi <sudhakarvaddi11@gmail.com> wrote:
pipeline {
    agent any
                                    
    stages {
        stage ('Compile Stage') {
            steps {
                echo 'Compiling ... '
                }
            }
        stage ('Testing Stage') {
            steps {
                echo 'Testing ... '
                }
            }
        stage ('Deployment Stage') {
            steps {
                echo 'Deploying ... '
                }
            }                
        }    
    }

On Sat, Nov 25, 2017 at 10:28 PM, Sudhakar Vaddi <sudhakarvaddi11@gmail.com> wrote:
Dear Students,

Please make sure that you installed Plugins below in Jenkins:
Jenkins Plug-ins to install

1) Build pipeline
2) build timeout
3) email extension plug-in
4) github branch service plug-in
5) gradle plug-in
6) groovy
7) metrics plug-in
8) pipeline maven integration plug-in
9) pipeline github grovvy libraries
10) pmd pulg-in
11) ssh salves pulg-in
12) time stamp
13) workspace clean-up plug-in

Regards
Sudhakar Vaddi

On Thu, Nov 16, 2017 at 9:47 AM, Sudhakar Vaddi <sudhakarvaddi11@gmail.com> wrote:








Sudhakar Vaddi <sudhakarvaddi11@gmail.com>
AttachmentsFeb 27 (2 days ago)
to ARVIND, me, Rajesh, nanigovvala114. 

4 Attachments

Sudhakar Vaddi <sudhakarvaddi11@gmail.com>
Feb 27 (2 days ago)
to ARVIND, me, Rajesh, nanigovvala114. 
pipeline {
agent any
stages {
stage ('Compile Stage') {
steps {
bat 'mvn clean compile'
}
}
stage ('Testing Stage') {
steps {
bat 'mvn test'
}
}
stage ('Packaging Stage') {
steps {
bat 'mvn package'
}
}
}
}

	
Click here to Reply, Reply to all, or Forward
2.39 GB (15%) of 15 GB used
Manage
Terms - Privacy
Last account activity: 1 hour ago
Details

pipeline {
	agent any
	
	stages {
		stage ('Compile Stage') {
			steps {
				withMaven(maven : 'apache-maven-3.5.0'){
					sh 'mvn clean compile'
				}
			}
		}

		stage ('Testing Stage') {
			steps {
				withMaven(maven : 'apache-maven-3.5.0'){
					sh 'mvn test'
				}
			}
		}
		stage ('Installing Stage') {
			steps {
				withMaven(maven : 'apache-maven-3.5.0'){
					sh 'mvn install'
				}
			}				
		}	
		stage ('Deployment Stage') {
			steps {
				withMaven(maven : 'apache-maven-3.5.0'){
					sh 'mvn deploy'
				}
			}				
		}
	}
}