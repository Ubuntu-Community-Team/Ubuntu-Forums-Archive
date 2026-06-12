---
title: "problems w/ beryl 3d and firefox"
date: 2007-04-07
forum: Desktop Environments
---

### Post by keidori on 2007-04-07
Just got beryl last night. I have a few problems. First issue that im having is any window that I maximize losses its controls (close, minimize, maximize) in its place is a white strip. [ATTACH]29188[/ATTACH]The second issue im having is when beryl manager comes up it complains about a 3d error (see the text below) I used the install guide from [http://doc.gwos.org/index.php/BerylOnEdgy#Radeon_Driver](http://doc.gwos.org/index.php/BerylOnEdgy#Radeon_Driver) (btw I use a radeon mobility 7500) Any help would be great, Thanks


libGL warning: 3D driver claims to not support visual 0x4b
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

libGL warning: 3D driver claims to not support visual 0x4b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (1024x1024)

libGL warning: 3D driver claims to not support visual 0x4b
Reloading options

---

### Post by SorenK on 2007-04-08
I don't know about your second problem, but I had the same first problem as you.  The solution in the thread linked below worked for me:

[http://ubuntuforums.org/showthread.php?t=389390](http://ubuntuforums.org/showthread.php?t=389390)

---

