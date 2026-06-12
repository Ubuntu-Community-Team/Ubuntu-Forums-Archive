---
title: "fglrx driver not loaded!"
date: 2007-11-10
forum: Desktop Environments
---

### Post by {spitFire} on 2007-11-10
I can't get the fglrx module get loaded automagically during boot. I always get the following after a reboot,

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

However, after I manually INSMOD the fglrx module into the kernel, things work fine!!! But how do I make it load automatically every time during boot?

---

### Post by Laserbeast on 2007-11-10
Post your xorg.conf, please.

---

### Post by {spitFire} on 2007-11-10
I've uploaded my xorg.conf

---

