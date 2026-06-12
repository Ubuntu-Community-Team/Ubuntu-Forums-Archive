---
title: "Beryl &amp; Feisty &amp; ATI (beryl detect only aiglx), how forced beryl to use xgl?"
date: 2007-04-20
forum: Desktop Environments
---

### Post by peter07 on 2007-04-20
EDIT No I have this problems:

Beryl:
```
 beryl **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
```

Beryl USE COPY:
```
beryl --use-copy**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
```

What is this  GLX_SGIX_fbconfig is missing??

---

### Post by sc30317 on 2007-04-28
bump

---

### Post by Icx on 2007-08-16
I have one problem: I installed xorg propertiarty driver on my Kubuntu 7.04 FF X64. Beryl worked as I installed system and Beryl with Emerald without driver. But when I installed this driver it crashed so I uninstalled driver. Now Beryl icon is floating but it won't load. Then I went to Konsole and typed manually Beryl Manager. It appeared but it's all in white. There is no beryl logo but when I rotate I see it's a cube. When I loaded glxinfo there stands both SGI output rendering; that means driver is uninstalled. Help please.

---

### Post by neuralnet on 2007-08-21
Yep, exactly same problem here. GFx Card is a Radeon X1650 on Ubuntu Feisty, have tried various combinations of drivers.. Managed to get XGL to run instead of AIGLX, only to have this error message. Anyone got this fixed ?

---

