---
title: "libvnc.so in Xorg + gdm = corrupted image in vncviewer"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Georges on 2006-08-11
Hi

I added libvnc.so to Xorg so I can also view my linux from a remote PC on the gdm login. This actually works!

But after logging in, someone (who???) changes resolution and the desktop gets completely messed (only in the vncviewer) because libvnc.so somehow does not know that the resolution has been changed.

On the real PC running the X server, it all looks fine.

I guess it's the same issue that this guy has: [http://www.realvnc.com/pipermail/vnc-list/2006-June/055273.html](http://www.realvnc.com/pipermail/vnc-list/2006-June/055273.html)

---

