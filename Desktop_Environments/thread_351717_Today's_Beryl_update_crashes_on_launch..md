---
title: "Today's Beryl update crashes on launch."
date: 2007-02-02
forum: Desktop Environments
---

### Post by danhm on 2007-02-02
You guys might want to wait a little before installing the newest version (0.1.9999.1); whenever I try to launch mine it crashes immediately.

Here is what happens when I try to run it from the console:
```

dan@dan-laptop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing

```

I have a Radeon X1400 in a Dell e1505 laptop, using the flgrx driver. Is it just me with this problem, or are other people getting it?

---

### Post by wh0rd on 2007-02-02
Quite a lot of people are having this issue, including myself.

---

### Post by dasunst3r on 2007-02-02
Confirmed on Dell Inspiron 6000 with Radeon Mobility x300.

---

### Post by waldorf on 2007-02-02
A complete removal and then re-install seemed to solve the problem for me.

---

