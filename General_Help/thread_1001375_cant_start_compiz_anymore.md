---
title: "cant start compiz anymore ??"
date: 2008-12-03
forum: General Help
---

### Post by anhvu2875 on 2008-12-03
after follow this :[https://launchpad.net/~xorg-edgers/+archive](https://launchpad.net/~xorg-edgers/+archive) my compiz not work anymore ??! :(:(:(:(

```
anhvu2875@ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x720) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

---

### Post by anhvu2875 on 2008-12-03
noone ???? ((

---

### Post by mhh91 on 2008-12-04
it says "for Hard-core testers" only,it's a possibility there's bugs in them

---

### Post by anhvu2875 on 2008-12-04
**mhh91**
yes and now i wanna get compiz work back ! ((

---

### Post by mhh91 on 2008-12-04
try reinstalling xorg

---

### Post by eternalnewbee on 2008-12-04
Have you checked if your graphic card is working properly?
To do that, go to: **Main Menu > System > Administration > Hardware Drivers**.

---

### Post by amauk on 2008-12-04
you need to update your graphics drivers

Xorg has changed, so you need to reinstall your drivers (if any exist) for the new xorg version

---

### Post by anhvu2875 on 2008-12-04
im using Intel VGA card so i checked Hard Drivers and see nothing ??!

---

### Post by eternalnewbee on 2008-12-04
> im using Intel VGA card so i checked Hard Drivers and see nothing ??!
Don't worry about that. It only means that you've got an onboard graphic card.
I've seen several posts here, where people just reinstalled compiz, and their problems were solved. You could give it a try.

---

### Post by anhvu2875 on 2008-12-05
**eternalnewbee**
i tried to reinstall ''compiz'' with synaptic but the same prob ! ((

---

