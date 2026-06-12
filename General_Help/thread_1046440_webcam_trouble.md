---
title: "webcam trouble"
date: 2009-01-21
forum: General Help
---

### Post by coops351 on 2009-01-21
im having trouble with my logitech quickchat webcam is there a way that ubuntu will recognise it?

Cheers

Luke

---

### Post by spiderbatdad on 2009-01-21
some more information maybe helpful. Please run ```
lsusb
```
and post output.
Also tell us what apps you are trying to run.

---

### Post by coops351 on 2009-01-21
luke@luke-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:092e Logitech, Inc. QuickCam Chat
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

im trying to run aMSN

---

### Post by spiderbatdad on 2009-01-21
I have not tried to run amsn. You can try to copy/paste this command into your terminal:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so amsn
```

---

