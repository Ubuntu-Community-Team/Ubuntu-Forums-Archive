---
title: "Installing navit"
date: 2008-12-16
forum: General Help
---

### Post by lcruz007 on 2008-12-16
Hi,
I have some problems when I try to install navit. I get some errors when I use "make"... Can someone help me with my problem? I need this program by this week... Here's part of the outcome I get: 

...
```
make[4]: Entering directory `/home/luis/navit/navit/font'
Making all in freetype
make[5]: Entering directory `/home/luis/navit/navit/font/freetype'
/bin/bash ../../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../..  -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/freetype2    -I../../../navit -DMODULE=font_freetype   -g -O2 -Wall -Wcast-align -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wpointer-arith -Wreturn-type -D_GNU_SOURCE -ffast-math -MT font_freetype.lo -MD -MP -MF .deps/font_freetype.Tpo -c -o font_freetype.lo font_freetype.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../../.. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I../../../navit -DMODULE=font_freetype -g -O2 -Wall -Wcast-align -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wpointer-arith -Wreturn-type -D_GNU_SOURCE -ffast-math -MT font_freetype.lo -MD -MP -MF .deps/font_freetype.Tpo -c font_freetype.c  -fPIC -DPIC -o .libs/font_freetype.o
font_freetype.c:1:35: error: fontconfig/fontconfig.h: No such file or directory
font_freetype.c: In function &#8216;font_freetype_font_new&#8217;:
font_freetype.c:271: error: &#8216;FcPattern&#8217; undeclared (first use in this function)
font_freetype.c:271: error: (Each undeclared identifier is reported only once
font_freetype.c:271: error: for each function it appears in.)
font_freetype.c:271: error: &#8216;required&#8217; undeclared (first use in this function)
font_freetype.c:272: warning: implicit declaration of function &#8216;FcPatternBuild&#8217;
font_freetype.c:272: error: &#8216;FC_FAMILY&#8217; undeclared (first use in this function)
font_freetype.c:272: error: &#8216;FcTypeString&#8217; undeclared (first use in this function)
font_freetype.c:275: warning: implicit declaration of function &#8216;FcPatternAddInteger&#8217;
font_freetype.c:275: error: &#8216;FC_WEIGHT&#8217; undeclared (first use in this function)
font_freetype.c:276: error: &#8216;FC_WEIGHT_BOLD&#8217; undeclared (first use in this function)
font_freetype.c:277: warning: implicit declaration of function &#8216;FcConfigSubstitute&#8217;
font_freetype.c:277: warning: implicit declaration of function &#8216;FcConfigGetCurrent&#8217;
font_freetype.c:278: error: &#8216;FcMatchFont&#8217; undeclared (first use in this function)
font_freetype.c:279: warning: implicit declaration of function &#8216;FcDefaultSubstitute&#8217;
font_freetype.c:280: error: &#8216;FcResult&#8217; undeclared (first use in this function)
font_freetype.c:280: error: expected &#8216;;&#8217; before &#8216;result&#8217;
font_freetype.c:281: error: &#8216;matched&#8217; undeclared (first use in this function)
font_freetype.c:282: warning: implicit declaration of function &#8216;FcFontMatch&#8217;
font_freetype.c:283: error: &#8216;result&#8217; undeclared (first use in this function)
font_freetype.c:285: error: &#8216;FcValue&#8217; undeclared (first use in this function)
font_freetype.c:285: error: expected &#8216;;&#8217; before &#8216;v1&#8217;
font_freetype.c:286: error: &#8216;FcChar8&#8217; undeclared (first use in this function)
font_freetype.c:286: error: &#8216;fontfile&#8217; undeclared (first use in this function)
font_freetype.c:288: warning: implicit declaration of function &#8216;FcPatternGet&#8217;
font_freetype.c:288: error: &#8216;v1&#8217; undeclared (first use in this function)
font_freetype.c:289: error: &#8216;v2&#8217; undeclared (first use in this function)
font_freetype.c:290: error: expected &#8216;;&#8217; before &#8216;r1&#8217;
font_freetype.c:293: error: expected &#8216;;&#8217; before &#8216;r2&#8217;
font_freetype.c:296: error: &#8216;r1&#8217; undeclared (first use in this function)
font_freetype.c:296: error: &#8216;FcResultMatch&#8217; undeclared (first use in this function)
font_freetype.c:297: error: &#8216;r2&#8217; undeclared (first use in this function)
font_freetype.c:298: warning: implicit declaration of function &#8216;FcValueEqual&#8217;
font_freetype.c:308: warning: implicit declaration of function &#8216;FcPatternDestroy&#8217;
font_freetype.c: In function &#8216;plugin_init&#8217;:
font_freetype.c:520: warning: implicit declaration of function &#8216;FcInit&#8217;
make[5]: *** [font_freetype.lo] Error 1
make[5]: Leaving directory `/home/luis/navit/navit/font/freetype'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/luis/navit/navit/font'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/luis/navit/navit'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/luis/navit/navit'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/luis/navit'
make: *** [all] Error 2
```

Thanks in advance.

---

### Post by mc4man on 2008-12-17
It seems pretty straightforward to build. Your best bet would be to go here and make sure you have ALL the minimum dependies satisfied.
Search them out in synaptic and install.

[http://wiki.navit-project.org/index.php/Ubuntu_dependencies](http://wiki.navit-project.org/index.php/Ubuntu_dependencies)

If you can't find something then  don't use the full name shown, just the first.

For example - libtiff-dev, just search libtiff, the package is actually libtiff4-dev

As far as the optionals, that's up to you, don't think you'll need the OpenGl gui.

After installing all the deps then follow instructions here

[http://wiki.navit-project.org/index.php/NavIt_on_Linux](http://wiki.navit-project.org/index.php/NavIt_on_Linux)

I'd break the build command up 

```
./autogen.sh 
```

then either ```
./configure --prefix=/usr
``` or just  ```
./configure
```

At the end of the configure check the results (summary
(at any point you can run ./configure --help to ck. options

Then run make

Note: if you want to make a checkinstall .deb to install from then install checkinstall.
After the make run (to make .deb and install
```
sudo checkinstall
```

or to make a .deb and not install now
```
sudo checkinstall --install=no
```

Note: you'll have to change the version number for checkinstall ,either do it at the beginning when the list comes up or you'll be prompted to a bit later.
To change you'd type 3, press enter and then enter the new ver. number - 0.1 is no good, try anything else 0.2, 0.3 ect. or just use 1.0



Edit: if your on 8.10 and want to use checkinstall use this

```
sudo checkinstall --fstrans=no
```  
or
```
sudo checkinstall --fstrans=no --install=no
```

---

### Post by lcruz007 on 2008-12-17
Hi,
Thanks for your reply. I installed all the dependency packages(even the optional ones), and did what you told me, but I still cannot install it...!

```
make[6]: Leaving directory `/home/luis/navit/navit/gui/cegui/datafiles'
make[5]: Leaving directory `/home/luis/navit/navit/gui/cegui/datafiles'
make[5]: Entering directory `/home/luis/navit/navit/gui/cegui'
/bin/bash ../../../libtool --tag=CXX   --mode=link g++  -g -O2 -Wall -Wcast-align -Wmissing-prototypes -Wstrict-prototypes -Wpointer-arith -Wreturn-type -D_GNU_SOURCE   -o libgui_cegui.la -rpath /usr/local/lib/navit/gui gui_sdl_window.lo sdl_events.lo wmcontrol.lo cegui_keyboard.lo -lSDL -lCEGUIBase -lCEGUIOpenGLRenderer -lCEGUIFalagardWRBase -lCEGUIXercesParser -lCEGUITinyXMLParser -lCEGUIDevILImageCodec -lCEGUITGAImageCodec  -lGL -lGLU -lGLC -lm -rdynamic
libtool: link: cannot find the library `/usr/lib/libtiff.la' or unhandled argument `/usr/lib/libtiff.la'
make[5]: *** [libgui_cegui.la] Error 1
make[5]: Leaving directory `/home/luis/navit/navit/gui/cegui'
make[4]: *** [install-recursive] Error 1
make[4]: Leaving directory `/home/luis/navit/navit/gui/cegui'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/luis/navit/navit/gui'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/luis/navit/navit'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/luis/navit/navit'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.


