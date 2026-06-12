---
title: "Kick-ass splash engine for KDE"
date: 2005-06-26
forum: Desktop Environments
---

### Post by dolny on 2005-06-26
Splash Screen Engine for KDE. Heavily customizable engine for various types of themes.

[img]http://www.kde-look.org/content/pre3/25705-3.png[/img]

FEATURES:
- Default MoodinKDE theme included
- Default FingerPrint theme included
- Fading images
- Use current icon set or custom images
- Unlimited Custom text labels
- System information labels
- Set fading delay and length
- Custom image arrangement
- Resolution independent themes

Link: [http://www.kde-look.org/content/show.php?content=25705](http://www.kde-look.org/content/show.php?content=25705)

My output: :( 

```
dolny@milkshake:~/paczki$ sudo dpkg -i ksplash-engine-moodin_0.4_i386.deb
Password:
Zaznaczenie poprzednio niezaznaczonego pakietu ksplash-engine-moodin.
(Odczytywanie bazy danych ... 112757 plików i katalogów obecnie zainstalowanych.)
Rozpakowanie ksplash-engine-moodin (z ksplash-engine-moodin_0.4_i386.deb) ...
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie ksplash-engine-moodin:
 ksplash-engine-moodin zale&#380;y od kdelibs4 (>= 4:3.4.1-1); jednak&#380;e:
  Wersja kdelibs4 w systemie to 4:3.4.1-0ubuntu0hoary1.
 ksplash-engine-moodin zale&#380;y od ksplash (>= 4:3.4.1-1); jednak&#380;e:
  Wersja ksplash w systemie to 4:3.4.1-0ubuntu0hoary2.
 ksplash-engine-moodin zale&#380;y od libidn11 (>= 0.5.13); jednak&#380;e:
  Wersja libidn11 w systemie to 0.5.2-3.
 ksplash-engine-moodin zale&#380;y od libstdc++6 (>= 4.0.0-10); jednak&#380;e:
  Wersja libstdc++6 w systemie to 4.0.0-7ubuntu6~5.04ubp1.
 ksplash-engine-moodin zale&#380;y od libxrender1 (>> 1:0.9.0-1); jednak&#380;e:
  Wersja libxrender1 w systemie to 0.9.0-0ubuntu4.
dpkg: b&#322;&#261;d przetwarzania ksplash-engine-moodin (--install):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 ksplash-engine-moodin

```

Tell me if you manage to install it :(

---

### Post by ltmon on 2005-06-26
You'll need to compile from source, as the package provided only works on Debian unstable not Kubuntu.

I compiled it fairly quickly and easily.  If you have trouble let me know and I'll send you a hacked up package I made with checkinstall (when I get home tonight).

The default theme is really looks good, but I'm not such a fan of the "fingerprint" theme.

Cheers,

L.

---

### Post by wdso on 2005-06-27
It might be a good idea to request a backbort. On the other hand, backporting isn't too complicated. I'd write a little HOWTO if there is any demand.

---

### Post by shakin on 2005-06-27
[QUOTE=ltmon]You'll need to compile from source, as the package provided only works on Debian unstable not Kubuntu.

I compiled it fairly quickly and easily.  If you have trouble let me know and I'll send you a hacked up package I made with checkinstall (when I get home tonight).

The default theme is really looks good, but I'm not such a fan of the "fingerprint" theme.

Cheers,

L.[/QUOTE]

I get some make errors. Not sure what to make of them:

thememoodin.moc:106: error: parse error before `::' token
thememoodin.h:30: error: forward declaration of `class ThemeMoodin'

---

### Post by shakin on 2005-06-27
[QUOTE=shakin]I get some make errors. Not sure what to make of them:

thememoodin.moc:106: error: parse error before `::' token
thememoodin.h:30: error: forward declaration of `class ThemeMoodin'[/QUOTE]

Ahh... needed the kdebase-dev package installed. Works fine now.

---

### Post by fire59 on 2005-06-27
Got it to compiled and installed after I installed kdebase-dev and qt3.

---

### Post by uberlinux on 2005-06-27
Does this have instructions, post compilation, for installation, I havent gotten splashes to work yet...

---

### Post by ltmon on 2005-06-27
Once installed you should just be able to go to 

Settings -> Appearance -> Splash Screen

and select a Moodin theme as your splash screen.

Click the "Test" button to see what it does.

L.

---

### Post by dolny on 2005-06-29
```
dolny@milkshake:~$ sudo apt-get install kdebase-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebase-dev: Depends: kate (= 4:3.4.0-0ubuntu18) but 4:3.4.1-0ubuntu0hoary2 is to be installed
               Depends: kdesktop (= 4:3.4.0-0ubuntu18) but 4:3.4.1-0ubuntu0hoary2 is to be installed
               Depends: kicker (= 4:3.4.0-0ubuntu18) but 4:3.4.1-0ubuntu0hoary2 is to be installed
               Depends: konqueror-nsplugins (= 4:3.4.0-0ubuntu18) but 4:3.4.1-0ubuntu0hoary2 is to be installed
               Depends: konqueror (= 4:3.4.0-0ubuntu18) but 4:3.4.1-0ubuntu0hoary2 is to be installed
               Depends: ksysguard (= 4:3.4.0-0ubuntu18) but 4:3.4.1-0ubuntu0hoary2 is to be installed
               Depends: kwin (= 4:3.4.0-0ubuntu18) but 4:3.4.1-0ubuntu0hoary2 is to be installed
               Depends: kdelibs4-dev (>= 4:3.4.0) but it is not going to be installed
E: Broken packages
```


:(

---

### Post by ltmon on 2005-06-29
I don't think you really need kdebase-dev.  That package is for kdevelop (the IDE) and various other things.  

I'll edit this post when I get home tonight to let you know exactly what you need.

L.

---

### Post by dolny on 2005-06-30
```
checking for Qt... configure: error: Qt (>= Qt 3.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.Make sure that you have compiled Qt with thread support!

```

What specific package do i need? I have libqt3c102-mt - Qt GUI Library (Threaded runtime version), Version 3 installed :/

Doh...

---

### Post by vanaedium on 2005-06-30
when you compile you need the package requested and the relative dev, so check for all qt libraries with dev also and it will works.

---

### Post by hammett111 on 2005-07-07
Yip running awesome on my AMD64 gaming monster. By the way you Blizzard fans out there get ready, my team and I are ready to release native ports of Starcraft/Broodwar and warcraft at a later date.

---

### Post by dolny on 2005-07-07
Cannot install it - too many unresolved dependencies.

---

### Post by jimarko on 2005-08-08
[QUOTE=ltmon]I don't think you really need kdebase-dev.  That package is for kdevelop (the IDE) and various other things.  

I'll edit this post when I get home tonight to let you know exactly what you need.

L.[/QUOTE]

Yeah, i found that you need kdebase-dev, otherwise if you run 'make' it will crash while looking for themeengine.h

This was the only thing holding me back, but i've since got it sorted :)

---

### Post by nickless on 2005-08-30
I have changed my resolution and now I can't see the whole loading screen anymore :(
Also I have no idea how to change the kdm appearence. Changed the background image in the ControlCentre, but it shows still the old look. Just before loading the splash the image I choose blinks for a secound. I know how this was done in gdm by deselecting the "grafical greeter" or something. Where can I do so in kde? :)

---

### Post by patpicos on 2005-09-11
./configure works fine for me :
```
patrick@laptop:~/moodin$ make
make: *** No targets specified and no makefile found.  Stop.
patrick@laptop:~/moodin$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for mcopidl... /usr/bin/mcopidl
checking for artsc-config... /usr/bin/artsc-config
checking for meinproc... /usr/bin/meinproc
checking for xmllint... /usr/bin/xmllint
checking whether byte ordering is bigendian... no
checking for MAXPATHLEN... 4096
checking if src should be compiled... yes
configure: creating ./config.status
fast creating Makefile
fast creating src/Makefile
config.pl: fast created 2 file(s).
config.status: creating config.h
config.status: executing depfiles commands

Good - your configure finished. Start make now
``` 


But when i try to sudo make, it bombs on me :

```
patrick@laptop:~/moodin$ sudo make
make  all-recursive
make[1]: Entering directory `/home/patrick/moodin'
Making all in src
make[2]: Entering directory `/home/patrick/moodin/src'
if /bin/sh ../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I/usr/X11R6/include  -I/usr/include/kde/ksplash  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wno-non-virtual-dtor -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT thememoodin.lo -MD -MP -MF ".deps/thememoodin.Tpo" \
  -c -o thememoodin.lo `test -f 'thememoodin.cpp' || echo './'`thememoodin.cpp; \
then mv -f ".deps/thememoodin.Tpo" ".deps/thememoodin.Plo"; \
else rm -f ".deps/thememoodin.Tpo"; exit 1; \
fi
In file included from thememoodin.cpp:32:
thememoodin.h:20:25: themeengine.h: No such file or directory
thememoodin.h:21:24: objkstheme.h: No such file or directory
In file included from thememoodin.cpp:32:
thememoodin.h:34: error: parse error before `{' token
thememoodin.h:35: error: virtual outside class declaration
thememoodin.h:35: error: non-member function `const char* className()' cannot
   have `const' method qualifier
thememoodin.h:35: error: virtual outside class declaration
thememoodin.h:35: error: virtual outside class declaration
thememoodin.h:35: error: virtual outside class declaration
thememoodin.h:35: error: virtual outside class declaration
thememoodin.h: In function `QObject* qObject()':
thememoodin.h:35: error: invalid use of `this' in non-member function
thememoodin.h: At global scope:
thememoodin.h:35: error: parse error before `private'
thememoodin.h:68: error: parse error before `public'
thememoodin.h:72: error: parse error before `private'
thememoodin.h:126: error: parse error before `}' token
thememoodin.cpp:38: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.cpp: In constructor `ThemeMoodin::ThemeMoodin(QWidget*, const
   char*, const QStringList&)':
thememoodin.cpp:38: error: class `ThemeMoodin' does not have any field named `
   ThemeEngine'
thememoodin.cpp: At global scope:
thememoodin.cpp:46: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.cpp: In member function `void ThemeMoodin::readSettings()':
thememoodin.cpp:47: error: `mTheme' undeclared (first use this function)
thememoodin.cpp:47: error: (Each undeclared identifier is reported only once
   for each function it appears in.)
thememoodin.cpp:78: error: `mUseIconSet' undeclared (first use this function)
thememoodin.cpp: At global scope:
thememoodin.cpp:113: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.cpp: In member function `void ThemeMoodin::init()':
thememoodin.cpp:114: error: `NoBackground' undeclared (first use this function)
thememoodin.cpp:114: error: `setBackgroundMode' undeclared (first use this
   function)
thememoodin.cpp:115: error: `setFixedSize' undeclared (first use this function)
thememoodin.cpp:117: error: no matching function for call to `QWidget::QWidget(
   ThemeMoodin* const)'
/usr/share/qt3/include/qwidget.h:696: error: candidates are:
   QWidget::QWidget(const QWidget&)
/usr/share/qt3/include/qwidget.h:135: error:
   QWidget::QWidget(QWidget*, const char*, unsigned int)
thememoodin.cpp:118: error: `size' undeclared (first use this function)
thememoodin.cpp:133: error: `move' undeclared (first use this function)
thememoodin.cpp: At global scope:
thememoodin.cpp:138: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.cpp: In member function `void
   ThemeMoodin::initBackground(QPainter*)':
thememoodin.cpp:160: error: `width' undeclared (first use this function)
thememoodin.cpp:160: error: `height' undeclared (first use this function)
thememoodin.cpp:167: error: no matching function for call to `KMessageBox::
   error(ThemeMoodin* const, QString)'
/usr/include/kde/kmessagebox.h:604: error: candidates are: static void
   KMessageBox::error(QWidget*, const QString&, const QString&, int)
thememoodin.cpp: At global scope:
thememoodin.cpp:178: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.cpp:213: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.cpp:261: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.cpp:304: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.cpp:321: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.cpp:333: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.cpp: In member function `void ThemeMoodin::slotSetPixmap(const
   QString&)':
thememoodin.cpp:349: error: `repaint' undeclared (first use this function)
thememoodin.cpp: At global scope:
thememoodin.cpp:354: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.cpp:380: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
In file included from thememoodin.cpp:389:
thememoodin.moc:23: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.moc:27: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.moc:27: error: assignment (not initialization) in declaration
thememoodin.moc:28: error: incomplete type `ThemeMoodin' does not have member `
   staticMetaObject'
thememoodin.moc:32: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.moc:40: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.moc:51: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.moc: In member function `QMetaObject*
   ThemeMoodin::staticMetaObject()':
thememoodin.moc:52: error: `metaObj' undeclared (first use this function)
thememoodin.moc:54: error: `ThemeEngine' undeclared (first use this function)
thememoodin.moc:54: error: parse error before `::' token
thememoodin.moc: At global scope:
thememoodin.moc:81: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.moc: In member function `void* ThemeMoodin::qt_cast(const char*)':
thememoodin.moc:84: error: parse error before `::' token
thememoodin.moc: At global scope:
thememoodin.moc:88: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.moc: In member function `bool ThemeMoodin::qt_invoke(int,
   QUObject*)':
thememoodin.moc:90: error: `slotSetText' undeclared (first use this function)
thememoodin.moc:93: error: parse error before `::' token
thememoodin.moc: At global scope:
thememoodin.moc:99: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.moc: In member function `bool ThemeMoodin::qt_emit(int, QUObject*)
   ':
thememoodin.moc:100: error: parse error before `::' token
thememoodin.moc:99: warning: unused parameter `int _id'
thememoodin.moc:99: warning: unused parameter `QUObject*_o'
thememoodin.moc: At global scope:
thememoodin.moc:105: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.moc: In member function `bool ThemeMoodin::qt_property(int, int,
   QVariant*)':
thememoodin.moc:106: error: parse error before `::' token
thememoodin.moc:105: warning: unused parameter `int id'
thememoodin.moc:105: warning: unused parameter `int f'
thememoodin.moc:105: warning: unused parameter `QVariant*v'
thememoodin.moc: At global scope:
thememoodin.moc:109: error: invalid use of undefined type `class ThemeMoodin'
thememoodin.h:33: error: forward declaration of `class ThemeMoodin'
thememoodin.h:35: warning: `bool qt_static_property(QObject*, int, int,
   QVariant*)' declared `static' but never defined
thememoodin.h:35: warning: `QMetaObject* staticMetaObject()' declared `static'
   but never defined
thememoodin.h:35: warning: `QString tr(const char*, const char*)' declared
   `static' but never defined
thememoodin.h:35: warning: `QString trUtf8(const char*, const char*)' declared
   `static' but never defined
thememoodin.h:44: warning: `QStringList names()' defined but not used
make[2]: *** [thememoodin.lo] Error 1
make[2]: Leaving directory `/home/patrick/moodin/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/patrick/moodin'
make: *** [all] Error 2
``` 


I am trying to compile the ksplash-engine-moodin_0.4.2.tar.gz version I downloaded from kde-look.

Anyone can help me to get it working ?

---

### Post by dakilla on 2005-09-21
Thanks for the help with qt!!!
you guys are the best!

and now!! I am stuck at this..



> make[2]: Leaving directory `/home/dakilla/src'
make[1]: *** [all-recursive] error 1
make[1]: Leaving directory `/home/dakilla'
make: *** [all] error 2 

I just wrote "make"..

---

### Post by dakilla on 2005-09-21
Thanks for the help with qt!!!
you guys are the best!

and now!! I am stuck again  ](*,)  

same as patpicos..

> make[2]: Leaving directory `/home/dakilla/src'
make[1]: *** [all-recursive] error 1
make[1]: Leaving directory `/home/dakilla'
make: *** [all] error 2 

I just wrote "make"..

---

### Post by johnniecarcinogen on 2005-10-11
[QUOTE=dakilla]Thanks for the help with qt!!!
you guys are the best!

and now!! I am stuck again  ](*,)  

same as patpicos..

 

I just wrote "make"..[/QUOTE]

Same here. Everything is fine until i sudo make install.

patpicos or dakilla ever get this working?

---

### Post by johnniecarcinogen on 2005-10-11
I came back to this after posting and tried to compile and it mysteriously worked this time.

EDIT: It may have been because I used apt-get to install the 'automake' package and then rebooted before trying again.

---

### Post by Inspector Hector on 2005-11-09
Could someone post the source code of 0.4.2?
The link on kde-look is broken for over a week now.

---

### Post by feeling on 2005-12-08
i've build a deb for this package :
[http://www.cabestan.be/ksplash-engine-moodin_0.1-1_i386.deb](http://www.cabestan.be/ksplash-engine-moodin_0.1-1_i386.deb)

compiled for the kde 3.5

cheers.
laurent.

---

### Post by Vampis on 2006-01-31
THANK YOU! :D :D :D 

I've been sitting all day trying to compile it. When I finally made it through ./configure (with help of auto-apt) it failed in make :(

I'll try this first thing In the morning :D

EDIT: Sorry for the bumb, Just now i saw this one was VERY old

---

