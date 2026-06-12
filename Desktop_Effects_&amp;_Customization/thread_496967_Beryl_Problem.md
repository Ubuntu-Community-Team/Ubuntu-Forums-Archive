---
title: "Beryl Problem"
date: 2007-07-09
forum: Desktop Effects &amp; Customization
---

### Post by moisessalum on 2007-07-09
Hi, I'm having a problem with Beryl.
When I want to start Beryl, it shows the next message:

> moises@moises-desklap:~$ beryl-manager
moises@moises-desklap:~$ Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Sending reload event...
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
**************************************************************
* Beryl system compatibility check                           *
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

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
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


** (beryl-manager:5753): WARNING **: Beryl caught deadly signal 11
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


I don't know what to do, I disabled GL Yield setting, but still nothing. I don't know what else to do, help please.

---

### Post by kidders on 2007-07-10
Hi there,

I know this probably won't be much help, but in case you don't already know, "signal 11" is the dreaded segmentation fault. It suggests fundamental problems, eg binaries compiled for the wrong sub-architecture, faulty hardware, badly-written code, and so on. Depending on how you installed Beryl, and which version you went for, you might want to try something newer, older, or otherwise different ... just to see what happens.

Incidentally, afaik Beryl is no longer being actively developed.

---

