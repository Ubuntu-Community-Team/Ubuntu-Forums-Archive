---
title: "What is broken?"
date: 2007-07-29
forum: Desktop Effects &amp; Customization
---

### Post by ErusGuleilmus on 2007-07-29
I recently went, for reasons that I still cant comprehend, from Gnome to KDE. I did a fresh install of Kubuntu 7.04 and was able to get the correct Nvidia drivers going. The Only problem is that beryl will not work. After getting the proper driver, I did "sudo apt-get install beryl" in the konsole. It installed and when I tried to run it, all of my window borders disappear. The cube effect and all other effects worked. I then typed in "sudo apt-get install emerald" but it said that emerald was already in its most recent version. Here is what the Konsole says when I run Beryl in it:

```
william@william-laptop:~$ beryl --replace
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32

```
This is what it says when I do Emerald:

```
william@william-laptop:~$ sudo apt-get install emerald
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
emerald is already the newest version.
emerald set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 90 not upgraded.
william@william-laptop:~$ emerald --replace
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(emerald:9649): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(emerald:9649): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(emerald:9649): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(emerald:9649): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8
```

Thank you for the help!!

---

### Post by andrewsomething on 2007-07-29
The X-Error seems like it might be un-related, see: [http://ubuntuforums.org/showthread.php?p=1762954](http://ubuntuforums.org/showthread.php?p=1762954)

As for getting Emerald to start, try updating the package: "libdecoration0" and make sure that you are getting emeralad from the same repo as beryl.

If that doesn't work you might need to change your default depth to 24. Edit the "Screen" section in your /etc/X11/xorg.conf file so that the default depth is set to 24 and then restart X.

Hope that helps...

---

### Post by ErusGuleilmus on 2007-07-29
How do I open  /etc/X11/xorg.conf as root so that I can save it?

---

### Post by andrewsomething on 2007-07-29
> **ErusGuleilmus said:**
> How do I open  /etc/X11/xorg.conf as root so that I can save it?

Well I'd do "sudo gedit /etc/X11/xorg.conf" but I'm not using KDE. So you probably need to change gedit to a KDE txt editor... I guess that would be "kate"

---

