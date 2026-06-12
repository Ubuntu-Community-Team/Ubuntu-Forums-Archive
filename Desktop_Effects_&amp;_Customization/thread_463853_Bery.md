---
title: "Bery"
date: 2007-06-04
forum: Desktop Effects &amp; Customization
---

### Post by Samjiman on 2007-06-04
Hi, everyone.

I've been having problems running Beryl.
I have installed the proprietary ATI drivers.

I get this output, some weird error to do with non powers of two. How can I resolve it?

> 
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


Also I can't enable destop effects, when I try to I get an error "Desktop effects can not be enabled".
Why is this - I've checked my card using grep and direct rendering is apparently supported by it?

Thank you very much for any pointers :)

---

