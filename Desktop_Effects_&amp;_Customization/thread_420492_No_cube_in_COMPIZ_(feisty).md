---
title: "No cube in COMPIZ (feisty)"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by el mariachi on 2007-04-23
It was working until awhile ago... after i installed (and uninstalled) avant window navigator the cube animation stopped showing up when you change workspaces. everything else runs flawlessly. :confused:

---

### Post by icechen1 on 2007-04-23
Go in terminal and tape:
```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

```and```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

```

---

