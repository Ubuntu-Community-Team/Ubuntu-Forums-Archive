---
title: "Beryl Not Starting All Of A Sudden"
date: 2007-09-16
forum: Desktop Environments
---

### Post by Uber Nooblett on 2007-09-16
but now I've got this and Beryl wont start :(

Thinking that i might have knocked some dependencys or something when I was tinkering earlier. Its not the xorg.conf thats off as I've used the backup from when it was working fine, must be something else... have purged and re-installed beryl, its not running twice or anything...

Any Ideas?

```
jj@JJ-Beast:~$ beryl
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
Checking maximum texture size                   : passed (8192x8192)

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
Checking maximum texture size                   : passed (8192x8192)

beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :0.0

``` 

Thanks in advance for your help. Reeeeally don't want to re-install everything from the OS up again :'(

---

### Post by Uber Nooblett on 2007-09-16
Never Mind, Fixed it :D removed KoolDock from Autostart and need to exit it before shutdown or it interferes lol

---

