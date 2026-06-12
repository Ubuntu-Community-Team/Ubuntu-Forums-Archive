---
title: "Beryl@AIGLX and &quot;cut&quot; windows"
date: 2007-02-07
forum: Desktop Environments
---

### Post by embrion on 2007-02-07
Hi,

I've installed BERYL with AIGLX using this thwo guides:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX")
[https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy")
Additionally I installed some extra plugins/files connected with Beryl.

I use ati driver with Mobile Radeon 9200. The problem is when I turn on Beryl-manager and Beryl starts I end up with no ability to writing, "cut" windows tops (see pic.) and some other things. When I switch back to GNOME I got everything fine again.
This is what I get after Beryl-manager launch:

```

root@embrion-hp:~# beryl
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
Checking maximum texture size                   : passed (2048x2048)

libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libcube.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libscreenshot.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsplash.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libresize.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libplace.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/lib3d.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libmove.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdecoration.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libswitcher.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libcrashhandler.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libblurfx.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwater.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libclone.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libbench.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwobbly.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libneg.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libput.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libanimation.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libscale.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libinputzoom.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libstate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/librotate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libfade.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libannotate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libgroup.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libplane.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsettings.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libshowdesktop.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libtrailfocus.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libzoom.so' plugin
libGL warning: 3D driver claims to not support visual 0x4b
Reloading options


```

[[IMG]http://img481.imageshack.us/img481/6736/zrzutekranugf9.th.png[/IMG]](http://img481.imageshack.us/my.php?image=zrzutekranugf9.png)


I thought it's GNOME theme problem but I tried to change for Beryl/Emerald one (fortunatelly mouse was working) and:

```

(emerald:5704): Gdk-CRITICAL **: gdk_drawable_unref: assertion `GDK_IS_DRAWABLE (drawable)' failed
Reloading...
```

TIA.

---

