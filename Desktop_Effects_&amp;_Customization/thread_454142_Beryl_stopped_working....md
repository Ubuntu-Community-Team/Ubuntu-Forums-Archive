---
title: "Beryl stopped working..."
date: 2007-05-25
forum: Desktop Effects &amp; Customization
---

### Post by jperez on 2007-05-25
It was working well, until I put in a CD while I was getting the update info for the night.  Here's what I got after typing beryl into the terminal:

```
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

Segmentation fault (core dumped)

```

Anyone got any ideas?

Jesse~

---

### Post by jperez on 2007-05-25
Anyone?  I'd really like to et my Beryl working again.  =/

Jesse~

---

### Post by jperez on 2007-05-25
Nevermind, it started working again...somehow.

I uninstalled it, reinstalled it and messed with the settings a bit and somehow it worked. =/

Beryl is weird...

Jesse~

---

### Post by gp2x on 2007-06-05
This has happened to me now, what exactly did you do???????

---

### Post by gp2x on 2007-06-06
update:

[http://ubuntuforums.org/showthread.php?p=2791601#post2791601](http://ubuntuforums.org/showthread.php?p=2791601#post2791601)

---

### Post by peedeeramone on 2007-06-13
ohh i have a somewhat similar problem...

i had beryl running for a long time now, and just recently it crapped out for some reason...

i kinda know what my problem is but i dont remember how to fix it....

here's my terminal output when i run beryl:


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

Xlib:  extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
Xlib:  extension "GLX" missing on display ":0.0".
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
^^^^-for some reason i think my display is wrong

does someone know how to change it..?

i dont think it would be too difficult to fix but i just cant remember what file im supposed to edit...

---

