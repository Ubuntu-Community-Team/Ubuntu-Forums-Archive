---
title: "Beryl Help yet again"
date: 2007-02-14
forum: Desktop Environments
---

### Post by ajmorris on 2007-02-14
when i run beryl-manger and switch to beryl window manager i get this huge message :

```
Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : failed

No GLX_SGIX_fbconfig
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libgroup.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libshowdesktop.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libinputzoom.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libannotate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libresize.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/librotate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libsnow.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libzoom.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libbench.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libneg.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libtrailfocus.so' plugin
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
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libswitcher.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libstate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libplace.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libplane.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libblurfx.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libscreenshot.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdecoration.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdbus.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libclone.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/lib3d.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libjpeg.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libcube.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libscale.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libcrashhandler.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libfade.so' plugin
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

Any ideas?

---

### Post by Waappu on 2007-02-15
Hi

I think you are missing some packages.
Type in terminal```
sudo aptitude reinstall beryl emerald
```

---

### Post by ajmorris on 2007-02-15
Thanks, I will do that at home tonight. I am at school now and i get a size mismatch when trying to download at school.

---

### Post by ajmorris on 2007-02-15
> **Waappu said:**
> Hi

I think you are missing some packages.
Type in terminal```
sudo aptitude reinstall beryl emerald
```

When i run this i get:
```
Need to get 0B of archives. After unpacking 733kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate file for the beryl package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
```

 i ran ```
sudo aptitude reinstall beryl emerald
```
I have cleaned synaptic's cache yesterday so i need to download it. How can i make it so it doesn't think there is the package in the cache, (other than going into Synaptic and marking it for re-install)?


Also in synaptic the box for re-installation for those pacakges is greyed out so i can only remove it and then install again.

---

