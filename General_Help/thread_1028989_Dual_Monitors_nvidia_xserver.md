---
title: "Dual Monitors nvidia xserver"
date: 2009-01-02
forum: General Help
---

### Post by dtrot55 on 2009-01-02
hello i am running ubuntu 8.10...i have activated the nvidia drivers and i went into the x server settings and activated my other monitor...went and hit save to x configuration file and i get this error

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.

any ideas??

---

### Post by 2hot6ft2 on 2009-01-02
You have to run it as root for it to save a system file. Close it first then
In a terminal use
```
gksudo nvidia-settings
```
then you will be able to save it.

---

