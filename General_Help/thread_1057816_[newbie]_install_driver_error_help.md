---
title: "[newbie] /install driver error help"
date: 2009-02-02
forum: General Help
---

### Post by scrilla on 2009-02-02
i've been trying to install my drivers for my integrated gfx card for my machine. it uses Intel® 82845G Graphics Controller aka (i915). i got the tarball extracted and tried to sudo ./install and i got the following error. im really confused as what i need to do ive only been using linux for 3 days. ive learned a lot just trying to get this damn video over 800x600 but its starting to get frustrating. any suggestions on what i may need to do? below is the following error i get after trying to execute the install. NOTE: there is no rpm for this just a tarball on the intel site.


The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.



here is the dri.log
> make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/scrilla/Desktop/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/scrilla/Desktop/dripkg/agpgart-2.0/backend.o
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c:68: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c:88: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function ‘inter_module_register’
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function ‘inter_module_unregister’
make[2]: *** [/home/scrilla/Desktop/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/scrilla/Desktop/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/scrilla/Desktop/dripkg/drm'
+ ln -s Makefile.linux Makefile
make -C /lib/modules/2.6.27-11-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
rm: cannot remove `/home/scrilla/Desktop/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/scrilla/Desktop/dripkg/drm'
make: *** [gdg.ko] Error 2

---

### Post by gettinoriginal on 2009-02-02
Is there some special reason you are trying to install the drivers?  Have you tried going to System, Administration, Hardware Drivers?

And by the way, welcome to Ubuntu

---

### Post by scrilla on 2009-02-02
yeah the special reason im trying to install the drivers is because im trying to get over 800x600 resolution. everything i attempt fails to fix the problem.

---

### Post by gettinoriginal on 2009-02-02
Check System, Administration, Software Sources and make sure the first 4 boxes are checked, then under third party, make sure all but CD are checked.  It may ask you to reload, do so, then try System, Administration, Hardware Drivers again.

---

### Post by cmani on 2009-02-06
I am also getting the same error, when googled this issue was posted in buglist as the drm kernals are outdated with ubuntu 8.04 / 8.10.  From the package manager installed xorg-xvesa-intel package also in the description it was mentioned it will support all i815, i915 cards. but no luck :(
Did some have the compiled file or workaround

---

### Post by gettinoriginal on 2009-02-06
Can you both please post your xorg.conf files here:
```
sudo gedit /etc/X11/xorg.conf
```

---

