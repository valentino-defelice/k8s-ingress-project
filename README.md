# Kubernetes Multiple Services Domain

This is an approach to manage multiple services with different domains using NGINX, dnsmasq and Kubernetes.

## Prerequisites
1. NGINX ingress installed on cluster
2. dnsmasq configured on local machine to manage local dns

## Files
You will find couple files in this directory, basically:
- **ingress.yaml** - contain the nginx configuration
- **webserver.yaml** - simple kubernetes deployment. It will deploy a nodejs server with it services.
- **valentino-web.yml** - same thing than webserver but different pod name.

## Execution steps
Once you got the cluster running with nginx ingress configured, just:
1. kubectl apply -f valentino-web.yaml
2. kubectl apply -f web-server.yaml
3. kubectl apply -f ingress.yaml
4. Configure dnsmasq to redirect `*.hello-world.loc` to your local cluster ip
5. Open a web browser and access to this local domain, it will display the name of the pod.


## TO-DO
1. Standarize and automate ingress rules.
2. Create or use a basic odoo image
3. Deploy postress pod or just host a postgress database in your local machine and set up parameters in odoo.

