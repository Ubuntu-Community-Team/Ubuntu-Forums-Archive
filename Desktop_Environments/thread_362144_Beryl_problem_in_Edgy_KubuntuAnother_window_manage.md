---
title: "Beryl problem in Edgy Kubuntu:Another window manager is already running"
date: 2007-02-15
forum: Desktop Environments
---

### Post by dancer_69 on 2007-02-15
When beryl starts, crashes with the error: Another window manager is already running on screen 0.
This is the full output: 

--------------------------------------------------------------------------------------------------------------------------
Beryl system compatiblity check                            *
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

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
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

beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :0.0
---------------------------------------------------------------------------------------------------------------------

I unchecked the "Use Translucency/shadows" box in the widows decoration from Kcontrol and I used the option (Option       "Composite" "0") in xorg, and it works until a system reboot. After that I have the same problem and nothing works any more.

Anyone can help me to solve this? 

Thanks in advance!

---

### Post by shareMenaPeace on 2007-02-15
Looks like you try to load it twice.
Check System -> Preferences .> Sessions, maybe its twice in startup programs?

---

### Post by dancer_69 on 2007-02-15
> **shareMenaPeace said:**
> Looks like you try to load it twice.
Check System -> Preferences .> Sessions, maybe its twice in startup programs?

I have kubuntu installed and I cannot find the sessions applet. 
I removed the beryl link from kde autostart, reboot and execute it manual and I have same problem.

---

### Post by dancer_69 on 2007-02-16
Finally uninstal and reinstall everything after I change my beryl repositories with these:
deb [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) edgy beryl-svn
And all works now!

---

