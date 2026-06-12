---
title: "Beryl not working after dist-upgrade to feisty"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by _hawk_ on 2007-05-14
Hi!

I've just upgraded my kernel from edgy to feisty and all of a sudden beryl stopped working. I've reinstalled my graphicscard driver and beryl without success. (ATI mobility). Beryl worked quite well before the upgrade. I could use Compix

Thus, fglrxinfo gives me:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300
OpenGL version string: 2.0.6334 (8.34.8)

Whenever I try to run beryl, I get the following error: 

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

Any help would be appriciated.

---

### Post by Death_Sargent on 2007-05-14
you need to reinstall

[Beryl install Wiki]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_7.04_.28Feisty_Fawn.29")

---

### Post by _hawk_ on 2007-05-14
Yup, I found that as well... Tried to access the beryl wiki earlier but it seemed to be down. Managed to get it to work though, it seemed to be the downgrading that was the solution. Thanks anyhow

-Hawk

---

