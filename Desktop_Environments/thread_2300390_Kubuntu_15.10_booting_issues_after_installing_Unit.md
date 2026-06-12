---
title: "Kubuntu 15.10 booting issues after installing Unity"
date: 2015-10-25
forum: Desktop Environments
---

### Post by Vladglot on 2015-10-25
Have been using Ubuntu for quite some time on my Dell Inspiron touchscreen desktop. Dual booted with Windows 8.1. I replaced the Ubuntu partition with Kubuntu 15.10 this week and that was working fine. I then installed the Unity DE and since doing so, I boot Kubuntu from the GRUB boot menu, and then have a black screen for approximately 15 minutes. After that my Unity/KDE Plasma choice appears, I can log in, and everything functions great. Can anyone help shed some light?

---

### Post by deadflowr on 2015-10-25
That's usually the plymouth-splash screens time to shine.
Maybe try resetting it with
```
sudo update-alternatives --config default.plymouth
```
then select which number is the normal kubuntu-splash, press enter,
and reboot.

If that's what you meant?

---

### Post by Vladglot on 2015-10-25
Thanks deadflowr! I tried your advice, and the same issue continued upon reboot. I decided to pick my battles and start from scratch with Ubuntu 15.10 as it boots and runs just fine.

---

