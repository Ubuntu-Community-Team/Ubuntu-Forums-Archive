---
title: "[SOLVED] kubuntu-desktop package error on install"
date: 2008-07-19
forum: Desktop Environments
---

### Post by Separ on 2008-07-19
I tried to install the kubuntu-desktop package from ubuntu and got this:
```
Errors were encountered while processing:
 kdm
 kubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up kdm (4:3.5.9-0ubuntu7.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing kdm (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on kdm; however:
  Package kdm is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdm
 kubuntu-desktop

```

It does work when I change session but there is no compiz-fusion working. Can these errors just be ignored since it works?

And also how do I install KDE4 in the KDE session?

---

### Post by Separ on 2008-07-19
Solved it myself, nevermind :D

---

### Post by king EZi on 2010-01-24
> **Separ said:**
> Solved it myself, nevermind :D

Im having the same problem. How did you solve this one??

---

