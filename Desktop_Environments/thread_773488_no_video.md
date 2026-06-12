---
title: "no video"
date: 2008-04-28
forum: Desktop Environments
---

### Post by flomt on 2008-04-28
Installed the current version of ubuntu, rebotted and all I get is a flashing bunch of colors.  Don't have a chance to enter anything.

---

### Post by Xiong Chiamiov on 2008-04-28
That sounds like a problem with your video card and/or X.  Try the video support forum.

---

### Post by overdrank on 2008-04-29
> **flomt said:**
> Installed the current version of ubuntu, rebotted and all I get is a flashing bunch of colors.  Don't have a chance to enter anything.

HI and welcome, you can try and boot into recovery mode which is usually the second choice in the grub. Then reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` hopefully this will get you to a GUI, Desktop. Good luck.

---

