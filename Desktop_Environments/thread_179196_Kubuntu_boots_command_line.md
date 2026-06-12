---
title: "Kubuntu boots command line"
date: 2006-05-19
forum: Desktop Environments
---

### Post by Wr8EYilK8Y on 2006-05-19
Why, yesterday, after using automatix, did my computer start booting a command line instead of a GUI? I used automatix to install nVidia drivers. Then OpenGL stopped working. I tried reinstalling that, and now it won't boot a GUI.

---

### Post by vidak on 2006-05-19
is it possible that your xorg.conf got messed up? I mean eg. it tries to load the wrong driver... The easiest way to change this is
sudo configure-debian
if you have installed this utility of course. Select x11/<your x server> and select your card's driver or as a last chance the vesa driver...

---

### Post by vidak on 2006-05-19
btw. you could check these pages too:
OpenGL problems:
[https://wiki.ubuntu.com/NvidiaTroubleshooting?highlight=%28nvidia%29](https://wiki.ubuntu.com/NvidiaTroubleshooting?highlight=%28nvidia%29)
BinaryDriver:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
And a "not recommended way to install the Nvidia drivers":
[https://wiki.ubuntu.com/NvidiaManual?highlight=%28nvidia%29](https://wiki.ubuntu.com/NvidiaManual?highlight=%28nvidia%29)

---

### Post by Wr8EYilK8Y on 2006-05-19
I got help in another thread, but now GLX isn't working. I use official 87.56 nVidia drivers and have a GeForce 6200.
```

williamd@williamskubuntu:~$ sudo nvidia-glx-config enable
Password:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
williamd@williamskubuntu:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x57 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
williamd@williamskubuntu:~$                                

```

---

### Post by romUdog on 2006-05-19
hey dude go startx after you login and it should start the GUI

---

### Post by [S|G] on 2006-05-20
I've had that very same problem more than once. You should try this (from the command line you have):
```

sudo apt-get install nvidia-glx nvidia-kernel-common nvidia-kernel-source linux-restricted-modules-common linux-restricted-modules-YourKernelVersion

```

Note that where I wrote YourKernelVersion you'll replace with something such as "2.6.15-23-386". You check your kernel version using "uname -r". After installing, just reboot and you should have your video working

---

### Post by Wr8EYilK8Y on 2006-05-20
I just did this to get OpenGL working (installing official nVidia drivers by hand fixed what automatix broke):
```

md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
sudo nvidia-glx-config enable

```
startx doesn't work, romUdog. The problem is a lack of drivers for the display card (in this case my GeForce 6200)

---

### Post by [S|G] on 2006-05-20
[QUOTE=Your Name Is]The problem is a lack of drivers for the display card (in this case my GeForce 6200)[/QUOTE]

You couldn't get them working using the apt-get line I posted above?

---

### Post by Wr8EYilK8Y on 2006-05-22
No, so I tried the official drivers. They worked.

---