```

---

### Post by lcruz007 on 2008-12-18
bump

---

### Post by lcruz007 on 2008-12-20
someone?

---

### Post by AgentWD-40 on 2009-08-25
Same problem here. I was hoping to eventually install this on a car PC for navigation. Has anybody actually installed this? I'm running 9.04.

---

### Post by Ixtao on 2009-10-21
Yes, check out [this repository]("http://navit.latouche.info/ubuntu/"). I got an error activating the gpg key, but after saving the key into a file and manually importing it in synaptic Navit is now installed and works. I run an up to date 9.10

---

### Post by icodemonkey on 2009-11-02
> **Ixtao said:**
> Yes, check out [this repository]("http://navit.latouche.info/ubuntu/"). I got an error activating the gpg key, but after saving the key into a file and manually importing it in synaptic Navit is now installed and works. I run an up to date 9.10
how did you import the key i keep getting errors?

---

### Post by jap1968 on 2009-11-05
> **icodemonkey said:**
> how did you import the key i keep getting errors?

There are several blog entries about people having installed Navit under Linux. I will recommend a couple of them:

[http://www.len.ro/2009/07/navit-gps-on-a-acer-aspire-one](http://www.len.ro/2009/07/navit-gps-on-a-acer-aspire-one)
[http://ospatia.blogspot.com/2009/01/gps-para-linux-ii.html](http://ospatia.blogspot.com/2009/01/gps-para-linux-ii.html)

On the comments of the second article you will find instructions about how to import keys.

---

