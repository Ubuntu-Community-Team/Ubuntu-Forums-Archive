---
title: "Newbie seeking help with gfx driver installation"
date: 2005-07-11
forum: Desktop Environments
---

### Post by | MM | on 2005-07-11
Hello,

I have just installed the 64bit version of ubuntu.

At the moment my desktop resolution is at 1024 * 768.  but the refresh rate is on at 60Hz, and its literally giving me a damn headache.  So my first issue will be to ramp the refresh rate up at least 75Hz.  I hope this is possible, perhaps without new drivers?

I have an Nvidia 6600GT 128MB, and from my reading their is an extra element of difficulty associated with these cards?
[i]nVidia 
GeForce 6610XL / 128 MB 

Seems to be an downgraded 6600, BinaryDriverHowto does NOT work. One must install the driver from Nvidia (see FinishInstallationHowto )[/i]
[https://wiki.ubuntu.com//HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com//HardwareSupportComponentsVideoCards)

I want to install the latest AMD64 linux drivers.  I have the .run package.
'NVIDIA-Linux-x86_64-1.0-7667-pkg1.run'

I have never used Linux before in my life.  The result being the tutorials that i have seen posted dont seem comprehensive enough to guide me through them.


With respect to the nvidia README:

[i]
Prior to beginning the installation, you should exit the X server and kill all
OpenGL applications (note that it is possible that some OpenGL applications
persist even after the X server has stopped). You should also set the default
run level on your system such that it will boot to a VGA console, and not
directly to X. Doing so will make it easier to recover if there is a problem
during the installation process. Please see Chapter 8 for details.[/i]

I have no idea how to carry out any of this ...  and as such i am reluctant to start the installer.

So first things first.

How do I:

[b]exit the X server and kill all OpenGL applications.
set the default run level on your system such that it will boot to a VGA console, and not directly to X OpenGL applications[/b]

Ill probably have heaps of other questions as the (my)night progresses, so any help would be much appreciated.

---

### Post by brim4brim on 2005-07-11
[QUOTE=| MM |]Hello,

I have just installed the 64bit version of ubuntu.

At the moment my desktop resolution is at 1024 * 768.  but the refresh rate is on at 60Hz, and its literally giving me a damn headache.  So my first issue will be to ramp the refresh rate up at least 75Hz.  I hope this is possible, perhaps without new drivers?

I have an Nvidia 6600GT 128MB, and from my reading their is an extra element of difficulty associated with these cards?
[i]nVidia 
GeForce 6610XL / 128 MB 

Seems to be an downgraded 6600, BinaryDriverHowto does NOT work. One must install the driver from Nvidia (see FinishInstallationHowto )[/i]
[https://wiki.ubuntu.com//HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com//HardwareSupportComponentsVideoCards)

I want to install the latest AMD64 linux drivers.  I have the .run package.
'NVIDIA-Linux-x86_64-1.0-7667-pkg1.run'

I have never used Linux before in my life.  The result being the tutorials that i have seen posted dont seem comprehensive enough to guide me through them.


With respect to the nvidia README:

[i]
Prior to beginning the installation, you should exit the X server and kill all
OpenGL applications (note that it is possible that some OpenGL applications
persist even after the X server has stopped). You should also set the default
run level on your system such that it will boot to a VGA console, and not
directly to X. Doing so will make it easier to recover if there is a problem
during the installation process. Please see Chapter 8 for details.[/i]

I have no idea how to carry out any of this ...  and as such i am reluctant to start the installer.

So first things first.

How do I:

[b]exit the X server and kill all OpenGL applications.
set the default run level on your system such that it will boot to a VGA console, and not directly to X OpenGL applications[/b]

Ill probably have heaps of other questions as the (my)night progresses, so any help would be much appreciated.[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=31094&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=31094&page=1&pp=10)

This thread has a lot of How To's that were in the forums of common problems, check there if you havn't and bookmark it for future reference.  It's a really useful starting spot if your having problems and need a step by step guide to fix them.

---

### Post by | MM | on 2005-07-11
Thanks soo much

---

