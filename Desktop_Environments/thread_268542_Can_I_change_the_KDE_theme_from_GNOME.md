---
title: "Can I change the KDE theme from GNOME?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by hygraed on 2006-09-30
A recent ill-fated installation of KDE over GNOME has left my KDE applications (KolourPaint, Opera) looking pretty funky, where before they meshed rather nicely with my GNOME desktop. Is there an app that will let me change the KDE theme without actually having KDE installed?

---

### Post by aysiu on 2006-09-30
You could try this: ```
sudo aptitude update
sudo aptitude install kcontrol
kcontrol
```

---

### Post by hygraed on 2006-09-30
> **aysiu said:**
> You could try this: ```
sudo aptitude update
sudo aptitude install kcontrol
kcontrol
```

Thanks, that worked great. Opera doesn't look like complete shit anymore. :)

---

### Post by lonelypauly on 2006-09-30
im thinking of reinstalling ubuntu using KDE...will i have any problems with dual monitor Nvidia drivers?

---

### Post by aysiu on 2006-09-30
I don't know much about dual monitor setup, but you can install Nvidia drivers in Kubuntu, same as Ubuntu. In fact, Ubuntu and Kubuntu are essentially the same operating system--just different default packages.

Neither Ubuntu nor Kubuntu comes with Nvidia drivers installed, but you can install it yourself:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

