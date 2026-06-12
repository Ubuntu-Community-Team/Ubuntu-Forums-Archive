---
title: "Beryl Issues..."
date: 2007-04-13
forum: Desktop Effects &amp; Customization
---

### Post by ArmoredCavalry on 2007-04-13
I finally got beryl working with my ATI x1400. The only thing is, there seems to be many features that don't work. All the windows effects are fine, but when I change workspaces using the cube, it stays doesn't really change workspaces, it just stays in the first one. In addition, the skydome doesn't work. The only clue I have is this message when I type "beryl" in terminal:

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


Anyone?

---

### Post by bdogg64 on 2007-04-13
You need to use beryl-xgl and its not in the feisty repos. You should downgrade to beryl 0.2.0 which has beryl-xgl and works

---

### Post by ArmoredCavalry on 2007-04-13
I'm using dapper, and have 0.2.0~0beryl1 installed...

P.S. Anyone know how to change the icon theme with beryl?

---

