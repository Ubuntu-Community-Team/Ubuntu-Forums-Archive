---
title: "Beryl broken after working for a month"
date: 2007-02-25
forum: Desktop Environments
---

### Post by medley on 2007-02-25
Hi all

Well, I managed to break beryl once again. I had been enjoying it for more than a month when I thought I would upgrade some other components of my edgy system. I upgraded several items, but didn't touch any beryl upgrades (this from painful experience). 

When I select beryl as the window manager, the windows no longer have decorations and controls on them. Also it appears that many plugins are not loading. If I watch konsole while I select beryl as the window manager I receive the following errors.


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

libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libanimation.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/lib3d.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libcrashhandler.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libannotate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libbench.so' plugin

etc...

There are actually 47 source files that libberylsettings can't get the 'vtable' from (whatever that means). I truncated the list to keep it manageable. The things is that all of these source files are present in /usr/lib/beryl/. 

Any ideas?

---

### Post by shareMenaPeace on 2007-02-25
> **medley said:**
> 
Any ideas?
Reinstall? (See my signature link).

---

