---
title: "ATI Script Install, need help with error."
date: 2007-03-12
forum: Desktop Environments
---

### Post by mijink on 2007-03-12
Hello, I'm somewhat a noob when it comes to Ubuntu (I've played with linux enough to be enticed to play with it more). Anyhow, onto my issue... I have downloaded the ATI drivers for my system (.Run file) and have followed the guide found [HERE]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Install_the_8.28.8_Driver_the_Ubuntu_Way"). However, I get the following error:

```
mijink@mijink-desktop:~/Desktop$ sh ati-driver-installer-8.34.8-x86.x86_64.run --buildpkg Ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.34.8..................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
cp: writing `/tmp/fglrx.ev8413/usr/X11R6/lib/modules/dri/fglrx_dri.so': No space left on device
cp: cannot create directory `/tmp/fglrx.ev8413/usr/sbin': No space left on device
cp: cannot create directory `/tmp/fglrx.ev8413/etc': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/make.sh': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/agp.h': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/agp3.c': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/agp_backend.h': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/agpgart.h': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/agpgart_be.c': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/i7505-agp.c': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/nvidia-agp.c': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/drm.h': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/drmP.h': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/drm_os_linux.h': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/drm_proc.h': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/drm_compat.h': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/firegl_public.c': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/firegl_public.h': No space left on device
cp: cannot create directory `/tmp/fglrx.ev8413/lib/modules/fglrx/build_mod/2.6.x': No space left on device
cp: writing `/tmp/fglrx.ev8413/lib/modules/fglrx/make_install.sh': No space left on device
cp: cannot create directory `/tmp/fglrx.ev8413/opt': No space left on device
cp: cannot create directory `/tmp/fglrx.ev8413/usr/share': No space left on device
cp: cannot create directory `/tmp/fglrx.ev8413/usr/X11R6/include': No space left on device
cp: cannot create directory `/tmp/fglrx.ev8413/usr/include': No space left on device
cp: cannot create directory `/tmp/fglrx.ev8413/usr/sbin': No space left on device
cp: cannot create directory `/tmp/fglrx.ev8413/usr/src': No space left on device
cp: writing `/tmp/fglrx.ev8413/usr/X11R6/bin/fireglcontrolpanel': No space left on device
cp: cannot create directory `/tmp/fglrx.ev8413/debian': No space left on device
cp: cannot create directory `/tmp/fglrx.ev8413/module': No space left on device
./packages/Ubuntu/ati-packager.sh: line 34: /tmp/fglrx.ev8413/debian/changelog: No such file or directory
./packages/Ubuntu/ati-packager.sh: line 36: /tmp/fglrx.ev8413/debian/changelog: No such file or directory
./packages/Ubuntu/ati-packager.sh: line 38: /tmp/fglrx.ev8413/debian/changelog: No such file or directory
Package build failed!
Package build utility output:
Removing temporary directory: fglrx-install
mijink@mijink-desktop:~/Desktop$ 


```

I'm not sure if I did not allow enough space on the partitions I setup or what... I used the exact space that it suggested for the Root, and Swap parts. If I need to expand the swap or root part please suggest how I do this and by how much... currently root is 2gb and swap is about 300mb while the other is 20gb.

---

### Post by mijink on 2007-03-12
Never mind about my above post, I used Method #1 and it seems to be working now, no errors. Screen looks much better now with a higher rez and better refresh rate.

---

