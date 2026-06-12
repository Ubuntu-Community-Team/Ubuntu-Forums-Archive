---
title: "deb files issues"
date: 2009-05-16
forum: Desktop Environments
---

### Post by num on 2009-05-16
Hello,

I tried installing Exacq deb file package on Kubuntu 9.04 but it crashes giving me this error:

> Dependency is not satisfiable: ntp-server|ntp

But on Ubuntu 9.04 it installs without issues. What's going on?

---

### Post by SuperSonic4 on 2009-05-16
My guess would be that ntp-server is in GNOME but not in KDE by default. I would look in KPackagekit for the dependency

---

