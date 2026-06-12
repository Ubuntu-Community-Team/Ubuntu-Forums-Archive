---
title: "Uninstalling Beryl"
date: 2007-05-11
forum: Desktop Effects &amp; Customization
---

### Post by SBinVA on 2007-05-11
How do I uninstall Beryl? After I first installed it everything worked fine, but I've done something to make it stop working properly. (When using the beryl window manager and emerald window decorator I lose the title bar on all windows. I've tried everything I can find to try to fix it to no avail.)

My thought is, and please tell me if I'm wrong, that if I just remove beryl and then install it again that maybe, just maybe, it will work again.

I've got Fiesty installed on an AMD 64 x2 6000 machine, 2GB PC6400, NVIDIA 7300GT.

If I use the terminal to start beryl, it hangs at "Reloading Options"

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

Reloading options

```

---

### Post by Ateo on 2007-05-11
Remove all traces of Beryl first. 

Then run```
$ gconftool-2 --recursive-unset /apps/beryl
```

Then reinstall Beryl.

This should give you a nice clean slate to start with.

---

