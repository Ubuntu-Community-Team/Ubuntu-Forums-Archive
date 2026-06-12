---
title: "NVIDIA Driver stopped working. No 3D acceleration."
date: 2010-08-23
forum: Desktop Environments
---

### Post by phamnewan on 2010-08-23
My problem started with the following post.

[http://ubuntuforums.org/showthread.php?t=1551476](http://ubuntuforums.org/showthread.php?t=1551476)


I ended up tracing the issue back to openGL that disappeared during an update and the nvidia driver had broken.  The only remaining issue is that the 3D acceleration on the NVIDIA (GeForce 8600 GT) card will not activate.

It appears to be the following issue:
[http://georgia.ubuntuforums.org/showthread.php?t=1538268](http://georgia.ubuntuforums.org/showthread.php?t=1538268)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Which I have done many times now.  I am now on the nvidia-173 driver as that one seems to be working the best.  Even the nvidia-settings is having trouble and crashes when I try to look at the OPENGL/GLX information.

I have found many instances of jockey showing that the driver is "active but not in use" which is what I am seeing.  The problem is that the 3D acceleration is not working and the issue seems to be the driver.

---

### Post by phamnewan on 2010-08-25
Bump...  Any ideas?

---

### Post by phamnewan on 2010-08-25
Here is the driver section of xorg.conf

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

---

### Post by dabl on 2010-08-25
The driver needs to be re-installed.

---

### Post by phamnewan on 2010-08-27
Is it possible that the actual 3D portion of the card failed?

I have purged all versions of nvidia drivers multiple times as well as nouveau.  Have re-installed the 173, 185, current with no change.  I have run the nvidia-xconfig after each with reboot and the result is always the same.

All attempts to activate 3D acceleration fail with the driver active.  I am almost convinced that it isn't a driver issue, but it seems so odd that all the problems started with an update.

I have even compiled wine from source which solved many other problems, but this 3D acceleration one will not resolve although any non-3D wine apps run great.

---

### Post by Keith Fox on 2010-09-06
same problem with me. I'm on Ubuntu Lucid.

---

### Post by Termaim on 2010-09-06
I would try using the most current stable nvidia drivers instead of the ones in the repos.  This guide will help you with doing that, and if you don't have the issue it's stating @ the top of the guide, just start from step 3.

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

---

