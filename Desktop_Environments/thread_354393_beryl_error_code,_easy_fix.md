---
title: "beryl error code, easy fix"
date: 2007-02-05
forum: Desktop Environments
---

### Post by lessonz101 on 2007-02-05
Does anyone happen to know how to fix this error message?

```
lessonz101@tiny:~$ beryl-manager
lessonz101@tiny:~$ libGL warning: 3D driver claims to not support visual 0x4b
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

libGL warning: 3D driver claims to not support visual 0x4b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libGL warning: 3D driver claims to not support visual 0x4b
Reloading options
beryl: unsupported window depth for thumbnail
beryl: unsupported window depth for thumbnail
beryl: unsupported window depth for thumbnail
beryl: unsupported window depth for thumbnail
```

any help would be appreciated. I should know this, but I'm having a brain fart...
thanks

---

### Post by shareMenaPeace on 2007-02-05
Did you just installed and run for the first time?

Only i can think of is try to load 
```

beryl-manager
```
and under general settings browse down to windows thumbnails and deactivate it.

---

### Post by lessonz101 on 2007-02-05
that's how I got the error, I did the install and put beryl-manager in the startup. when I restarted beryl didn't start up. so I fired it up in the terminal and got that message. any ideas? this one is new to me, maybe an xorg line is out of wack?that I can't find


EDIT

just read the last line under your code after I posted this

---

### Post by shareMenaPeace on 2007-02-05
Please post teh screen and device section of

gksudo gedit /etc/X11/xorg.conf

---

