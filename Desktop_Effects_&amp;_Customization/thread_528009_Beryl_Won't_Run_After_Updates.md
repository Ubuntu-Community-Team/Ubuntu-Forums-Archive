---
title: "Beryl Won't Run After Updates"
date: 2007-08-17
forum: Desktop Effects &amp; Customization
---

### Post by hutch346 on 2007-08-17
I just installed some updates (which were all for beryl) and after my next reboot Beryl won't start- it just reverts back to Metacity. This is is the output from the terminal after I use the "beryl --replace" command:

john@john-laptop:~$ beryl --replace
**************************************************************
* Beryl system compatibility check                           *
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
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Initiating splash
beryl: symbol lookup error: /usr/lib/beryl/libbench.so: undefined symbol: benchGetOutput_console

---

### Post by H_out on 2007-08-23
I remember having a problem with Beryl after updating as well, but I got around it by forcing:

libdecoration0

to stay at version 1:0.3.6 (the latest is 1:0.5.1)

Hope that helps.

---

