---
title: "fluxbox and usb devices"
date: 2006-01-16
forum: Desktop Environments
---

### Post by hollowhead on 2006-01-16
I've predominately switched from gnome/metacity to fluxbox (at least until E DR17 is stable) since the themes rock and the interface is simpler.  I've got it to do most things I want but two allude me.  One of these is mounting my usb stick device.  In gnome/metacity plugging the device in brings its Nautalus icon up on the desktop allowing you to copy files to and from it.  How do I access it in fluxbox not found a way since it is not listed in etc/fstab?  Ta.

---

### Post by Ampersand on 2006-01-16
If you want removal media to be automatically mounted, you can edit your ~/.fluxbox/startup file and add 
```
gnome-volume-manager
```
somewhere in the file. You can also use disks-admin, which may have found its way into your fluxbox menu or can be called from a terminal using
```
sudo disks-admin
```

---

### Post by hollowhead on 2006-01-16
Cheers I'll try both.

---

### Post by hollowhead on 2006-01-17
gmome-volume-manager worked a treat thanks Ampersand

---

