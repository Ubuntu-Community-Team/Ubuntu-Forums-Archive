---
title: "problem installing xine-lib"
date: 2006-01-16
forum: General Help
---

### Post by 40%TUX on 2006-01-16
hi all,
trying to install latest version (1.1.1) of xine-lib and i get following error after ./configure:
```
*********************************************************
WARNING! No X11 output plugins will be built.

For some reason, the requirements for building the X11 video
output plugins are not met. That means, that you will NOT be
able to use the resulting xine-lib to watch videos in a window
on any X11-based display (e.g. your desktop).

If this is not what you want, provide the necessary X11 build
dependencies (usually done by installing a package called
XFree86-devel or similar) and run configure again.
*********************************************************

```

i couldn't find xfree86-devel and have no idea what can be used insted of it. if you got any ideas please...

thnx in advance

---

### Post by schilcha on 2006-01-17
try installing "libx11-dev"

Hope that helps!

---

