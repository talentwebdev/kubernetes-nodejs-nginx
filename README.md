# kubernetes-nodejs-nginx
Kubernetes node js repo 

Source[https://www.youtube.com/watch?v=bhBSlnQcq2k]

## Docker commands
Exposing ports 
```
docker run -d -p 8080:80 nginx:latest
```
Exposing multiple ports 
```
docker run -d -p 8080:80 -p 3000:80 nginx:latest
```
Run container with name 
```
docker run --name website -d -p 3000:80 -p 8080:80 nginx:latest
```
Formmat
"ID\t{{.ID}}\nNAME\t{{.Names}}\nIMAGE\t{{.Image}}\nPORTS\t{{Ports}}\nCOMMAND\t{{.Command}}\nCREATED\t{{.CreatedAt}}\nSTATUS\t{{.Status}}\n



## Docker file build 
```
docker build -t user-service-api:latest . 
```

Caching 
```
FROM node:latest 

WORKDIR /app
ADD package*.json ./
RUN npm install

ADD . .

CMD node index.js
```
Not caching
```
FROM node:latest 

WORKDIR /app
ADD . .
RUN npm install

CMD node index.js
```


# Kubernetes
## minikube and kubectl install
https://phoenixnap.com/kb/install-minikube-on-ubuntu

## commands
```
kubectl get nodes
kubectl get pods
kubectl get services
kubectl get deployment 
```

## Pods
pods will not be created/accessed directly via kubectl. Instead it will be access/managed by abstraction layer called Deployments
Usage: 
```
kubectl create deployment NAME --image=image [--dry-run] [options]
kubectl create deployment mongo-depl --image=mongo
```

## Logs
```
kubectl logs [pod name]
```

## Useful debugging
```
kubectl exec -it mongo-depl-5fd6b7d4b4-bmdgg -- bin/bash 
```

## config configuration file
```
kubectl apply -f config-file.yaml
kubectl apply -f nginx-deployment.yaml 
```

## Get all kubernetes containers
```
kubectl get all
```

## Command to get base64 value
```
echo -n 'password' | base64
```

## Command to check pod logs
```
kubectl describe pod mongodb-deployment-8f6675bc5-5l9v6
```

## Command to get pod info with ip addr
```
kubectl get pod -o wide 
```

## How to delete kubenetes components?
```
kubectl delete [component] id
kubectl delete deployement mongo-express
```

## How to assign external ip address to external service(LoadBalancer)? 
```
minikube service mongo-express-service
```