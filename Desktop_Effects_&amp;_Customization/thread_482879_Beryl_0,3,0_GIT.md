---
title: "Beryl 0,3,0 GIT"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by ucsblaw on 2007-06-24
so i updated today to beryl 0.3.0 and now...beryl doesnt work. I cant use the cube or anything else...this obviously sucks.. I was using 0.2.0 and everything was fine...i got greedy once again and now im more than annoyed...any suggestions?

should i downgrade? Uninstall (if that's even the correct term here)? Or are there any fixes for my problem

oh and before i forget...when beryl is on my windows dont have borders...regardless of whether i use beryl window decorator or heliodor ( i think the update involved heliodor too)

thanks

---

### Post by ucsblaw on 2007-06-24
here is some more information...im running feisty with an nvidia geforce 6400 

in terminal when i type 'beryl' i get

> bearmen8@adsl-75-50-152-243:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Reloading options
beryl: '/usr/lib/beryl/libanimation.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libanimation.so' has version 0.
beryl: Couldn't load plugin 'animation'
beryl: '/usr/lib/beryl/libwater.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libwater.so' has version 0.
beryl: Couldn't load plugin 'water'
beryl: '/usr/lib/beryl/libjpeg.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libjpeg.so' has version 3.
beryl: Couldn't load plugin 'jpeg'
beryl: '/usr/lib/beryl/librotate.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/librotate.so' has version 0.
beryl: Couldn't load plugin 'rotate'
beryl: '/usr/lib/beryl/libsplash.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libsplash.so' has version 0.
beryl: Couldn't load plugin 'splash'
beryl: '/usr/lib/beryl/lib3d.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/lib3d.so' has version 0.
beryl: Couldn't load plugin '3d'
beryl: '/usr/lib/beryl/libdecoration.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libdecoration.so' has version 0.
beryl: Couldn't load plugin 'decoration'
beryl: '/usr/lib/beryl/libobs.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libobs.so' has version 0.
beryl: Couldn't load plugin 'obs'
beryl: '/usr/lib/beryl/libinputzoom.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libinputzoom.so' has version 1.
beryl: Couldn't load plugin 'inputzoom'
beryl: '/usr/lib/beryl/libsvg.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libsvg.so' has version 3.
beryl: Couldn't load plugin 'svg'
beryl: '/usr/lib/beryl/libscale.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libscale.so' has version 0.
beryl: Couldn't load plugin 'scale'
beryl: '/usr/lib/beryl/libmove.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libmove.so' has version 0.
beryl: Couldn't load plugin 'move'
beryl: '/usr/lib/beryl/libplace.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libplace.so' has version 0.
beryl: Couldn't load plugin 'place'
beryl: '/usr/lib/beryl/libresize.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libresize.so' has version 1.
beryl: Couldn't load plugin 'resize'
beryl: '/usr/lib/beryl/libwobbly.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libwobbly.so' has version 1.
beryl: Couldn't load plugin 'wobbly'
beryl: '/usr/lib/beryl/libtext.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libtext.so' has version 1.
beryl: Couldn't load plugin 'text'
beryl: '/usr/lib/beryl/libgroup.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libgroup.so' has version 0.
beryl: Couldn't load plugin 'group'
beryl: '/usr/lib/beryl/libpng.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libpng.so' has version 2.
beryl: Couldn't load plugin 'png'
beryl: '/usr/lib/beryl/libdbus.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libdbus.so' has version 0.
beryl: Couldn't load plugin 'dbus'
beryl: '/usr/lib/beryl/libswitcher.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libswitcher.so' has version 0.
beryl: Couldn't load plugin 'switcher'
beryl: '/usr/lib/beryl/libcube.so' plugin version does not match beryl version.
beryl is of version 50, but plugin '/usr/lib/beryl/libcube.so' has version 2.
beryl: Couldn't load plugin 'cube'
beryl: pixmap 0x2c0008d can't be bound to texture
beryl: Couldn't bind redirected window 0xa00003 to texture
beryl: pixmap 0x2c0008f can't be bound to texture
beryl: Couldn't bind redirected window 0x2600098 to texture
beryl: pixmap 0x2c00091 can't be bound to texture
beryl: Couldn't bind redirected window 0x2a00020 to texture


---

### Post by ucsblaw on 2007-06-24
anyone?

---

### Post by andrewsomething on 2007-06-24
Did you update these packages as well?

beryl-plugins
beryl-plugins-data
beryl-plugins-unsupported
beryl-plugins-unsupported-data

Go into Synaptic and search for Beryl. Make sure all you installed Beryl packages are the same version.

---

### Post by ucsblaw on 2007-06-25
i never had a chance to try what u suggested. I installed compiz-fusion...and my computer completey crashed. I was running feisty on Wubi and after installing compiz fusion I had some problems. It was running well at first but while messing around with it my computer froze and i could do anything but manually shut down my computer. When i restarted I couldnt boot XP or Ubuntu. My computer just kept restarting in an endless loop. I ended up reinstalling everything...fortunately i had things backed up

thanks anyway.

just curious...is Beryl 0.3.0 safe to use or should i just stick with 0.2.0.

---

### Post by kpolice on 2007-06-25
Beryl is dead so it's the same.

---

