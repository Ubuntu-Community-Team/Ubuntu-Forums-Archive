---
title: "GIMP and EXIF"
date: 2009-06-15
forum: General Help
---

### Post by nickcollie on 2009-06-15
Can someone explain in very simple terms how to install the exif browser add on to gimp.

I am using Hardy 8.04 and Gimp 2.4.5.  I have libexif 0.6.16-2.

In the instructions it says:

   1.  gunzip exif-browser.tar.gz
   2. tar xcf exif-browser.tar
   3. cd exif-browser
   4. ./configure
   5. make
   6. sudo make install

I download it and extract it fine.  When I ./configure I get errors.  The important bit of which seems to be at the bottom!  Thanks guys it would be great to be able to use this.  I am sure that I am making a beginners error.

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking for gimp-2.0 gimpui-2.0 libexif >= 0.5.9... Package gimp-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimp-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimp-2.0' found Package gimpui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimpui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimpui-2.0' found Package libexif was not found in the pkg-config search path. Perhaps you should add the directory containing `libexif.pc' to the PKG_CONFIG_PATH environment variable No package 'libexif' found

```

---

### Post by jynyl on 2010-05-24
There is an exif plugin for the gimp over here; [http://registry.gimp.org/node/8839]("http://registry.gimp.org/node/8839").
Before you compile and install this, you need to add these packages from the Ubuntu repository; libexif, libexif-dev, libgimp2.0-dev.

---

### Post by StuartN on 2010-05-24
> **nickcollie said:**
> Can someone explain in very simple terms how to install the exif browser add on to gimp.

I am using Hardy 8.04 and Gimp 2.4.5.

Possibly the versions of Gimp and libexif that you are using are not provided by a package recognized by the version of the plugin that you are using, because the versions of Gimp and the plugin are too far apart:

> checking for gimp-2.0 gimpui-2.0 libexif >= 0.5.9... **Package gimp-2.0 was not found in the pkg-config search path**. Perhaps you should add the directory containing `gimp-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimp-2.0' found **Package gimpui-2.0 was not found** in the pkg-config search path. Perhaps you should add the directory containing `gimpui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimpui-2.0' found **Package libexif was not found** in the pkg-config search path. Perhaps you should add the directory containing `libexif.pc' to the PKG_CONFIG_PATH environment variable No package 'libexif' found

Where was the plugin from? There may be another source with a different version - I can't tell if you need a newer or an older plugin, but probably older because Gimp is now 2.6.8

It might not suit you, but gThumb has a very good EXIF display in a separate window, that can be resized and scrolled but remains synchronized with the currently viewed image.

---

