---
title: "Why does beryl not work?"
date: 2007-03-27
forum: Desktop Environments
---

### Post by Zahlerstreik on 2007-03-27
I have installed Edgy 6.10, fully updated, installed beryl with the autoinstall script...and beryl still will not work!!!
is it possible that my using x64 is the problem?
everything looks like it is configured properly...but beryl wont start. when i type beryl in console this is what i get :```
**************************************************************
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

i am on a notebook with an ati x700. any ideas?

---

### Post by adam.tropics on 2007-03-27
Try 'beryl-xgl' instead of 'beryl'.

---

### Post by Zahlerstreik on 2007-03-27
got it working. after some xorg conf tinkering and driver reompiles i also had to restart the machine under a different kernel.


<3

---

