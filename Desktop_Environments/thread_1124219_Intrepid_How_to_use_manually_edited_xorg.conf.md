---
title: "Intrepid: How to use manually edited xorg.conf?"
date: 2009-04-13
forum: Desktop Environments
---

### Post by wolfchri on 2009-04-13
Hello,

my problem:

Intrepid does no longer identifiy my mother's screen (Belinea 10 30 40) on a Intel i945 chipset and tries to drive it outside its frequency range which results in a black screen as the monitor turns itself off for protection.

I did create a working /etc/X11/xorg.conf but first, Ubuntu tries to autodetect the screen all the time which now results in an xorg error "device not found". After that, I get the emergency screen and when I click ok 3 times (for the low resultion Gnome desktop), I get in fact my perfect xorg setup in high resolution and flickerfree.

So my problem basically is: How can I tell xorg to use ONLY the config file in /etc/X11/xorg.conf and not try to autodetect my screen?

---

### Post by Aubergines on 2009-04-13
Can you post the xorg.conf? and may be the /var/log/Xorg.0.log as well.

If the resolutions and may be valid modelines are set in the config I didn't think it would autodetect.

Having said that there are loads of options avaliable, take a look in
```
man xorg.conf
```
there may be something there to stop autodetecting.

---

