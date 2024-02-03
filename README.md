# Introduction
Retrieve the data stored in etcd by Kubernetes, based on the open-source etcdhelper.  
Change the output to YAML, and modify the jsonserializer.NewSerializer(Deprecated) function to 
jsonserializer.NewSerializerWithOptions.

# Build
```
$ git clone https://github.com/ruo91/etcdhelper-custom.git
$ cd etcdhelper-custom
$ go build .
$ cp etcdhelper-main /usr/bin/
```

# How to use
```
$ etcdhelper-main \
-endpoint "http://localhost:2379" \
get /kubernetes.io/config.openshift.io/clusterversions/version
```
```
INFO: Key /kubernetes.io/config.openshift.io/clusterversions/version:
config.openshift.io/v1, Kind=ClusterVersion
apiVersion: config.openshift.io/v1
kind: ClusterVersion
metadata:
  creationTimestamp: "2021-01-15T03:37:38Z"
  generation: 3
  managedFields:
  - apiVersion: config.openshift.io/v1
    fieldsType: FieldsV1
    fieldsV1:
      f:spec:
        .: {}
        f:clusterID: {}
    manager: cluster-bootstrap
    operation: Update
    time: "2021-01-15T03:37:38Z"
  - apiVersion: config.openshift.io/v1
    fieldsType: FieldsV1
    fieldsV1:
      f:spec:
        f:desiredUpdate:
          .: {}
          f:force: {}
          f:image: {}
          f:version: {}
    manager: oc
    operation: Update
    time: "2021-11-15T01:36:05Z"
  - apiVersion: config.openshift.io/v1
    fieldsType: FieldsV1
    fieldsV1:
      f:status:
        .: {}
        f:availableUpdates: {}
        f:conditions: {}
        f:desired:
          .: {}
          f:image: {}
          f:url: {}
          f:version: {}
        f:history: {}
        f:observedGeneration: {}
        f:versionHash: {}
    manager: cluster-version-operator
    operation: Update
    time: "2021-11-15T02:16:43Z"
  - apiVersion: config.openshift.io/v1
    fieldsType: FieldsV1
    fieldsV1:
      f:spec:
        f:channel: {}
    manager: Mozilla
    operation: Update
    time: "2023-01-30T11:17:11Z"
  name: version
  uid: f8610a2a-45a1-4192-ac33-c22b743d1612
spec:
  channel: stable-4.6
  clusterID: 6d8cf474-0f56-4a8d-8985-194764868fd7
  desiredUpdate:
    force: true
    image: registry.ocp46.local/openshift4/release:4.6.48
    version: ""
status:
  availableUpdates: null
  capabilities: {}
  conditions:
  - lastTransitionTime: "2021-01-15T04:12:22Z"
    message: Done applying 4.6.48
    status: "True"
    type: Available
  - lastTransitionTime: "2024-01-15T04:08:52Z"
    status: "False"
    type: Failing
  - lastTransitionTime: "2021-11-15T03:11:08Z"
    message: Cluster version is 4.6.48
    status: "False"
    type: Progressing
  - lastTransitionTime: "2021-01-15T03:37:57Z"
    message: 'Unable to retrieve available updates: Get "https://api.openshift.com/api/upgrades_info/v1/graph?arch=amd64&channel=stable-4.6&id=6d8cf474-0f56-4a8d-8985-194764868fd7&version=4.6.48":
      context canceled'
    reason: RemoteFailed
    status: "False"
    type: RetrievedUpdates
  desired:
    image: registry.ocp46.local/openshift4/release:4.6.48
    url: https://access.redhat.com/errata/RHBA-2021:3829
    version: 4.6.48
  history:
  - completionTime: "2021-11-15T03:11:08Z"
    image: registry.ocp46.local/openshift4/release:4.6.48
    startedTime: "2021-11-15T01:36:12Z"
    state: Completed
    verified: false
    version: 4.6.48
  - completionTime: "2021-01-15T04:12:22Z"
    image: registry.ocp46.local/openshift4/release@sha256:494dd5029f03c7b5c8f4404c9281b5ad435403a6f7a29daecc82381d66cf5d89
    startedTime: "2021-01-15T03:37:57Z"
    state: Completed
    verified: false
    version: 4.6.7
  observedGeneration: 3
  versionHash: UocyDcWTg1A=
```

# Reference
[https://gitee.com/tddh/etcdhelper-custom](https://gitee.com/tddh/etcdhelper-custom)
