---
title: "ImageMagick(++)-dev"
date: 2009-06-17
forum: General Help
---

### Post by idokus on 2009-06-17
I am developing a c++ program using CImg in combination with ImageMagick which adds png support. This worked when I was using ubuntu 8.10.

But now it dies with an "Magick::ErrorMissingDelegate". 

How can I enable Magick to use this delegate png and which delegate should it use? 


The configuration of ImageMagick shows DELEGATES: (..) png (..)
but it is not listed in the LIBS entry (-lpng)

```

:~/convert -list configure

Path: /usr/lib/ImageMagick-6.4.5/config/configure.xml

Name          Value
-------------------------------------------------------------------------------
CC            gcc -std=gnu99
CFLAGS        -fopenmp -g -O2 -Wall -W
CONFIGURE     ./configure  '--prefix=/usr' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--with-gs-font-dir=/usr/share/fonts/type1/gsfonts' '--with-magick-plus-plus' '--with-djvu' '--enable-shared' '--without-dps' '--without-fpx' '--with-perl-options=INSTALLDIRS=vendor' '--x-includes=/usr/include/X11' '--x-libraries=/usr/lib/X11' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
COPYRIGHT     Copyright (C) 1999-2008 ImageMagick Studio LLC
CPPFLAGS      -I/usr/include/ImageMagick
CXX           g++
CXXFLAGS      -g -O2 -Wall -W
DEFS          -DHAVE_CONFIG_H
DELEGATES     bzlib djvu freetype gvc jpeg jp2 lcms openexr png tiff x11 xml wmf zlib
DISTCHECK_CONFIG_FLAGS 'CFLAGS=-g -O2' 'CPPFLAGS=' 'LDFLAGS=-Wl,-Bsymbolic-functions' --disable-deprecated --with-quantum-depth=16 --with-umem=no --with-autotrace=no --with-dps=no --with-fpx=no --with-fontpath= --with-gs-font-dir=/usr/share/fonts/type1/gsfonts
EXEC-PREFIX   /usr
HOST          i686-pc-linux-gnu
LDFLAGS       -L/usr/lib -Wl,-Bsymbolic-functions -L/usr/lib/X11 -lfreetype -lz
LIB_VERSION   0x645
LIB_VERSION_NUMBER 6,4,5,4
LIBS          -lMagickCore -llcms -ltiff -lfreetype -ljpeg -lXext -lSM -lICE -lX11 -lXt -lbz2 -lz -lm -lgomp -lpthread -lltdl
NAME          ImageMagick
PCFLAGS       -fopenmp
PREFIX        /usr
QuantumDepth  16
RELEASE_DATE  2009-06-04
VERSION       6.4.5
WEBSITE       http://www.imagemagick.org



```


I am using kubuntu 9.04, with ImageMagick 6.4.5 and libpng12

---

### Post by idokus on 2009-06-18
Convert does work with png and I've tried bmp as well to no avail, so appearently ImageMagick has png support but the C++ interface doesn't

---

### Post by dtschump on 2009-06-25
Getting PNG support in CImg can be actually done more 'natively', simply by pre-defining the macro 'cimg_use_png' prior to the inclusion of CImg.h, then by linking your code with the libpng library.

---

