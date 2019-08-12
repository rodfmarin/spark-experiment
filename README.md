## Spark-Experiment
---

### Mainly hacking around with
- minikube
- kubernetes
- docker
- apache-spark
On Windows for now.


### Notes:
Ran this from a surface laptop.
When Minikube is going and spark is going, things get really slow.
You need a hypervisor installed, i opted for virtualbox.
I handled most installations via [Chocolatey](https://www.chocolatey.org/)
The relevant packages:
```
docker-desktop 2.1.0.1
kubernetes-cli 1.15.2
minikube 1.3.0
virtualbox 6.0.10
vscode 1.37.0
```

I followed this guide mostly
[Deploying Spark on Kubernetes](https://testdriven.io/blog/deploying-spark-on-kubernetes/)

The Dockerfile failed to build for me, it mentioned a missing file.  I opted to pull this person's image from the public registry via

```
docker pull mjhea0/spark-hadoop:2.2.1
```

You have to re-tag this image when it's on the machine via
```
docker tag mjhea0/spark-hadoop:2.2.1 spark-hadoop:2.2.1
```
Otherwise the Kubernetes won't be able to locate the right image on the system.

When you start the spark application, you have to add an entry to the HOSTS file on the system that maps the application's IP to a hostname `apache-spark`  This is covered in the guide, but is important to load the controller's web interface