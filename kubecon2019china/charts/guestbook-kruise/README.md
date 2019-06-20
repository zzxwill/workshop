# guestbook: an example chart for educational purpose.

This chart provides example of some of the important features of Helm.

The chart installs a [guestbook](https://github.com/cloudnativeapp/guestbook) application.

The chart use [Kruise](https://github.com/openkruise/kruise) as workloads so in-place upgrade is possible (Awesome!).

## Installing the Chart

Add the repository to your local environment:
```bash
$ helm repo add apphub https://apphub.aliyuncs.com
```

To install the chart with release name (application name) of `guestbook-kruise`:

```bash
$ helm install guestbook-kruise apphub/guestbook
```

## Configuration

The following tables lists the configurable parameters of the chart and their default values.

| Parameter                  | Description                                     | Default                                                    |
| -----------------------    | ---------------------------------------------   | ---------------------------------------------------------- |
| `image.repository`         | Image repository                                | `resouer/guestbook`                                         |
| `image.tag`                | Image tag                                       | `v1`                                                       |
| `image.pullPolicy`         | Image pull policy                               | `Always`                                                   |
| `service.type`             | Service type                                    | `LoadBalancer`                                             |
| `service.port`             | Service port                                    | `3000`                                                     |
| `redis.slaveEnabled`       | Redis slave enabled                             | `true`                                                     |
| `redis.port`               | Redis port                                      | `6379`                                                     |

Specify each parameter using the `--set [key=value]` argument to `helm install`. For example,

```bash
$ helm install guestbook-kruise apphub/guestbook --set service.type=NodePort
```

If you are using minikube:

```bash
$ minikube service guestbook-kruise
```

## Use Kustomize to configure the application

TBD

### Uninstalling the Chart

To completely uninstall/delete the `guestbook-kruise` deployment:

```bash
$ helm uninstall guestbook-kruise
```

The command removes all the Kubernetes components associated with the chart and deletes the release.