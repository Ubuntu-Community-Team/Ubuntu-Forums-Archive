---
title: "compiz and cpu usage"
date: 2007-05-09
forum: Desktop Effects &amp; Customization
---

### Post by Ateo on 2007-05-09
When I enable the 3D plugin (the one that makes all the windows pop out before turning) my CPU shoots from 1-3% (normal usage) to 10-13% usage. Is this normal for this plugin?

I'm currently using compiz 0.5.0 because I thought upgrading from the packages in Synaptic (0.3.6) would address my CPU usage but it did not change a thing.

Thanks for any input.

/edit: Back to version 0.3.6

---

### Post by Ateo on 2007-05-10
It appears that switch from AIGLX to XGL solves this issue.

So, I suppose XGL is better for nvidia cards?

I also added --use-cow to compiz startup options:
```
$ sudo gedit /usr/bin/compiz
```
Change
```
COMPIZ_OPTIONS="--no-fbo --ignore-desktop-hints"
```
TO
```
COMPIZ_OPTIONS="--no-fbo --ignore-desktop-hints --use-cow"
```

---

