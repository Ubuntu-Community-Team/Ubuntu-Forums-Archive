---
title: "reconfiguring for a larger monitor"
date: 2007-05-01
forum: Desktop Environments
---

### Post by pentium on 2007-05-01
I revently replaced my far smaller monitor with a larger monitor capavle of displaying 1280x1024.
The problem is that when I installed ubuntu I didn't install support for anything larget than 1024x768 and when I got the nvidia driver installed (I finally got it after replacing the old card) I was given additional useless resolutions like1280x800.
How should I reconfigure x to get the larger resolutions?

---

### Post by taurus on 2007-05-01
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.backup
dpkg-reconfigure -phigh xserver-xorg
```
Then reboot and see what happens.

```
shutdown -r now
```

---

### Post by pentium on 2007-05-01
Nope.
All my resolutions above 600x800 are gone now and my nvidia driver is going screwy.

---

### Post by pentium on 2007-05-02
I dropped -phigh and reconfigured again.
After reinstalling the nvidia driver using envy I was able to get the wanted screen resolution.
Problem solved.

---

