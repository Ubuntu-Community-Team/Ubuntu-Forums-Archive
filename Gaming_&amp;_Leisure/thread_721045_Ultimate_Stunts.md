---
title: "Ultimate Stunts"
date: 2008-03-10
forum: Gaming &amp; Leisure
---

### Post by oak_one on 2008-03-10
i downloaded it but have no idea how to install properly?

i went into the directory and typed ./configure then make

but i cant seem to see it

---

### Post by Perfect Storm on 2008-03-11
You might have downloaded the wrong file.

[http://ultimatestunts.nl/documentation/en/compile.htm](http://ultimatestunts.nl/documentation/en/compile.htm)

```
cd ~/Desktop
wget http://prdownloads.sourceforge.net/ultimatestunts/ultimatestunts-srcdata-0741.tar.gz?download
tar zxfv ultimatestunts-srcdata-0741.tar.gz
cd ultimatestunts-srcdata-0741
./configure
make
sudo checkinstall
ustunts
```

---

### Post by Teddy Picker on 2008-03-18
I tried the commands you just gave, but when i got to "sudo checkinstall" it did nothing and said that it was not a command

---

### Post by Perfect Storm on 2008-03-18
Install checkinstall - then do it again.

---

### Post by compiledkernel on 2008-03-18
sudo apt-get install checkinstall, 

dont you mean AI. :)

---

### Post by Perfect Storm on 2008-03-18
Aye, I would prefer aptitude...well each to his own I guess ;)

---

### Post by seaking69 on 2008-10-09
when running ./configure i get:

    checking for g++... no
    checking for c++... no
    checking for gpp... gpp
    checking whether we are using the GNU C++ compiler... no
    checking whether gpp accepts -g... no
    checking dependency style of gpp... none
    checking how to run the C++ preprocessor... /lib/cpp
    configure: error: C++ preprocessor "/lib/cpp" fails sanity check
    See `config.log' for more details.

I've installed the gpp and cpp... config.log id very long and also mention something like that

please help :confused:

---

### Post by Perfect Storm on 2008-10-09
> **seaking69 said:**
> when running ./configure i get:

    checking for g++... no
    checking for c++... no
    checking for gpp... gpp
    checking whether we are using the GNU C++ compiler... no
    checking whether gpp accepts -g... no
    checking dependency style of gpp... none
    checking how to run the C++ preprocessor... /lib/cpp
    configure: error: C++ preprocessor "/lib/cpp" fails sanity check
    See `config.log' for more details.

I've installed the gpp and cpp... config.log id very long and also mention something like that

please help :confused:

```
sudo apt-get install build-essential
```
This will get you the default compiling tool.

---

