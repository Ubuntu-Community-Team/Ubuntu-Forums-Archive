---
title: "Nvidia Display driver problem"
date: 2009-05-17
forum: General Help
---

### Post by k4kelly on 2009-05-17
I have a amd system with m3n72-d MB, with 2 nvidia Geforce 7800 video cards.  I installed the Nvidia accelerated graphics driver (version 180). When I rebooted it come up on the command terminal. I reloaded
mythubuntu 2 times. I'm new to linux and don't know how to fix this from the command line. Can you help?

---

### Post by 67GTA on 2009-05-17
Do you have a Hauppauge TV tuner card?

---

### Post by Enlitend on 2009-05-17
Ok, when you boot up in the command line, log in with your username and password.
After login in, type this:

```
gksudo gedit /etc/X11/xorg.conf
```

It will ask you for a password, type in your password (the password will not show, just keep typing).
Scroll down in the "xorg.conf", find the **Section "Device"** line and add this line under it:

```
BusID  "PCI:1:0:0"
```

For example, it will look something similar like this:

```
Section "Device"
  Idenfitifier	"Device0"
  Driver	"nvidia"
  VendorName	"NVIDIA Corporation"
  BoardName	"GeForce 7800 GT"
  *BusID		"PCI:1:0:0"*
EndSection
```

Save it and reboot:

```
sudo reboot
```

---

### Post by k4kelly on 2009-05-17
Yes I have a hauppauge WinTV-HVR-1800 and i can't locate the drivers for it.

---

### Post by 67GTA on 2009-05-17
It should use the cx18 module which is already in the kernel. The problem is a conflict between cx18 and nvidia. Look here for solution to use both at the same time.

[http://ubuntuforums.org/showthread.php?t=1004660](http://ubuntuforums.org/showthread.php?t=1004660)

---

