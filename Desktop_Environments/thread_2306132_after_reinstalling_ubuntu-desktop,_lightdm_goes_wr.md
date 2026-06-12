---
title: "after reinstalling ubuntu-desktop, lightdm goes wrong"
date: 2015-12-12
forum: Desktop Environments
---

### Post by michael337 on 2015-12-12
So, after reinstalling ubuntu -desktop, and gdm, lightdm won't let me log out of my account.
It says that the system is running in low graphics mode. So can anyone help me pls?


I run ubuntu 15.10 on a think pad t410 25222AU

---

### Post by grahammechanical on 2015-12-12
I do not think that it is possible to have both GDM & LightDM working at the same time. I think that we have to stop one display manager before starting the other. Why did you need to re-install ubuntu-desktop? why did you install GDM? Ubuntu uses LightDM.

As the system is running in low graphics mode you could try using the open source video driver or another proprietary video driver.

Regards.

---

### Post by michael337 on 2015-12-12
because I just wanted to remove the GNOME desktop environment & only stick to unity, so I went to this forum: [http://askubuntu.com/questions/498635/how-to-remove-gnome-from-ubuntu-desktop-14-04](http://askubuntu.com/questions/498635/how-to-remove-gnome-from-ubuntu-desktop-14-04).then, I realized that it was removing the desktop, so after it got removed, I installed it again, rebooted. It booted normally, until I wanted to see if it was there and it gave the low graphics warning

---

