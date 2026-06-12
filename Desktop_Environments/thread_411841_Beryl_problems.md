---
title: "Beryl problems"
date: 2007-04-17
forum: Desktop Environments
---

### Post by allforcarrie on 2007-04-17
I have been following this [http://ubuntuforums.org/showthread.php?t=388819&highlight=No+composite+extension](http://ubuntuforums.org/showthread.php?t=388819&highlight=No+composite+extension)
and i still cant get beryl to work. here is the error i get now:
> **************************************************************
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
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


---

### Post by garlik42 on 2007-04-17
Do you have

Load "dri" 

In your Module section ??

---

### Post by allforcarrie on 2007-04-17
i would assume not since i don't know what that is.

---

### Post by garlik42 on 2007-04-24
OK, in your /etc/X11/xorg.conf file, there is a section called modules.
This is an EXAMPLE of that section

```
Section "Module"
    Load        "freetype"
    Load       "glx"
    Load       "dri"
    Load        "vnc"
EndSection
```

If you find the module section in your xorg.conf file, make sure there is a Load "dri" statement.
If it's already there, then I am not sure what is wrong.

---