### Post by ondmis on 2008-11-23
```
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for egrep... grep -E
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
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking for glNewList in -lGL... yes
checking for gluLookAt in -lGLU... yes
checking for sdl-config... no
checking for SDL - version >= 1.1.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
checking SDL_image.h usability... no
checking SDL_image.h presence... no
checking for SDL_image.h... no
checking for IMG_Load in -lSDL_image... no
checking for socket in -lsocket... no
checking for gethostbyname in -lnsl... yes
checking for inet_aton in -lresolv... yes
checking for ANSI C header files... (cached) yes
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking for GL/glext.h... yes
checking AL/al.h usability... no
checking AL/al.h presence... no
checking for AL/al.h... no
checking AL/alut.h usability... no
checking AL/alut.h presence... no
checking for AL/alut.h... no
checking for alGetError in -lopenal... no
checking fmod/fmod.h usability... no
checking fmod/fmod.h presence... no
checking for fmod/fmod.h... no
checking for FSOUND_Close in -lfmod... no
checking whether gcc accepts -finput-charset and -fexec-charset... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking whether we are using the GNU C Library 2 or newer... yes
checking for library containing strerror... none required
checking for an ANSI C-conforming const... yes
checking for signed... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for long long... yes
checking for long double... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for stdint.h... (cached) yes
checking for SIZE_MAX... 4294967295U
checking for stdint.h... (cached) yes
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/bash: ./config.rpath: No such file or directory
done
checking for ptrdiff_t... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for asprintf... yes
checking for fwprintf... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for snprintf... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for wcslen... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... yes
checking whether getc_unlocked is declared... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking for CFPreferencesCopyAppValue... (cached) no
checking for CFLocaleCopyCurrent... (cached) no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
configure: creating ./config.status
config.status: creating ultimatestunts.conf
config.status: creating Makefile
config.status: creating intl/Makefile
config.status: creating po/Makefile.in
config.status: creating data/Makefile
config.status: creating shared/Makefile
config.status: creating simulation/Makefile
config.status: creating graphics/Makefile
config.status: creating stuntsserver/Makefile
config.status: creating stuntsai/Makefile
config.status: creating stunts3dedit/Makefile
config.status: creating trackedit/Makefile
config.status: creating ultimatestunts/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile

Some important results:
Network libraries: "-lresolv -lnsl "
Sound libraries: ""
Graphics libraries: "-lGLU -lGL "
SDL libraries: ""
Prefix dir: "/usr/local"
usdatadir: "/usr/local/share/ultimatestunts/"

WARNING: No appropriate sound libraries found.
  You can still compile Ultimate Stunts, but
  sound will not be available

WARNING: SDL library not found
  You may still be able to compile the non-graphical programs,
  but that is not guaranteed

WARNING: SDL_image library not found
  It is still perfectly possible to compile Ultimate Stunts,
  but it won't be able to load all image formats.
  This is no problem for the non-graphical programs,
  but the graphical programs will not work with all
  the default texture files. Only .rgb and .rgba are
  supported withoud SDL_image.

bjarke@bjarke-desktop:~/ultimatestunts-srcdata-0741$ make
make  all-recursive
make[1]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741'
Making all in intl
make[2]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/intl'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/intl'
Making all in po
make[2]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/po'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/po'
Making all in data
make[2]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/data'
make[2]: Ingenting at gøre for 'all'.
make[2]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/data'
Making all in shared
make[2]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/shared'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../intl     -finput-charset=ISO-8859-1 -fexec-charset=ISO-8859-1 -Wall -g -O2  -MT binbuffer.o -MD -MP -MF ".deps/binbuffer.Tpo" -c -o binbuffer.o binbuffer.cpp; \
	then mv -f ".deps/binbuffer.Tpo" ".deps/binbuffer.Po"; else rm -f ".deps/binbuffer.Tpo"; exit 1; fi
I filen inkluderet af binbuffer.h:25,
                   af binbuffer.cpp:19:
usmacros.h:30:24: error: SDL_endian.h: No such file or directory
usmacros.h:31:17: error: SDL.h: No such file or directory
In file included from binbuffer.cpp:19:
binbuffer.h:32: fejl: ‘Uint8’ was not declared in this scope
binbuffer.h:32: fejl: skabelonsparameter 1 er ugyldig
binbuffer.h:32: fejl: skabelonsparameter 2 er ugyldig
binbuffer.h:45: fejl: expected ‘,’ or ‘...’ before ‘&’ token
binbuffer.h:45: fejl: ISO C++ forbids declaration of ‘Uint8’ with no type
binbuffer.h:46: fejl: expected ‘,’ or ‘...’ before ‘&’ token
binbuffer.h:46: fejl: ISO C++ forbids declaration of ‘Uint16’ with no type
binbuffer.h:46: fejl: ‘CBinBuffer& CBinBuffer::operator+=(int)’ cannot be overloaded
binbuffer.h:45: fejl: with ‘CBinBuffer& CBinBuffer::operator+=(int)’
binbuffer.h:47: fejl: expected ‘,’ or ‘...’ before ‘&’ token
binbuffer.h:47: fejl: ISO C++ forbids declaration of ‘Uint32’ with no type
binbuffer.h:47: fejl: ‘CBinBuffer& CBinBuffer::operator+=(int)’ cannot be overloaded
binbuffer.h:45: fejl: with ‘CBinBuffer& CBinBuffer::operator+=(int)’
binbuffer.h:59: fejl: ‘Uint8’ does not name a type
binbuffer.h:60: fejl: ‘Uint16’ does not name a type
binbuffer.h:61: fejl: ‘Uint32’ does not name a type
binbuffer.cpp: In member function ‘CBinBuffer& CBinBuffer::operator+=(const unsigned char*)’:
binbuffer.cpp:32: fejl: ‘class CBinBuffer’ has no member named ‘push_back’
binbuffer.cpp:32: fejl: ‘Uint8’ was not declared in this scope
binbuffer.cpp: In member function ‘CBinBuffer& CBinBuffer::operator=(const unsigned char*)’:
binbuffer.cpp:37: fejl: ‘class CBinBuffer’ has no member named ‘empty’
binbuffer.cpp: In member function ‘CBinBuffer& CBinBuffer::operator+=(const CBinBuffer&)’:
binbuffer.cpp:43: fejl: ‘const class CBinBuffer’ has no member named ‘size’
binbuffer.cpp:43: fejl: ‘class CBinBuffer’ has no member named ‘push_back’
binbuffer.cpp:43: fejl: no match for ‘operator[]’ in ‘bb[i]’
binbuffer.cpp: In member function ‘CBinBuffer CBinBuffer::getBuffer(unsigned int&, unsigned int) const’:
binbuffer.cpp:49: fejl: ‘size’ was not declared in this scope
binbuffer.cpp:55: fejl: ‘class CBinBuffer’ has no member named ‘resize’
binbuffer.cpp:58: fejl: no match for ‘operator[]’ in ‘ret[i]’
binbuffer.cpp:58: fejl: no match for ‘operator[]’ in ‘*(const CBinBuffer*)this[pos]’
binbuffer.cpp: At global scope:
binbuffer.cpp:66: fejl: expected ‘,’ or ‘...’ before ‘&’ token
binbuffer.cpp:66: fejl: ISO C++ forbids declaration of ‘Uint8’ with no type
binbuffer.cpp: In member function ‘CBinBuffer& CBinBuffer::operator+=(int)’:
binbuffer.cpp:68: fejl: ‘class CBinBuffer’ has no member named ‘push_back’
binbuffer.cpp:68: fejl: ‘i’ was not declared in this scope
binbuffer.cpp: At global scope:
binbuffer.cpp:72: fejl: ‘Uint8’ does not name a type
binbuffer.cpp:81: fejl: expected ‘,’ or ‘...’ before ‘&’ token
binbuffer.cpp:81: fejl: ISO C++ forbids declaration of ‘Uint16’ with no type
binbuffer.cpp:81: fejl: redefinition of ‘CBinBuffer& CBinBuffer::operator+=(int)’
binbuffer.cpp:66: fejl: ‘CBinBuffer& CBinBuffer::operator+=(int)’ previously defined here
binbuffer.cpp: In member function ‘CBinBuffer& CBinBuffer::operator+=(int)’:
binbuffer.cpp:83: fejl: ‘Uint16’ was not declared in this scope
binbuffer.cpp:83: fejl: ‘i’ was not declared in this scope
binbuffer.cpp:83: fejl: ‘Uint8’ cannot be used as a function
binbuffer.cpp:84: fejl: ‘Uint8’ cannot be used as a function
binbuffer.cpp: At global scope:
binbuffer.cpp:88: fejl: ‘Uint16’ does not name a type
binbuffer.cpp:96: fejl: expected ‘,’ or ‘...’ before ‘&’ token
binbuffer.cpp:96: fejl: ISO C++ forbids declaration of ‘Uint32’ with no type
binbuffer.cpp:96: fejl: redefinition of ‘CBinBuffer& CBinBuffer::operator+=(int)’
binbuffer.cpp:66: fejl: ‘CBinBuffer& CBinBuffer::operator+=(int)’ previously defined here
binbuffer.cpp: In member function ‘CBinBuffer& CBinBuffer::operator+=(int)’:
binbuffer.cpp:98: fejl: ‘i’ was not declared in this scope
binbuffer.cpp:98: fejl: ‘Uint8’ cannot be used as a function
binbuffer.cpp:99: fejl: ‘Uint8’ cannot be used as a function
binbuffer.cpp:100: fejl: ‘Uint8’ cannot be used as a function
binbuffer.cpp:101: fejl: ‘Uint8’ cannot be used as a function
binbuffer.cpp: At global scope:
binbuffer.cpp:105: fejl: ‘Uint32’ does not name a type
binbuffer.cpp: In member function ‘CBinBuffer& CBinBuffer::operator+=(const CString&)’:
binbuffer.cpp:117: fejl: ‘Uint8’ was not declared in this scope
binbuffer.cpp:119: fejl: expected `)' before ‘bs’
binbuffer.cpp: In member function ‘CString CBinBuffer::getCString(unsigned int&) const’:
binbuffer.cpp:127: fejl: ‘const class CBinBuffer’ has no member named ‘size’
binbuffer.cpp:128: fejl: ‘Uint8’ was not declared in this scope
binbuffer.cpp:128: fejl: expected `;' before ‘ssize’
binbuffer.cpp:129: fejl: ‘ssize’ was not declared in this scope
binbuffer.cpp:129: fejl: ‘const class CBinBuffer’ has no member named ‘size’
binbuffer.cpp:130: fejl: ‘ssize’ was not declared in this scope
binbuffer.cpp:132: fejl: ‘getUint8’ was not declared in this scope
binbuffer.cpp: In member function ‘CBinBuffer& CBinBuffer::addFloat8(const float&, float)’:
binbuffer.cpp:143: fejl: ‘Uint8’ was not declared in this scope
binbuffer.cpp: In member function ‘float CBinBuffer::getFloat8(unsigned int&, float) const’:
binbuffer.cpp:148: fejl: ‘getUint8’ was not declared in this scope
binbuffer.cpp: In member function ‘CBinBuffer& CBinBuffer::addFloat16(const float&, float)’:
binbuffer.cpp:153: fejl: ‘Uint16’ was not declared in this scope
binbuffer.cpp: In member function ‘float CBinBuffer::getFloat16(unsigned int&, float) const’:
binbuffer.cpp:158: fejl: ‘getUint16’ was not declared in this scope
binbuffer.cpp: In member function ‘CBinBuffer& CBinBuffer::addFloat32(const float&, float)’:
binbuffer.cpp:164: fejl: ‘Uint32’ was not declared in this scope
binbuffer.cpp: In member function ‘float CBinBuffer::getFloat32(unsigned int&, float) const’:
binbuffer.cpp:170: fejl: ‘getUint32’ was not declared in this scope
binbuffer.cpp: In member function ‘CString CBinBuffer::dump() const’:
binbuffer.cpp:264: fejl: ‘const class CBinBuffer’ has no member named ‘size’
binbuffer.cpp:265: fejl: no match for ‘operator[]’ in ‘*(const CBinBuffer*)this[i]’
binbuffer.cpp:271: fejl: ‘Uint8’ was not declared in this scope
binbuffer.cpp:273: fejl: ‘Uint8’ was not declared in this scope
binbuffer.cpp: In member function ‘CBinBuffer CBinBuffer::substr(unsigned int, int) const’:
binbuffer.cpp:282: fejl: ‘size’ was not declared in this scope
binbuffer.cpp:287: fejl: ‘class CBinBuffer’ has no member named ‘push_back’
binbuffer.cpp:287: fejl: no match for ‘operator[]’ in ‘*(const CBinBuffer*)this[i]’
make[2]: *** [binbuffer.o] Fejl 1
make[2]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/shared'
make[1]: *** [all-recursive] Fejl 1
make[1]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741'
make: *** [all] Fejl 2
bjarke@bjarke-desktop:~/ultimatestunts-srcdata-0741$ sudo checkinstall
[sudo] password for bjarke: 

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@bjarke-desktop ]
1 -  Summary: [ ustunts ]
2 -  Name:    [ ultimatestunts-srcdata ]
3 -  Version: [ 0741 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ultimatestunts-srcdata-0741 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in intl
make[1]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/intl'
if test "ultimatestunts" = "gettext" \
	   && test '' = 'intl-compat.o'; then \
	  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/lib /usr/local/include; \
	  /usr/bin/install -c -m 644 libintl.h /usr/local/include/libintl.h; \
	  @LIBTOOL@ --mode=install \
	    /usr/bin/install -c -m 644 libintl.a /usr/local/lib/libintl.a; \
	else \
	  : ; \
	fi
if test 'no' = yes; then \
	  test yes != no || /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/lib; \
	  temp=/usr/local/lib/t-charset.alias; \
	  dest=/usr/local/lib/charset.alias; \
	  if test -f /usr/local/lib/charset.alias; then \
	    orig=/usr/local/lib/charset.alias; \
	    sed -f ref-add.sed $orig > $temp; \
	    /usr/bin/install -c -m 644 $temp $dest; \
	    rm -f $temp; \
	  else \
	    if test yes = no; then \
	      orig=charset.alias; \
	      sed -f ref-add.sed $orig > $temp; \
	      /usr/bin/install -c -m 644 $temp $dest; \
	      rm -f $temp; \
	    fi; \
	  fi; \
	  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/share/locale; \
	  test -f /usr/local/share/locale/locale.alias \
	    && orig=/usr/local/share/locale/locale.alias \
	    || orig=./locale.alias; \
	  temp=/usr/local/share/locale/t-locale.alias; \
	  dest=/usr/local/share/locale/locale.alias; \
	  sed -f ref-add.sed $orig > $temp; \
	  /usr/bin/install -c -m 644 $temp $dest; \
	  rm -f $temp; \
	else \
	  : ; \
	fi
if test "ultimatestunts" = "gettext"; then \
	  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/share/gettext/intl; \
	  /usr/bin/install -c -m 644 VERSION /usr/local/share/gettext/intl/VERSION; \
	  /usr/bin/install -c -m 644 ChangeLog.inst /usr/local/share/gettext/intl/ChangeLog; \
	  dists="COPYING.LIB-2.0 COPYING.LIB-2.1 Makefile.in config.charset locale.alias ref-add.sin ref-del.sin gmo.h gettextP.h hash-string.h plural-exp.h eval-plural.h os2compat.h libgnuintl.h loadinfo.h bindtextdom.c dcgettext.c dgettext.c gettext.c finddomain.c loadmsgcat.c localealias.c textdomain.c l10nflist.c explodename.c dcigettext.c dcngettext.c dngettext.c ngettext.c plural.y plural-exp.c localcharset.c localename.c osdep.c os2compat.c intl-compat.c"; \
	  for file in $dists; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/local/share/gettext/intl/$file; \
	  done; \
	  chmod a+x /usr/local/share/gettext/intl/config.charset; \
	  dists="plural.c"; \
	  for file in $dists; do \
	    if test -f $file; then dir=.; else dir=.; fi; \
	    /usr/bin/install -c -m 644 $dir/$file \
			    /usr/local/share/gettext/intl/$file; \
	  done; \
	  dists="xopen-msg.sed linux-msg.sed po2tbl.sed.in cat-compat.c COPYING.LIB-2 gettext.h libgettext.h plural-eval.c"; \
	  for file in $dists; do \
	    rm -f /usr/local/share/gettext/intl/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/intl'
Making install in po
make[1]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/po'
.././mkinstalldirs /usr/local/share
installing de.gmo as ../data/lang/de/LC_MESSAGES/ultimatestunts.mo
installing fr_FR.gmo as ../data/lang/fr_FR/LC_MESSAGES/ultimatestunts.mo
installing hu.gmo as ../data/lang/hu/LC_MESSAGES/ultimatestunts.mo
installing nl.gmo as ../data/lang/nl/LC_MESSAGES/ultimatestunts.mo
installing pt_BR.gmo as ../data/lang/pt_BR/LC_MESSAGES/ultimatestunts.mo
if test "ultimatestunts" = "gettext"; then \
	  .././mkinstalldirs /usr/local/share/gettext/po; \
	  for file in Makefile.in.in Makevars remove-potcdate.sin   ; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/local/share/gettext/po/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/po'
Making install in data
make[1]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/data'
/bin/bash ../mkinstalldirs /usr/local/share/ultimatestunts/
mkdir -p -- /usr/local/share/ultimatestunts/
cp -r cars environment lang misc music textures textures.dat tiles tracks /usr/local/share/ultimatestunts/
chmod 644 /usr/local/share/ultimatestunts//*.*
chmod: ændrer rettigheder på '/usr/local/share/ultimatestunts//textures.dat': No such file or directory
make[1]: *** [install] Fejl 1
make[1]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/data'
make: *** [install-recursive] Fejl 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

bjarke@bjarke-desktop:~/ultimatestunts-srcdata-0741$ 

```

