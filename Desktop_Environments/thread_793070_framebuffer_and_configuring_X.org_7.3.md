---
title: "framebuffer and configuring X.org 7.3"
date: 2008-05-13
forum: Desktop Environments
---

### Post by finite9 on 2008-05-13
How do I now configure xorg.conf by hand when it is auto configuring?  Can I still set the "driver"??

Can I use the framebuffer with an nVidia 7600Go?  How do I enable it?  I remember that you just set the driver to FBDev before but now in Hardy I am unsure if I can still do this.

---

### Post by Zorael on 2008-05-13
Regarding driver, sure, you can manually override the autodetection by adding it to xorg.conf. X.org will only use nv anyway (and other non-proprietary drivers) unless explicitly told not to, so go ahead.

As for framebuffers, I didn't have to enable any with the Hardy kernels. Just make the necessary modifications to your menu.lst.

As for available modes;
```
$ sudo aptitude install hwinfo
$ sudo hwinfo --framebuffer
```

---

