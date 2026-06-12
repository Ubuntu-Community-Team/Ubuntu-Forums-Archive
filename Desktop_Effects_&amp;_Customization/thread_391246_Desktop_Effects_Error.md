---
title: "Desktop Effects Error"
date: 2007-03-22
forum: Desktop Effects &amp; Customization
---

### Post by jsmidt on 2007-03-22
I installed desktop-effects.  When I run it I get this error:

The Composite extension is not available

modinfo: could not open /lib/modules/2.6.20-12-386/volatile/fglrx.ko: No such file or directory
modinfo: could not open /lib/modules/2.6.20-12-386/volatile/fglrx.ko: No such file or directory

nvidia hardware not available



Does anybody know what this is?  I have an ATI card so I don't know what the nvidia message is about.

---

### Post by adam.tropics on 2007-03-23
Just a thought, have you disabled composite in your xorg.conf, and is xgl actually installed?

---

