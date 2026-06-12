---
title: "Environment Profiles"
date: 2006-08-11
forum: Desktop Environments
---

### Post by NeoFax on 2006-08-11
Does anyone know if you can boot into grub and then select a profile instead of kernel and then certain servers/daemons startup/shutdown based on the profile selected. i.e. Gaming would turn on X, ALSA, UDEV..., Server would turn off X, and turn on MySQL, Postfix, Apache2...  If not, grub how about a KDE/Gnome/XFCE session that does this type of thing?

---

### Post by Ramses de Norre on 2006-08-11
Runlevels? 
Install sysv-rc-conf and use it to select which services to start in which runlevel, you can change runlevels 2-5 to your choice. Append the number of the runlevel you want to boot into to the kernel line in grub.

---

