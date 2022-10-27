# nginx-ingress

According to the Merriam-Webster dictionary, the meaning of ingress is the act of entering or entrance. In the context of Kubernetes, Ingress is a resource that enables clients or users to access the services which reside in a Kubernetes cluster. Thus Ingress is the entrance to a Kubernetes cluster! Let’s get to know more about it and test it out.

## How to deploy and use Ingress

Now we are going to deploy the Nginx Ingress at Kubernetes in Docker Desktop. We will configure it to access an Nginx web server, a variant for Tomcat web application server and our old beloved Apache web server.

 1. Start your Docker Desktop with Kubernetes Enable. Right click at the Docker Desktop icon at the top right area of your screen (near the left in this cropped screenshot) to see that both Docker and Kubernetes are running.
 2. Clone this repository to get the required deployments YAML files.
 3. Deploy the Ingress Controller. Execute the following to deploy the Ingress Controller.
 ```
 kubectl apply -f .\01-ingress-controller.yaml
 ```
 4. Execute the following to check on the deployment. The pod must be running and the Deployment must be ready.
 ```
 kubectl get all -n ingress-nginx
 ```
 5. Deploy the sample applications. Execute the following to deploy the sample applications.
 ```
 # Deploy the nginx webserver
 kubectl apply -f .\02-nginx-webserver.yaml
 # Deploy the tomcat webserver
 kubectl apply -f .\03-tomcat-webappserver.yaml
 # Deploy the httpd webserver
 kubectl apply -f .\04-httpd-webserver.yaml
 ```
 6. Execute the following to check on the deployments. All pods must be running and all deployments must be ready.
 ```
 kubectl get all
 ```
 7. Deploy the Ingress resources. Execute the following to deploy the Ingress resouces.
 ```
 kubectl apply -f .\05-ingress-resouce.yaml
 ```
 8. Execute the following to check on the Ingress resources.
 ```
 kubectl get ing
 ```
 9. Access the following URLs in your web browser. All URLs should bring you to the intended services.
 ```
 http://demo.localdev.me
 http://demo.localdev.me/tomcat/
 http://httpd.localdev.me
 ```

## Credit

All credit goes to [Jeffry Johar](https://github.com/aburayyanjeffry) on his article at [End Point Dev](https://www.endpointdev.com/blog/2022/10/knocking-on-kubernetes-door/).