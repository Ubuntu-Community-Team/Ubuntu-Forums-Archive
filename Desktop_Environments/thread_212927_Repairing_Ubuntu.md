---
title: "Repairing Ubuntu"
date: 2006-07-10
forum: Desktop Environments
---

### Post by srstakey on 2006-07-10
First and foremost, I must say that I am a longtime Windows user, but I am more than happy with Ubuntu.

In trying to get 3ddesktop to work today, however, I encountered a problem.  I tried to get the latest nVidia drivers to work, and now it seems that I can't get X started.  As a result, I am stuck at the command line.  How can I either reinstall Ubuntu without losing any performance (I know that would happen in Windows!) or just repair X?  If you guys need a log file, I'll see what I can do, but it seems that the driver doesn't realize that I actually do have an nVidia GPU.  Thanks in advance for the help!

---

### Post by Amduscias on 2006-07-10
Well.. let's first try to repair your X Server before reinstalling, won't we?

First of all, did the Nvidia Installer finish without an error, or was there any error like, "unable to compile nvidia.mo"?
If there was no error, did you change your xorg.conf file, you have to enable the new driver in there. The file is located in /etc/X11/xorg.conf

In the section "Device" is the point Driver which should be "nvidia" when your Nvidia Driver compiled right. If the Driver did not install, set this point to "nv" which is the standard nvidia driver without 3d acceleration to get back X.

---

### Post by Jasper Houtman on 2006-07-10
at the comnandline type:

```
sudo dpkg-reconfigure xserver-xorg
```

Then set up your video card etc. (pick vesa if you want to be on the safe side).

Then type:

```
sudo /etc/init.d/gdm restart
```

Then (re)start ubuntu

---

### Post by srstakey on 2006-07-10
Thank you both.  I was able to get everything working, although I did have to specify my display resolution (1280x800) in the xorg.conf file.

---

