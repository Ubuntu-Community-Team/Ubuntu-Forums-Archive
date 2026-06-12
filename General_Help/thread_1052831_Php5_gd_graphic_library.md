---
title: "Php5 gd graphic library"
date: 2009-01-28
forum: General Help
---

### Post by incanuz on 2009-01-28
Hello everyone, I am having an issue with the gd library that is in Ubuntu repositories. I need an updated version of this library in order to use a reflection script i have downloaded.

After doing sudo apt-get install php5-gd, I got a package containing and old version of this library and get an error suggesting to update to at least 2.0.1 version, though 2.0.28 is recommended. The last stable version of libgd according to the sites homepage is 2.0.35, and phpinfo() says that the one in Ubuntu repos is 2.0.0, which is rather old.

Does anyone know how to solve this? I have managed to download and compile from source, but dont know where to install this libraries, the default "make install" puts them somewhere that php does not recognize.

Thanks in advanced
Santiago

---

### Post by indiehead on 2009-01-28
i've got the same problem with the GD Library and Wordpress.

I Installed the GD Library thru aptitude but get the old version.

can you post your ./configure statement for building from source?

appreciate it,



John.

---

### Post by incanuz on 2009-01-28
The statement is used was just "./configure", anything else. At first I didnt got any PNG or JPEG support, but after installing the develepment packages for this libraries i got support ( i think the name of the packages are libjpeg-dev and libpng-dev).
Hope this helps you, please let me know if you get the new release working! Thanks


** Configuration summary for gd 2.0.34:

   Support for PNG library:          yes
   Support for JPEG library:         yes
   Support for Freetype 2.x library: no
   Support for Fontconfig library:   no
   Support for Xpm library:          no
   Support for pthreads:             yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating config/Makefile
config.status: creating config/gdlib-config
config.status: creating test/Makefile
config.status: creating config.h
config.status: executing depfiles commands

---

### Post by indiehead on 2009-01-28
thanks, thought you used some specific options to build it on your machine.

with regards to install location you can specify that with the prefix...


./configure --prefix=/usr/local

and that'll stick the binaries in /usr/local/php

then you can add them to your bash profile so it loads them in

mate ~/.bash_profile

export PATH=/usr/local/bin:$PATH

---

### Post by incanuz on 2009-01-28
There is something i still dont get, with the compiled stuff, how do i make php recognize it?

After compilation i get this tree folders: 

santiago@santiago-laptop:~/gdTEST$ ls
bin  include  lib

santiago@santiago-laptop:~/gdTEST$ ls bin
annotate  gd2copypal  gd2topng  gdlib-config  gdtopng   pngtogd   webpng
bdftogd   gd2togif    gdcmpgif  gdparttopng   giftogd2  pngtogd2

santiago@santiago-laptop:~/gdTEST$ ls include
entities.h  gdfontg.h  gdfontmb.h  gdfontt.h  gd.h
gdcache.h   gdfontl.h  gdfonts.h   gdfx.h     gd_io.h

santiago@santiago-laptop:~/gdTEST$ ls lib
libgd.a  libgd.la  libgd.so  libgd.so.2  libgd.so.2.0.0


My doubt is, where do i place this files in ubuntu 8.04, and how do i tell php apache modulo to use this libs?? Thanks again =)

---

### Post by incanuz on 2009-01-29
bump

---

