---
title: "Unity only works in 2D mode"
date: 2011-11-07
forum: Desktop Environments
---

### Post by tenshi3 on 2011-11-07
I've recently upgraded to 11.10 and found that I am unable to use Unity unless in 2D mode.

When loading Unity, it brings up the wallpaper, titlebar and the menu on the left of the screen, but then remains totally unresponsive. I cannot click anything and keyboard commands such as bringing up a terminal do nothing. However, everything seems to run fine in 2D mode.

I am reasonably confident this is not a hardware related issue, but I can provide more specific hardware details. I ran the unity support test which returned the following.

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7300 LE/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Anybody got any bright ideas? Cause I'm out! :confused:

---

### Post by 3Miro on 2011-11-07
Apparently the Nvidia 7300 cards are not fully compatible with Unity 3D. There seems to be an issue with the Nvidia driver, which means it is beyond Canonical's ability to fix.

[http://ubuntuforums.org/showthread.php?t=1741566](http://ubuntuforums.org/showthread.php?t=1741566)

You can try to install CCSM and try to adjust some of the settings in there. Maybe disabling an effect or two would fix the issue.

---

### Post by Tri-Booter on 2011-11-07
I would try making sure your drivers are up to date and if that does not work then just upgrade your card if this is a desktop..

---

### Post by tenshi3 on 2011-11-08
With regards to the previously mentioned post, I read the bug report [https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745) and noticed that other people were having success with driver version 173.

This although appearing sluggish has alleviated the problem. Thank you for your assistance.

---

### Post by typhoon_tip on 2011-11-08
> **tenshi3 said:**
> With regards to the previously mentioned post, I read the bug report [https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745) and noticed that other people were having success with driver version 173.

This although appearing sluggish has alleviated the problem. Thank you for your assistance.

Or you feel "adventurous", you can try the driver from NVIDIA website directly. I did that on a client's laptop Sony VAIO because all the repo drivers were not working, and got it working after doing unbelievable stunts. At once I was typing on a screen cut in half and had to type and pray it was the correct syntax and supposing the command went successfull (used to do that kind of typing while chatting with XMODEM back in 1996, as you could not see what you were typing to the other end ! :popcorn: ).

All in all, I got extremely good performance out of that laptop, but I would suggest only very skilled users to ever attempt installing that driver on Ubuntu.

EDIT: ... and updating the kernel after that driver is installed, it actually break everything down, but just reinstall the driver over the new kernel is fine.

---

