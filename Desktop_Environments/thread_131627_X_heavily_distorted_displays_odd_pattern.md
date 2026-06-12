---
title: "X heavily distorted/ displays odd pattern"
date: 2006-02-16
forum: Desktop Environments
---

### Post by johnnabn on 2006-02-16
I have just installed Ubuntu 5.10 and am expierencing the same problem that I had with Kubuntu Dapper.  When X loads up, the screen either becomes a distorted pink/red color or a screen of rectangles in a somewhat checkerboard like pattern.  The X server does NOT crash at any point, and the logs show no error.   It is, however, completely unusable. It appears that things are changing as I hit keys and/or attempt to login, but I cannot distinguish what is actually changing.

These problems occur both when X is invoked by the init scripts and when I run it myself.  I have verified that all of the settings related to the monitor and video card in xorg.conf match those in my working Gentoo setup.  In fact, I tried copying over the Gentoo xorg.conf, and after disabling some modules that didn't exist in Ubuntu, got it to load with the same effect.

I have an NVidia Geforce 6600 and a pretty generic LCD monitor.  I am attempting to use the NV driver, not NVIDIA.

Does anyone have any suggestions or help?

EDIT: I got X to load up fine with the vesa driver, I had almost forgotten about that.  I have no need for 3d at this time, and vesa looks fine, so I guess my problem is solved, for the time being at least.  Still have no idea why NV doesn't work, I'm pretty sure it should, but oh well.

Thanks again.
Thanks,

---

### Post by kuratkull on 2006-03-15
exactly the same problem...help?

---

### Post by CyberCam on 2006-03-20
I too have this problem, with the exact same vid card?

---

### Post by dickohead on 2006-03-21
Change your /etc/X11/xorg.conf file to use the "vesa" driver where it currently says "nv" or "nvidia" if it already says "vesa" then try "nv".

Ctrl + Alt + F2 will bring you into terminal mode, and Ctrl + Alt + F7 will bring you back to the login screen, pressing Ctrl + Alt + Backspace will restart the X-Server, restart it once you have made changes to xorg.conf and saved them.

---

