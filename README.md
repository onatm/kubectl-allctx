# kall: `kubectl` without context switch

Run `kubectl get` on all the contexts found in your `.kube/config`.

## Usage

### `get pods`

```bash
$ kubectl all get pods

Context: north-america
NAME                                READY   STATUS    RESTARTS   AGE
awesome-app-68d74656c5-rzt2z         1/1     Running   0          108d
awesome-resources-79c896db67-g4d5f   1/1     Running   0          108d
awesome-web-68bd99bb44-x5gg8         1/1     Running   0          108d
grafana-777564df5d-dcl4w             2/2     Running   0          74d

Context: west-europe
NAME                                READY   STATUS    RESTARTS   AGE
awesome-app-d7fb8dc96-6w22g          1/1     Running   0          105d
awesome-resources-777564df5d-dcl4w   1/1     Running   0          105d
awesome-web-6449f64fcd-pgphp         1/1     Running   0          105d
grafana-9c57bcc66-f7t9w              2/2     Running   0          74d

$ kubectl all get pods --like app

Context: north-america
awesome-app-68d74656c5-rzt2z         1/1     Running   0          108d

Context: west-europe
awesome-app-d7fb8dc96-6w22g          1/1     Running   0          105d
```

### `get deploy`

```bash
$ kubectl all get deploy

Context: north-america
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
awesome-app         1/1     1            1           108d
awesome-resources   1/1     1            1           108d
awesome-web         1/1     1            1           108d
grafana             1/1     1            1           74d

Context: west-europe
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
awesome-app         1/1     1            1           105d
awesome-resources   1/1     1            1           105d
awesome-web         1/1     1            1           105d
grafana             1/1     1            1           74d

$ kubectl all get deploy --like grafana

Context: north-america
grafana             1/1     1            1           74d

Context: west-europe
grafana             1/1     1            1           74d
```

### `get pv`

```bash
$ kubectl all get pv

Context: north-america
NAME                                       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                                         STORAGECLASS   REASON   AGE
pvc-70ab5227-3dc5-4901-9a3d-9c8542c9f379   10Gi       RWO            Delete           Bound    amazing-namespace/grafana                     default                 74d

Context: west-europe
NAME                                       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                                         STORAGECLASS   REASON   AGE
pvc-8f02ad08-df03-42d9-a9bf-d93338157d15   10Gi       RWO            Delete           Bound    amazing-namespace/grafana                     default                 74d
```

etc.

## Installation

### Manual

You should be able to install `kubectl-all` in any POSIX environment where `Bash` is installed.

- Download `kubectl-all`.
- Either:
  - save it to somewhere in your `PATH`,
  - or save it to a directory, then create a symlink to `kubectl-all` from somewhere in your `PATH`, like `/usr/local/bin`
- Make `kubectl-all` executable (`chmod +x kubectl-all`)

#### Example installation

``` bash
sudo git clone https://github.com/onatm/kall /opt/kall
sudo ln -s /opt/kall/kubectl-all /usr/local/bin/kubectl-all
```
