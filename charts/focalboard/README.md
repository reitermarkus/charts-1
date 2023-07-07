# focalboard

![Version: 4.4.2](https://img.shields.io/badge/Version-4.4.2-informational?style=flat-square) ![AppVersion: 0.9.0](https://img.shields.io/badge/AppVersion-0.9.0-informational?style=flat-square)

Focalboard is an open source, self-hosted alternative to Trello, Notion, and Asana.

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://www.focalboard.com/>
* <https://github.com/mattermost/focalboard>
* <https://github.com/FlipEnergy/container-images/blob/main/focalboard>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://library-charts.k8s-at-home.com | common | 4.5.2 |

## TL;DR

```console
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install focalboard k8s-at-home/focalboard
```

## Installing the Chart

To install the chart with the release name `focalboard`

```console
helm install focalboard k8s-at-home/focalboard
```

## Uninstalling the Chart

To uninstall the `focalboard` deployment

```console
helm uninstall focalboard
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common/values.yaml) from the [common library](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install focalboard \
  --set env.TZ="America/New York" \
    k8s-at-home/focalboard
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install focalboard k8s-at-home/focalboard -f values.yaml
```

## Custom configuration

By default Kubernetes will create several environment variables called service links (see [here](https://kubernetes.io/docs/concepts/services-networking/connect-applications-service/#accessing-the-service) for more information).

Focalboard can be configured with environment variables, so when you deploy this Helm release with a name of `focalboard`,
these service links will conflict with the application.

In order to prevent this, you can disable the creation of these service links by setting `enableServiceLinks: false` in your `values.yaml.

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common)

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| config | string | `"{\n  \"serverRoot\": \"http://localhost:8000\",\n  \"port\": 8000,\n  \"dbtype\": \"sqlite3\",\n  \"dbconfig\": \"/data/focalboard.db\",\n  \"postgres_dbconfig\": \"dbname=focalboard sslmode=disable\",\n  \"useSSL\": false,\n  \"webpath\": \"./pack\",\n  \"filespath\": \"/data/files\",\n  \"telemetry\": true,\n  \"session_expire_time\": 2592000,\n  \"session_refresh_time\": 18000,\n  \"localOnly\": false,\n  \"enableLocalMode\": true,\n  \"localModeSocketLocation\": \"/var/tmp/focalboard_local.socket\"\n}\n"` |  |
| env | object | See below | environment variables. |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"mattermost/focalboard"` | image repository |
| image.tag | string | `"0.9.0"` | image tag |
| ingress.main | object | See values.yaml | Enable and configure ingress settings for the chart under this key. |
| persistence | object | See values.yaml | Configure persistence settings for the chart under this key. |
| service | object | See values.yaml | Configures service settings for the chart. |

## Changelog

### Version 4.4.2

#### Added

N/A

#### Changed

* Upgraded `common` chart dependency to version 4.5.2

#### Fixed

N/A

### Older versions

A historical overview of changes can be found on [ArtifactHUB](https://artifacthub.io/packages/helm/k8s-at-home/focalboard?modal=changelog)

## Support

- See the [Docs](https://docs.k8s-at-home.com/our-helm-charts/getting-started/)
- Open an [issue](https://github.com/k8s-at-home/charts/issues/new/choose)
- Ask a [question](https://github.com/k8s-at-home/organization/discussions)
- Join our [Discord](https://discord.gg/sTMX7Vh) community

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v0.1.1](https://github.com/k8s-at-home/helm-docs/releases/v0.1.1)