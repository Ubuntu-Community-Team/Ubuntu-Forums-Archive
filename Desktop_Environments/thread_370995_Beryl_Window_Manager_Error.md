---
title: "Beryl Window Manager Error"
date: 2007-02-26
forum: Desktop Environments
---

### Post by Layton on 2007-02-26
I installed Beryl using this site - [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html) - and when i boot it up i get a window manger error.

I try to select beryl manually, but it just kick me back to the default. 

I should mention im running an ATI card (9800pro) and using Ubuntu.

When I run beryl-manager in the terminal i get this:

> adam@adam-ubuntu:~$ beryl-manager
adam@adam-ubuntu:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0




---

### Post by Waappu on 2007-02-26
Hi

Did you logon to XGL session ?

---

### Post by Layton on 2007-02-26
When i log on to xgl and run beryl, i get the white screen of death

---

### Post by Waappu on 2007-02-26
Hi

If you are using fglrx diver you need use XGL.
See if this helps you:
[http://www.ubuntuforums.org/showthread.php?t=363480&highlight=beryl+white](http://www.ubuntuforums.org/showthread.php?t=363480&highlight=beryl+white)

Other solution is that you start using open suorce driver and AiGLX. If you want to do that you need first remove fglrx driver and XGL.

---

