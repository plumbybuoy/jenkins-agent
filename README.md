# jenkins-agent

Setting Up hashtag#Jenkins Slaves on GCP VMs: Step-by-Step Guide 🎉

1. Provision GCP VMs:

-Create two VMs on Google Cloud Platform: one with Cent-OS, one with Ubuntu.
-Ensure both have proper network and security settings.

2. Install Java:

-On both VMs, install Java if it's not already present. Jenkins requires it to run.

3. Install Jenkins Slave Agent:

-Download the Jenkins slave agent JAR file (agent.jar) from your Jenkins server.

4. Configure Slave Nodes in Jenkins:

-Go to Jenkins Dashboard -> Manage Jenkins -> Manage Nodes and Clouds.
-Click on "New Node", name it (e.g., CentOS-Slave), select "Permanent Agent", and configure the necessary details:
-Remote root directory: a directory for Jenkins to store data on the slave.
-Labels: set labels to differentiate between CentOS and Ubuntu slaves.
-Usage: set how Jenkins should use this slave.

5. Set Up Slave on Cent-OS VM:

-SSH into your Cent-OS VM.
-Create a directory for Jenkins agent, and move the downloaded agent.jar into this directory.
-Run the agent with the following command:

java -jar agent.jar -jnlpUrl <JENKINS_URL>/computer/<NODE_NAME>/slave-agent.jnlp -secret <SECRET> -workDir "<DIR>"

6. Set Up Slave on Ubuntu VM:

-SSH into your Ubuntu VM.
-Similar to Cent-OS, create a directory for the agent and move the agent.jar file.
-Run the agent using the same command as above.

7. Verify Connection:

-Go back to Jenkins Dashboard -> Manage Nodes and Clouds.
-Ensure both Cent-OS and Ubuntu slaves are connected and online.
