# Kubernetes Custom Controller - Core Resource Handling

**Note**: the source code is _verbosely_ commented, so the source is meant to be read and to teach

## What is this?

An example of a custom Kubernetes controller that's only purpose is to watch for the creation, updating, or deletion of all pods (in the default namespace). This was created as an exercise to understand how Kubernetes controllers work and interact with the cluster and resources.

## Running

```console
$ git clone https://github.com/trstringer/k8s-controller-core-resource
$ cd k8s-controller-core-resource
$ go run *.go
```

## Inspecting resources in the handler

You are welcome to dump the resources themselves in handler but logging would be extremely verbose (and not interactive). I recommend you use a debugger...

```console
$ dlv debug
(dlv) b main.ObjectCreated
(dlv) c
```

You can then trigger an event by creating a deployment of nginx...

```console
$ kubectl run nginx --image=nginx
```

The breakpoint should be hit and you can analyze in the debugger the object...

```
(dlv) p obj
```
