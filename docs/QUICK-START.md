#Quick start

In this example you will use S2I Operator to create a S2iBuilder and S2iRun, that simply creates a  ready-to-run image and push to DockerHub.

1. Create a new `s2ibuilder`, all configuration information used in building are stored in `s2ibuilder` .

   ```yaml
   kubectl apply -f - <<EOF
   apiVersion: devops.kubesphere.io/v1alpha1
   kind: S2iBuilder
   metadata:
       name: s2ibuilder-sample
   spec:
       config:
           displayName: "For Test"
           sourceUrl: "https://github.com/sclorg/django-ex"
           builderImage: centos/python-35-centos7
           imageName: kubesphere/hello-python
           tag: v0.0.1
           builderPullPolicy: if-not-present
   EOF
   ```

2. You can use `kubectl get s2ib` to check `s2ibuilder` status.

   ```shell
   kubectl get s2ib
   NAME                RUNCOUNT   LASTRUNSTATE   LASTRUNNAME
   s2ibuilder-sample   2          Successful     s2irun-sample1
   ```

3. To start a building, 