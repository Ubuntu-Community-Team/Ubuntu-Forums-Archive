---
title: "Change default tty after boot on 16.04"
date: 2016-05-19
forum: Desktop Environments
---

### Post by alex_f4 on 2016-05-19
Hello, 
I have installed 16.04 64 bit desktop edition successfully on several machines.  I installed lxde, lxdm and lxsession and am able to use the lxde desktop environment.
My issue is this:
After installing lxde, when I boot any of the machines, it opens on tty1.  I can easily use Ctrl + Alt + F7 to get to the desktop environment, but I would like to change the default tty to 7 so this is not necessary.
I have tried editing /etc/grub.d/10_linux and changing the vt_handoff value to "7" but this had no effect.
Thank you for any advice you can offer.

---

### Post by izznogooood on 2016-05-20
[FONT=monospace]Its a shot in the dark but try:

[/FONT]```
sudo dpkg-reconfigure gdm

```

---

