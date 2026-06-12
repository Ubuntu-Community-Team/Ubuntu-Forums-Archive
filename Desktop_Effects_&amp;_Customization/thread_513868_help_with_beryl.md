---
title: "help with beryl"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by cptjaben on 2007-07-31
I installed beryl following [this guide]("https://wiki.ubuntu.com/BerylOnFeisty"). When I try to change the window manager from metacity to beryl I get this outcome: does anyone know how to fix this? Thanks.

```
john@laptop:~$ beryl-manager
john@laptop:~$ **************************************************************
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
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0


```

---

### Post by tgm4883 on 2007-07-31
> **cptjaben said:**
> I installed beryl following [this guide]("https://wiki.ubuntu.com/BerylOnFeisty"). When I try to change the window manager from metacity to beryl I get this outcome: does anyone know how to fix this? Thanks.

```
john@laptop:~$ beryl-manager
john@laptop:~$ **************************************************************
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
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0


```

Not a fix for your problem, but are you aware that beryl is discontinued and has remerged with compiz to form compiz fusion

---

### Post by Waappu on 2007-07-31
> **cptjaben said:**
> I installed beryl following [this guide]("https://wiki.ubuntu.com/BerylOnFeisty"). When I try to change the window manager from metacity to beryl I get this outcome: does anyone know how to fix this? Thanks.

What video card you have ? Could you post your xorg.conf?

---

### Post by cptjaben on 2007-07-31
I was unaware of the merge between beryl and compiz, i'll try a different guide Thanks.

---

