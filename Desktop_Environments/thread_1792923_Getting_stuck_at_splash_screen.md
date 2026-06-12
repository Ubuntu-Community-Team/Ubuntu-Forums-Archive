---
title: "Getting stuck at splash screen"
date: 2011-06-28
forum: Desktop Environments
---

### Post by neo1786 on 2011-06-28
Hi 
I was building LTIB and encountered a few dependencies missing. so i installed them manually. These were the ones i installed.

gettext
freetype
glib2
libXt(using synaptic)
dbus-glib(using synaptic)
after i installed dbus-glib laptop froze and on rebooting i get stuck at the splash screen

i have access to CL but dont kno wat to do wit it
i am using ubuntu 10.10 on Toshiba satellite

---

### Post by neo1786 on 2011-06-28
bounce

---

### Post by neo1786 on 2011-06-28
i entered the kernel recovery mode, logged in and gave the command startx.. cuz i saw it in some post
i get a bunch of warning messages
```
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found 
```{12 msgs similar to this}
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
waiting for X server to shutdown ddxSigGiveUp: Closing log
```

---

### Post by neo1786 on 2011-06-28
```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
```
both of them fail

---

