---
title: "Compiz and Beryl Acting Sparattic"
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by Opiemsith1 on 2007-07-26
So I was using Beryl and it was working great. Then I found out about Compiz Fusion which looked better so I went to install that following this guide: [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

After I followed that guide then whenever I enabled compiz the top bar of the program window would disappear. So I uninstalled that and to reinstall desktop effects I had to reinstall a bunch of compiz stuff. Now whenever I use Beryl that same problem happens and the only window manager I can select is Emerald. So I tried the normal desktop effects and when I click enable the window grays out so I can't close it and my CPU usage goes to 100% until I restart gnome...

This is what I get when switching to Beryl:

android@android-desktop:~$ beryl-manager
android@android-desktop:~$ **************************************************************
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

libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libblurfx.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libresize.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libpng.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwobbly.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libthumbnail.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdecoration.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libput.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libfade.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libcrashhandler.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsnap.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libannotate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libbench.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libanimation.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libtrailfocus2.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libmove.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libimgjpeg.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdbus.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwater.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/librotate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/lib3d.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libtext.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libplace.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsplash.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libstate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libswitcher.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libfadedesktop.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsvg.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libscale.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libneg.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libopacify.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libscreenshot.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libclone.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libinputzoom.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libcube.so' plugin
Reloading options

** (beryl-manager:8959): WARNING **: Beryl caught deadly signal 13
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by benx009 on 2007-07-26
hmmm... i'm guessing that your experience with (and eventual uninstall of) compiz fusion may have messed with some beryl settings and some, from the looks of it, beryl files as well.  did you uninstall beryl before trying out compiz fusion?  in any case, i would go for a complete uninstall of all things beryl/compiz/emerald that might still be lurking on your system and then doing a complete reinstall of them through synaptic.

---

### Post by Opiemsith1 on 2007-07-26
I did uninstall beryl before trying out Compiz Fusion. Anyway I did what you said and now this happens:
android@android-desktop:~$ beryl-manager
android@android-desktop:~$ emerald: error while loading shared libraries: libemeraldengine.so.0: cannot open shared object file: No such file or directory
emerald: error while loading shared libraries: libemeraldengine.so.0: cannot open shared object file: No such file or directory
beryl: error while loading shared libraries: libberylsettings.so.0: cannot open shared object file: No such file or directory
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

The emerald option is grayed out and beryl just crashes every time I try to run it

---

### Post by Opiemsith1 on 2007-07-28
So no one is going to help me? Because I did completely remove everything from synaptic and reinstalled it and it still gives me that error

---

### Post by Opiemsith1 on 2007-07-30
RESOLVED:

I followed a guide to install Compiz Fusion I found on Digg today and now emerald and fusion work great!

---

