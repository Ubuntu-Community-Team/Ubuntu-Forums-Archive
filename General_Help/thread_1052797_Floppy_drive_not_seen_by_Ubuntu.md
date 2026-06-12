---
title: "Floppy drive not seen by Ubuntu"
date: 2009-01-28
forum: General Help
---

### Post by tempus on 2009-01-28
For some reason Ubuntu 8.10 does not see my floppy drive which I do use from time to time. Does Ubuntu not support this hardware any longer?:p

How does one install a program while in Ubuntu. I wish to install the newest version of xsane and don't seem to know how to do this.:confused:

---

### Post by TheLions on 2009-01-28
Ubuntu supports floppy but it is just disabled by default (who in usb era uses floppy?)
to temporary enable it kick in this in terminal:
```
sudo modprobe floppy
```

---

### Post by madsmaddad on 2009-01-28
Thank You. Just the reply I needed. 

Madsmaddad.

---

### Post by tempus on 2009-01-28
> **TheLions said:**
> Ubuntu supports floppy but it is just disabled by default (who in usb era uses floppy?)
to temporary enable it kick in this in terminal:
```
sudo modprobe floppy
```
Thanks for that
tempus

---

