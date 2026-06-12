---
title: "No Animation On Default Ubuntu Splash Screen"
date: 2011-04-21
forum: Desktop Environments
---

### Post by jonbwilson on 2011-04-21
I recently performed a fresh install of Ubuntu 10.10 on a new hard disk, and I've noticed that for whatever reason, the animation isn't working on the default Ubuntu splash screen on startup. It does work on the splash screen when I shut down, oddly enough.

I haven't tried to change my splash screen or messed around with resolution settings or anything like that, so I'm not sure what to check.

Any ideas on how I can fix that?

---

### Post by jonbwilson on 2011-04-22
I hate bumping threads, but here I am doing it anyway.  Anybody got any bright ideas?

---

### Post by deconstrained on 2011-04-22
What video hardware are you using? There's a chance you'll be able to get it working properly by using the uvesafb module and modifying your /etc/default/grub to include the necessary kernel parameters for a nice hi-res plymouth animation.

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

It worked for me at least.

---

### Post by rolfijn on 2011-05-08
Well, the OP stated that it does work on shutdown, so it seems the graphics hardware should be able to show the graphic startup animation.

I have the same issue (I think). The resolution on my laptop seems to be set correctly to 1366x768 when the grub boot menu is displayed and after that when the system is starting up. But instead of a nice graphical Ubuntu logo in the center I get a purple screen with a sort of "ascii" line in the upper left corner stating: Ubuntu 11.04 and 4 color changing dots on the next line. On shutdown it **does** display the expected graphical screen. I run Ubuntu 11.04 on a Lenovo Edge 13 (Intel version) of which lspci says that it's equipped with a "VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])".

There seem to be quite some posts about Plymouth in Natty, but most seem to be related to ATI/Nvidia hardware and/or an incorrect resolution.

---

