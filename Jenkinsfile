pipeline{
    agent none
    
    stages{
        stage('build'){
            agent{
                label'builtnode'
            }
            steps{
                deleteDir()
                
                sh'''
                git clone https://github.com/ramnasmuhammad15-tech/sample.git
                
                ls -la 
                '''
                stash name:'webpage', includes:'sample/**'
            }
        }
        stage('deploy'){
            agent{
                label 'deploynode'
            }
            steps{
                deleteDir()
                
                
                unstash 'webpage'
                sh'''
                rm -rf /var/www/html/*
                cp -r sample/* /var/www/html
                ls -la /var/www/html/
                '''
            }
        }
    }
}
