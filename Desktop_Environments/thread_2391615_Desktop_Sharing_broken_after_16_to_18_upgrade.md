---
title: "Desktop Sharing broken after 16 to 18 upgrade"
date: 2018-05-11
forum: Desktop Environments
---

### Post by DigiAngel on 2018-05-11
Topic...going to the Desktop Sharing preferences crashes out.  This upgrade apparently kept Unity.  Anyone else seeing this?

---

### Post by rupesg on 2018-05-11
Yep - same here. Using Ubuntu 18.04 and Unity. Not used Desktop Sharing before but just curious as I find my way around the system.

---

### Post by DigiAngel on 2018-05-12
Looks like this is related to unity-control-center:

```
May 12 08:27:36 analysis unity-control-c[17749]: Settings schema 'org.gnome.Vino' does not contain a key named 'enabled'
```

/org/gnome is completely missing a Vino key.  Related ubuntu bug:

[https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1741027]("https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1741027")

---

