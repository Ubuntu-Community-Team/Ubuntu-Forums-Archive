---
title: "Could not install my webcam"
date: 2009-02-24
forum: General Help
---

### Post by goodbadwolf on 2009-02-24
Hi. Tried to install my web cam using EasyCam. Have ubuntu 8.10. webcam worked well in 8.04. 

lsusb o/p :

Bus 002 Device 002: ID 0c45:6270 Microdia U-CAM PC Camera NE878
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

on running easycam :

GO !
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-11-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-xext-dev ttf-wqy-zenhei x11proto-kb-dev
  vorbis-tools libgfortran3 ttf-kannada-fonts smplayer-translations libxi-dev
  libaccess-bridge-java libxdmcp-dev libsuitesparse-3.1.0 libarchive-zip-perl
  libseda-java libsox0 libcommons-cli-java libaudio-flac-header-perl
  libswt-gtk-3.4-java xtrans-dev libogg-vorbis-header-perl x11proto-core-dev
  gbsplay libmikmod2 libfile-which-perl ttf-telugu-fonts libxt-dev tzdata-java
  libxext-dev libswt-gnome-gtk-3.4-jni libinline-perl libparse-recdescent-perl
  x11proto-input-dev flac libpthread-stubs0-dev libxau-dev libsox-fmt-base
  libpthread-stubs0 sox libblas3gf liblapack3gf libunicode-string-perl
  libsox-fmt-alsa rhino libmp3-info-perl mpg123 ttf-oriya-fonts libmpg123-0
  mikmod timidity libx11-dev libxcb-xlib0-dev libcommons-lang-java
  libfile-type-perl libxcb1-dev ttf-bengali-fonts libswt-cairo-gtk-3.4-jni
  libid3-3.8.3c2a libswt-gtk-3.4-jni libswt-mozilla-gtk-3.4-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 92 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-source-2.6.24
rm: cannot remove `/lib/modules/2.6.27-11-generic/kernel/drivers/media/video/usbvideo/microdia.ko': No such file or directory
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS= clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CLEAN   /usr/src/linux-headers-2.6.27-11-generic
  CLEAN   .tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/usr/share/EasyCam2/drivers/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /usr/share/EasyCam2/drivers/microdia/microdia-usb.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /usr/share/EasyCam2/drivers/microdia/microdia-usb.c:27:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /usr/share/EasyCam2/drivers/microdia/microdia-usb.c:27:
include/linux/mmzone.h:218: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make[2]: *** [/usr/share/EasyCam2/drivers/microdia/microdia-usb.o] Error 1
make[1]: *** [_module_/usr/share/EasyCam2/drivers/microdia] Error 2
make: *** [driver] Error 2
cp: cannot stat `microdia.ko': No such file or directory
FATAL: Module microdia not found.
FATAL: Module microdia not found.


please help.

---

