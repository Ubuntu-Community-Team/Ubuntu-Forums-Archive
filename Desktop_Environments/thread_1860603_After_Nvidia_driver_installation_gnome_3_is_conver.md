---
title: "After Nvidia driver installation gnome 3 is converted to half gnome 2 nd half gnome 3"
date: 2011-10-14
forum: Desktop Environments
---

### Post by bhupinderjitbawa on 2011-10-14
Hi i newly installed ubuntu 11.10.
After Nvidia installation when i restarted my gnome 3 activity was gone.. it retained some properties..
i have removed nvidia now..
then tried reinstallation of "gnome-shell"
but no results
while loggin in it shows following options

gnome
gnome classic
gnome classic(no effects)
Ubuntu
Ubuntu 2d

gnome and gnome classic loginto same thing.. gnome 3 is not working..
any solution???
I am attaching the snapshot

---

### Post by mcduck on 2011-10-15
That's the Gnome Shell's fallback mode, used when you don't have graphics card (or drivers) capable of running hardware-accelerated desktop.

Seems like your driver installation failed, and simply removing the driver doesn't get you back to using the open-source drivers, so at the moment you have no working graphics acceleration. For best results you probably should retry installing the nVidia drivers...

---

### Post by thezood on 2011-10-15
I had the same problem, but with ATI. Install fglrx to see if it would solve my HDMI output problems (it didn't but instead caused screen corruption and made Ubuntu unusable). After uninstall of fglrx, I got unaccelerated Gnome only. I had the radeon driver active but I think Gallium is better for my graphics card. I just upgraded to xorg-edgers ([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)). I realize this isn't the proper way to solve this since edgers isn't necessarily but I'd rather just have a working desktop right now.

---