Someone who can tell me what i'm doing wrong?:confused:

---

### Post by Perfect Storm on 2008-11-23
Try this: [http://gaming.gwos.org/doku.php/guides:64bit:ultimate_stunts](http://gaming.gwos.org/doku.php/guides:64bit:ultimate_stunts)
Though I havn't tested it since 7.10

---

### Post by ondmis on 2008-11-24
```
bjarke@bjarke-desktop:~/ultimatestunts-srcdata-0741$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@bjarke-desktop ]
1 -  Summary: [ ustunts ]
2 -  Name:    [ ultimatestunts-srcdata ]
3 -  Version: [ 0741 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ultimatestunts-srcdata-0741 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 
```

what am i going to do now?:-?

---

### Post by Perfect Storm on 2008-11-24
<enter>

---

### Post by ondmis on 2008-11-25
then it says:
```
bjarke@bjarke-desktop:~/ultimatestunts-srcdata-0741$ sudo checkinstall
[sudo] password for bjarke: 

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@bjarke-desktop ]
1 -  Summary: [ ustunts ]
2 -  Name:    [ ultimatestunts-srcdata ]
3 -  Version: [ 0741 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ultimatestunts-srcdata-0741 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in intl
make[1]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/intl'
if test "ultimatestunts" = "gettext" \
	   && test '' = 'intl-compat.o'; then \
	  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/lib /usr/local/include; \
	  /usr/bin/install -c -m 644 libintl.h /usr/local/include/libintl.h; \
	  @LIBTOOL@ --mode=install \
	    /usr/bin/install -c -m 644 libintl.a /usr/local/lib/libintl.a; \
	else \
	  : ; \
	fi
if test 'no' = yes; then \
	  test yes != no || /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/lib; \
	  temp=/usr/local/lib/t-charset.alias; \
	  dest=/usr/local/lib/charset.alias; \
	  if test -f /usr/local/lib/charset.alias; then \
	    orig=/usr/local/lib/charset.alias; \
	    sed -f ref-add.sed $orig > $temp; \
	    /usr/bin/install -c -m 644 $temp $dest; \
	    rm -f $temp; \
	  else \
	    if test yes = no; then \
	      orig=charset.alias; \
	      sed -f ref-add.sed $orig > $temp; \
	      /usr/bin/install -c -m 644 $temp $dest; \
	      rm -f $temp; \
	    fi; \
	  fi; \
	  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/share/locale; \
	  test -f /usr/local/share/locale/locale.alias \
	    && orig=/usr/local/share/locale/locale.alias \
	    || orig=./locale.alias; \
	  temp=/usr/local/share/locale/t-locale.alias; \
	  dest=/usr/local/share/locale/locale.alias; \
	  sed -f ref-add.sed $orig > $temp; \
	  /usr/bin/install -c -m 644 $temp $dest; \
	  rm -f $temp; \
	else \
	  : ; \
	fi
if test "ultimatestunts" = "gettext"; then \
	  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/share/gettext/intl; \
	  /usr/bin/install -c -m 644 VERSION /usr/local/share/gettext/intl/VERSION; \
	  /usr/bin/install -c -m 644 ChangeLog.inst /usr/local/share/gettext/intl/ChangeLog; \
	  dists="COPYING.LIB-2.0 COPYING.LIB-2.1 Makefile.in config.charset locale.alias ref-add.sin ref-del.sin gmo.h gettextP.h hash-string.h plural-exp.h eval-plural.h os2compat.h libgnuintl.h loadinfo.h bindtextdom.c dcgettext.c dgettext.c gettext.c finddomain.c loadmsgcat.c localealias.c textdomain.c l10nflist.c explodename.c dcigettext.c dcngettext.c dngettext.c ngettext.c plural.y plural-exp.c localcharset.c localename.c osdep.c os2compat.c intl-compat.c"; \
	  for file in $dists; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/local/share/gettext/intl/$file; \
	  done; \
	  chmod a+x /usr/local/share/gettext/intl/config.charset; \
	  dists="plural.c"; \
	  for file in $dists; do \
	    if test -f $file; then dir=.; else dir=.; fi; \
	    /usr/bin/install -c -m 644 $dir/$file \
			    /usr/local/share/gettext/intl/$file; \
	  done; \
	  dists="xopen-msg.sed linux-msg.sed po2tbl.sed.in cat-compat.c COPYING.LIB-2 gettext.h libgettext.h plural-eval.c"; \
	  for file in $dists; do \
	    rm -f /usr/local/share/gettext/intl/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/intl'
Making install in po
make[1]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/po'
.././mkinstalldirs /usr/local/share
installing de.gmo as ../data/lang/de/LC_MESSAGES/ultimatestunts.mo
installing fr_FR.gmo as ../data/lang/fr_FR/LC_MESSAGES/ultimatestunts.mo
installing hu.gmo as ../data/lang/hu/LC_MESSAGES/ultimatestunts.mo
installing nl.gmo as ../data/lang/nl/LC_MESSAGES/ultimatestunts.mo
installing pt_BR.gmo as ../data/lang/pt_BR/LC_MESSAGES/ultimatestunts.mo
if test "ultimatestunts" = "gettext"; then \
	  .././mkinstalldirs /usr/local/share/gettext/po; \
	  for file in Makefile.in.in Makevars remove-potcdate.sin   ; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/local/share/gettext/po/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/po'
Making install in data
make[1]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/data'
/bin/bash ../mkinstalldirs /usr/local/share/ultimatestunts/
mkdir -p -- /usr/local/share/ultimatestunts/
cp -r cars environment lang misc music textures textures.dat tiles tracks /usr/local/share/ultimatestunts/
cp: kan ikke udføre stat() '/usr/local/share/ultimatestunts/cars': Not a directory
cp: kan ikke udføre stat() '/usr/local/share/ultimatestunts/environment': Not a directory
cp: kan ikke udføre stat() '/usr/local/share/ultimatestunts/lang': Not a directory
cp: kan ikke udføre stat() '/usr/local/share/ultimatestunts/misc': Not a directory
cp: kan ikke udføre stat() '/usr/local/share/ultimatestunts/music': Not a directory
cp: kan ikke udføre stat() '/usr/local/share/ultimatestunts/textures': Not a directory
cp: kan ikke udføre stat() '/usr/local/share/ultimatestunts/textures.dat': Not a directory
cp: kan ikke udføre stat() '/usr/local/share/ultimatestunts/tiles': Not a directory
cp: kan ikke udføre stat() '/usr/local/share/ultimatestunts/tracks': Not a directory
make[1]: *** [install] Fejl 1
make[1]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/data'
make: *** [install-recursive] Fejl 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

bjarke@bjarke-desktop:~/ultimatestunts-srcdata-0741$ 

```

:(

---

### Post by Perfect Storm on 2008-11-25
If sudo checkinstall fails, you can use;
sudo make install instead.

---

### Post by ondmis on 2008-11-25
aaaaaargh!
```
bjarke@bjarke-desktop:~/ultimatestunts-srcdata-0741$ sudo make install
[sudo] password for bjarke: 
Making install in intl
make[1]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/intl'
if test "ultimatestunts" = "gettext" \
	   && test '' = 'intl-compat.o'; then \
	  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/lib /usr/local/include; \
	  /usr/bin/install -c -m 644 libintl.h /usr/local/include/libintl.h; \
	  @LIBTOOL@ --mode=install \
	    /usr/bin/install -c -m 644 libintl.a /usr/local/lib/libintl.a; \
	else \
	  : ; \
	fi
if test 'no' = yes; then \
	  test yes != no || /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/lib; \
	  temp=/usr/local/lib/t-charset.alias; \
	  dest=/usr/local/lib/charset.alias; \
	  if test -f /usr/local/lib/charset.alias; then \
	    orig=/usr/local/lib/charset.alias; \
	    sed -f ref-add.sed $orig > $temp; \
	    /usr/bin/install -c -m 644 $temp $dest; \
	    rm -f $temp; \
	  else \
	    if test yes = no; then \
	      orig=charset.alias; \
	      sed -f ref-add.sed $orig > $temp; \
	      /usr/bin/install -c -m 644 $temp $dest; \
	      rm -f $temp; \
	    fi; \
	  fi; \
	  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/share/locale; \
	  test -f /usr/local/share/locale/locale.alias \
	    && orig=/usr/local/share/locale/locale.alias \
	    || orig=./locale.alias; \
	  temp=/usr/local/share/locale/t-locale.alias; \
	  dest=/usr/local/share/locale/locale.alias; \
	  sed -f ref-add.sed $orig > $temp; \
	  /usr/bin/install -c -m 644 $temp $dest; \
	  rm -f $temp; \
	else \
	  : ; \
	fi
if test "ultimatestunts" = "gettext"; then \
	  /bin/sh `case ".././mkinstalldirs" in /*) echo ".././mkinstalldirs" ;; *) echo "../.././mkinstalldirs" ;; esac` /usr/local/share/gettext/intl; \
	  /usr/bin/install -c -m 644 VERSION /usr/local/share/gettext/intl/VERSION; \
	  /usr/bin/install -c -m 644 ChangeLog.inst /usr/local/share/gettext/intl/ChangeLog; \
	  dists="COPYING.LIB-2.0 COPYING.LIB-2.1 Makefile.in config.charset locale.alias ref-add.sin ref-del.sin gmo.h gettextP.h hash-string.h plural-exp.h eval-plural.h os2compat.h libgnuintl.h loadinfo.h bindtextdom.c dcgettext.c dgettext.c gettext.c finddomain.c loadmsgcat.c localealias.c textdomain.c l10nflist.c explodename.c dcigettext.c dcngettext.c dngettext.c ngettext.c plural.y plural-exp.c localcharset.c localename.c osdep.c os2compat.c intl-compat.c"; \
	  for file in $dists; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/local/share/gettext/intl/$file; \
	  done; \
	  chmod a+x /usr/local/share/gettext/intl/config.charset; \
	  dists="plural.c"; \
	  for file in $dists; do \
	    if test -f $file; then dir=.; else dir=.; fi; \
	    /usr/bin/install -c -m 644 $dir/$file \
			    /usr/local/share/gettext/intl/$file; \
	  done; \
	  dists="xopen-msg.sed linux-msg.sed po2tbl.sed.in cat-compat.c COPYING.LIB-2 gettext.h libgettext.h plural-eval.c"; \
	  for file in $dists; do \
	    rm -f /usr/local/share/gettext/intl/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/intl'
Making install in po
make[1]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/po'
.././mkinstalldirs /usr/local/share
installing de.gmo as ../data/lang/de/LC_MESSAGES/ultimatestunts.mo
installing fr_FR.gmo as ../data/lang/fr_FR/LC_MESSAGES/ultimatestunts.mo
installing hu.gmo as ../data/lang/hu/LC_MESSAGES/ultimatestunts.mo
installing nl.gmo as ../data/lang/nl/LC_MESSAGES/ultimatestunts.mo
installing pt_BR.gmo as ../data/lang/pt_BR/LC_MESSAGES/ultimatestunts.mo
if test "ultimatestunts" = "gettext"; then \
	  .././mkinstalldirs /usr/local/share/gettext/po; \
	  for file in Makefile.in.in Makevars remove-potcdate.sin   ; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/local/share/gettext/po/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/po'
Making install in data
make[1]: Går til katalog '/home/bjarke/ultimatestunts-srcdata-0741/data'
/bin/bash ../mkinstalldirs /usr/local/share/ultimatestunts/
mkdir -p -- /usr/local/share/ultimatestunts/
mkdir: kan ikke oprette katalog '/usr/local/share/ultimatestunts/': File exists
make[1]: *** [install] Fejl 1
make[1]: Forlader katalog '/home/bjarke/ultimatestunts-srcdata-0741/data'
make: *** [install-recursive] Fejl 1

```

---

### Post by Perfect Storm on 2008-11-25
> mkdir -p -- /usr/local/share/ultimatestunts/
mkdir: kan ikke oprette katalog '/usr/local/share/ultimatestunts/': File exists

Do you have an older version of Ultimate stunts installed?


```
ls -a /usr/local/share/ultimatestunts
```

---

### Post by andrew.46 on 2008-11-27
Hi,

Checkinstall may work for you if you pass the --fstrans=no option:

```
sudo checkinstall --fstrans=no
```

Some more details of this fix and an alternative change in /etc/chickinstallrc here:

[https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/78455](https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/78455)

  Andrew

---

### Post by go_beep_yourself on 2008-12-20
Did using --fstrans=no work for anybody? I tried a deb earlier from the playdeb or getdeb website, and there was a dependency that was no longer available from the repos.

---

### Post by go_beep_yourself on 2008-12-20
> **Artificial Intelligence said:**
> You might have downloaded the wrong file.

[http://ultimatestunts.nl/documentation/en/compile.htm](http://ultimatestunts.nl/documentation/en/compile.htm)

```
cd ~/Desktop
wget http://prdownloads.sourceforge.net/ultimatestunts/ultimatestunts-srcdata-0741.tar.gz?download
tar zxfv ultimatestunts-srcdata-0741.tar.gz
cd ultimatestunts-srcdata-0741
./configure
make
sudo checkinstall
ustunts
```

In that url, it says install libopenal0a before compiling, but it's not in the repos anymore. See???

[PHP]$ sudo apt-get install libopenal0a
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libopenal0a is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libopenal1
E: Package libopenal0a has no installation candidate
[/PHP]

Well I already had libopenal1 installed, and that didn't work with the deb even though I managed to get it installed with dpkg -i --force-depends. It's the wrong version, so it doesn't work.

---

### Post by Perfect Storm on 2008-12-20
That have been a problem with more than one game that Ubuntu 8.10 uses libopenal1 :-/


But did you also have libopenal1-dev installed?

---

### Post by Perfect Storm on 2008-12-20
ok, just updated my guide, should work (work for me); [http://gaming.gwos.org/doku.php/guides:64bit:ultimate_stunts](http://gaming.gwos.org/doku.php/guides:64bit:ultimate_stunts)

---

