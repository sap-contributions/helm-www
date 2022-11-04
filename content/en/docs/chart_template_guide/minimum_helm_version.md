---
title: "Appendix: Minimum Helm Version"
description: "How to require a minimum Helm version"
weight: 16
---

If you want make use of Helm features, that where added in a recent minor release
of Helm, it is wise to require a minimum Helm version.

The recommended way of doing this is to create a file called
`minimum_helm_version.tpl` in your `templates` folder with the following content:

```
{{- if semverCompare "<3.11.0-0" .Capabilities.HelmVersion.Version }}
  {{- fail "This chart requires helm version 3.11 or higher" }}
{{- end }}
```

Obviously you will need to change `3.11` to whatever version you need. It is
recommended to use the earliest version, that contains all the features you
require, as the minimum version.
