---
title: "&quot;Field has incomplete type&quot; while compiling"
date: 2009-01-16
forum: General Help
---

### Post by JoyceBabu on 2009-01-16
Hello all,

I want to compile the software 'Maitreya' ([http://www.saravali.de/maitreya/](http://www.saravali.de/maitreya/)). But when I compile, I am getting the error
> In file included from Ashtakavarga.cpp:25:
Conf.h:71: error: field ‘color_fg’ has incomplete type
Conf.h:71: error: field ‘color_fg2’ has incomplete type
Conf.h:71: error: field ‘color_fg3’ has incomplete type
Conf.h:71: error: field ‘color_bg’ has incomplete type
Conf.h:71: error: field ‘color_bg2’ has incomplete type
Conf.h:71: error: field ‘color_marked’ has incomplete type
Conf.h:71: error: field ‘color_benefic’ has incomplete type
Conf.h:71: error: field ‘color_malefic’ has incomplete type
make[4]: *** [Ashtakavarga.o] Error 1
make[4]: Leaving directory `/home/joyce/Desktop/Astro/maitreya/src/jyotish'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/joyce/Desktop/Astro/maitreya/src/jyotish'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/joyce/Desktop/Astro/maitreya/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/joyce/Desktop/Astro/maitreya'
make: *** [all] Error 2


Can someone please tell me what to do? Thanks

---

### Post by almodovaris on 2009-02-22
$ sudo apt-get update
 $ sudo apt-get install checkinstall build-essential dh-make devscripts fakeroot patch diff patchutils lintian autotools-dev
 $ sudo apt-get install libwxbase2.8-0 libwxbase2.8-dev libwxgtk2.8-0 libwxgtk2.8-dev wx2.8-headers wx2.8-i18n bison
 $ cd maitreya-5.0.1
 $ ./configure
 $ make

[Now you install the MaitreyaSymbols.ttf font from src/fonts]

 $ sudo make install
 $ maitreya

---

### Post by JoyceBabu on 2009-02-22
almodovaris,

Thanks a lot for the reply. But I had managed to compile it on Window and check my modification. I will compile it on Ubuntu again this weekend. :)

---

