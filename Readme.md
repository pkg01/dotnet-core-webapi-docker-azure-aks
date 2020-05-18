These are the commands used to perform this experiment.

#### Create a docker image for dotnet core application (webapi)

1. Create a dotnet core webapi

   ```
   dotnet new webapi -o webapi
   ```

2. Create the Dockerfile to publish dotnet core application and to create an image containing published application

   ```
   Dockerfile
   ```

3. Build the docker image

   ```
   docker build -t pkg01/webapi:v1 .
   ```

   or create a tag for azure container registry

   ```
   docker build -t [registry uri]/webapi:v1 .
   ```

4. Push docker image to docket hub repository

   ```
   docker login
   docker push pkg01/mywebapi:v1
   ```

   or to azure container registry

   ```
   docker login
   docker push [registry uri]/mywebapi:v1
   ```

Resources :

https://docs.docker.com/engine/examples/dotnetcore/

#### Run docker container locally

1. Run following command to run container on local system

   ```
   docker run -it --rm -p 80:80 --name webapi pkg01/webapi:v1
   ```

2. Go to http://localhost/api/values in favorite browser.

#### Deploy dotnet core container to Azure kubernetes cluster

1. Create an Azure kubernetes cluster on azure portal.

2. Login to azure using azure cli

```
az login
```

3. Set default subscription

```
az account set --subscription [subscription name]
```

4. Get azure kubernetes cluster credentials

```
az aks get-credentials -g [resource group name] -n [cluster name]
```

5. Deploy K8s yml file

```
kubectl apply -f k8s.yml
```

6. Get Service Ip

```
kubectl get services
```
