---
title: "Problem after updating Beryl to the latest version"
date: 2007-06-14
forum: Desktop Effects &amp; Customization
---

### Post by shazm on 2007-06-14
As I made an update via Ubuntu update manager, and restarted my system.
My Beryl does no longer work with Beryl effetcs, and also all my desktop icons 
are away. How can I fix it?

> * Beryl system compatibility check                           *
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
Checking maximum texture size                   : passed (2046x2046)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
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
Checking maximum texture size                   : passed (2046x2046)

bberyl: Failed to load slide: /home/onur/Desktop/Walls/Caps/Simple
beryl: Failed to load slide: /home/onur/Desktop/Walls/Caps/Simple
Segmentation fault (core dumped)


---

### Post by mahiyar on 2007-06-15
I have the same problem as shazm's after update and that too after restart.
```
mahiyar@mahiyar-desktop:~$ beryl
**************************************************************
* Beryl system compatibility check                           *
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

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
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

whatever I do it ends at segmentation fault error (viz removing cap images, removing splash etc)

---

### Post by mahiyar on 2007-06-15
OK success. Just delete or rename your .beryl directory in home and restart beryl, of course you will have to discard your settings (I did not want to risk carrying forward old settings). The only problem is that on each change in settings it comes out of beryl in to metacity. Now its a nice Beryl SVN splash :).

---

### Post by shazm on 2007-06-16
sounds nice.
thank you.

---

### Post by Alex&amp;Linux on 2007-06-18
Heyo

Had the same problem after installing conky system monitor, even after uninstalling beryl, beryl-manager, beryl-settings, emerald-themes....the .beryl config files remain...great tip..removing solves!

---

