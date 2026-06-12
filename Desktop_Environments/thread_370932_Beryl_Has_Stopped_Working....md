---
title: "Beryl Has Stopped Working..."
date: 2007-02-26
forum: Desktop Environments
---

### Post by smartbei on 2007-02-26
I have had beryl installed for several months but in the past two weeks haven't used it at all. Then, when I tried to use it today, it does not manage to implement the window manager and when run in a console gives me:
> 
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
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libblurfx.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libclone.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdecoration.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libcube.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libinputzoom.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libfade.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libopacify.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libmove.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libneg.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libresize.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libplace.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libplane.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libpng.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libput.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libscreenshot.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/librotate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libscale.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libshowdesktop.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsnow.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsplash.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libstate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsvg.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libswitcher.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libjpeg.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwater.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwobbly.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libzoom.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdebug.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsnap.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libthumbnail.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdbus.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libtrailfocus2.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libscreensaver.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libmousegestures.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwidget.so' plugin

I am running version 0.2 from the svn repositories. Any ideas what the problem is?

Thanks

---

### Post by Sqwishy on 2007-02-26
it seems like it didn't install properly?! maybe you should reinstall it?

---

