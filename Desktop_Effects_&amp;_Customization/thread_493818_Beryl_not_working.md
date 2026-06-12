---
title: "Beryl not working"
date: 2007-07-06
forum: Desktop Effects &amp; Customization
---

### Post by SoftVision on 2007-07-06
I have an Intel 915G onboard video card. Beryl is giving me this error:

```
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
**Checking for non power of two texture support   : failed**

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

What text do I need to add to the xorg.conf file to fix this or is there another way? I have read that my card is compatible with Beryl.

---

### Post by Gremlinzzz on 2007-07-06
How did you install Beryl.I use the synaptic package manager and it works fine.See if you can uninstall and reinstall using synaptic.

---

### Post by SoftVision on 2007-07-06
I've reinstalled it twice now, but I'm getting the same error. Can anybody please help?

---

