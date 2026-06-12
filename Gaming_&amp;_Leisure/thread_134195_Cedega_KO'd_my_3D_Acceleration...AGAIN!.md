---
title: "Cedega KO'd my 3D Acceleration...AGAIN!"
date: 2006-02-21
forum: Gaming &amp; Leisure
---

### Post by kudu on 2006-02-21
A game refused to run in Cedega and locked up necessitaing a ctl-alt-backspace  to restart X. Now my FPS has dropped from 12000+ to 60! I tried re-enabling my Nvidia driver with sudo nvidia-glx-config enable but got an error message stating my /etc/X11/xorg.conf had been altered (by me of course, hashed out GLcore and dri, ensured "nv" read "nvidia", and added Option "NoLogo"), and something about recalculating the checksum with md5.

I then tried restoring my xorg.conf with my backup copy but the FPS remains 60!
Even when I re-edit to hash out GLcore, dri, etc.

How do I fix this without having to reinstall the whole OS again ???

Yours truly,
frazzled

Got it covered!  \\:D/

---

