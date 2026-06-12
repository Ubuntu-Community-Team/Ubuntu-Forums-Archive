---
title: "beryl problem"
date: 2007-03-03
forum: Desktop Environments
---

### Post by sdrubolo on 2007-03-03
Hi folks,
I don't know how many times I tried to install beryl, today I installed the 2.0 version.
when I try to launch beryl-xgl I get this error message :
> 
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libgroup.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libshowdesktop.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libinputzoom.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libannotate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsnap.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libresize.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/librotate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsnow.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libzoom.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libbench.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libneg.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libthumbnail.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libtile.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libpng.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsplash.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdebug.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libput.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libopacify.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwallpaper.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsvg.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libmove.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwater.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libanimation.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwobbly.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libtrailfocus2.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libswitcher.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libstate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libplace.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libplane.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libblurfx.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libscreenshot.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdecoration.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libclone.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/lib3d.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libcube.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libscale.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libcrashhandler.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libfade.so' plugin


May anyone explain me why I get this daunting message?
Thanks
](*,)

---

### Post by sdrubolo on 2007-03-03
I've forgotten to say that I have a beryl edgy with a ATI X1600

---

### Post by Mytholody on 2007-03-03
You might want to try a complete uninstall install of beryl (It appears some of the libraries may have moved in edgy? not sure). But Anyways, theres a few threads in the ubuntu forums showing you how to do this. [[COLOR="Blue"]This one is an error similar to yours[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2203236") and [[COLOR="Blue"]hopefully this one will fix it[/COLOR]]("http://ubuntuforums.org/showthread.php?t=354228&highlight=reinstall+beryl+howto"). You may want to try and copy and paste errors into the forum search or  your favorite search engine and see what comes up. Usually you will find a solution and can begin immediately :) . I wish you good luck in fixing your problem, I know I had an annoying time getting mine up and running. Enjoy!

---

### Post by sdrubolo on 2007-03-03
Thank you so much, beryl is working now. Thanks^100000

---

