---
title: "Beryl Window Manager Fail"
date: 2007-02-11
forum: Desktop Environments
---

### Post by Johny2x4 on 2007-02-11
I completely installed beryl and all the updates.  I'm using Ubuntu 6.10 and when i try to change to beryl as the window manager it tries to start it, but it seems as if it crashes and falls back on the gnome window manager.  Any suggestions would be great. Thanks in advance.

---

### Post by Johny2x4 on 2007-02-11
After enabling composite i got further but when starting beryl in terminal i get this as a result
```
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

```

---

### Post by geek_Man on 2007-02-11
I'm having almost the exact problem, only when *I* run Beryl it says:

```
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

libGL warning: 3D driver claims to not support visual 0x46
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
libGL warning: 3D driver claims to not support visual 0x46
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

I've noticed that I've gotten the error "libGL warning: 3D driver claims to not support visual 0x46" a lot. Would anyone know what "visual 0x46" is? Help is much appreciated.

P.S. Sorry to hijack. 8-[

---

### Post by shareMenaPeace on 2007-02-11
> **Johny2x4 said:**
> After enabling composite i got further but when starting beryl in terminal i get this as a result
```
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

```
Can you post your xorg.conf?

from 
/etc/X11/xorg.conf

---

### Post by usergentoo on 2007-02-11
I got this problem also I picked up a kernel update this morning and thats when it started.

---

### Post by shareMenaPeace on 2007-02-11
> **usergentoo said:**
> I got this problem also I picked up a kernel update this morning and thats when it started.
Can you check your /var/log/Xorg.0.log for any error messages please.
gedit the file or use
System-> Administration -> System Logs

---

### Post by usergentoo on 2007-02-11
I forgot when you have a updated kernel you have to reinstall the ati/nvidia drivers which will fix the problem.

---

