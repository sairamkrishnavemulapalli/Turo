# Turo - Repo name
This repo is accomplish the interview tasks.

## Prerequisities 
1. EKS cluster setup
2. Have the kubeconfig file to access the cluster.
3. Argo CD already installed on the cluster.
   Following the instructions: https://argoproj.github.io/argo-cd/getting_started/


## Usage
Note: Argo CD has an app - `wordpress2` configured to use this repo as source of truth. 
Please try to run the sync first and then dry-run for testing it prior to deployment.

## Explanation

The repo has the required config files to deploy a wordpress app which connects to a local MySQL DB inside the EKS cluster.

MySQL config

1. Creting the presistent volume on a hostpath.
2. Creating the volume claim to claim the volume we created.
3. Creating a secret to store the MySQL password.
4. Creating the deployment for MySQL
5. Exposing the deployment as a service type - cluster IP.

Wordpress config

1. Creting the presistent volume on a hostpath.
2. Creating the volume claim to claim the volume we created.
3. Creating the deployment for Wordpress.
   The deployment gets the MySQL DB name from the `$WORDPRESS_DB_HOST` and DB password from the secretKeyRef. We will be using the sceret created as part of the MySQL config.
4. Exposing the deployment as a service type - NodePort.

