---
title: "UFO: Alien Invasion map compilation error."
date: 2009-12-16
forum: Gaming &amp; Leisure
---

### Post by sparky8251 on 2009-12-16
My OS is Ubuntu 9.10 1386.

When ever I try to compile ufoai following the instructions at this site:

http://ufoai.ninex.info/wiki/index.php/Debian

This is what happens as I try to compile:

name@family-computer:~$ cd ufoai
name@family-computer:~/ufoai$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking system... UNIX (GNU/Linux)
checking for sed... yes
checking for echo... yes
checking target OS... linux-gnu
checking target CPU... i386
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking for int*... yes
checking size of int*... 4
checking for rm... yes
checking for mkdir... yes
checking for getaddrinfo... yes
checking for freeaddrinfo... yes
checking whether AI_NUMERICSERV is declared... yes
checking for stdint.h... (cached) yes
checking for library containing dlopen... -ldl
checking for library containing cos... -lm
checking for library containing stricmp... no
checking for library containing strcasecmp... none required
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for compress in -lz... yes
checking curl/curl.h usability... yes
checking curl/curl.h presence... yes
checking for curl/curl.h... yes
checking for curl_easy_init in -lcurl... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for jpeg_CreateDecompress in -ljpeg... yes

---

### Post by sparky8251 on 2009-12-16
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for library containing gettext... none required
checking for sdl-config... yes
checking SDL.h usability... yes
checking SDL.h presence... yes
checking for SDL.h... yes
checking SDL_mixer.h usability... yes
checking SDL_mixer.h presence... yes
checking for SDL_mixer.h... yes
checking for library containing Mix_OpenAudio... -lSDL_mixer
checking SDL_ttf.h usability... yes
checking SDL_ttf.h presence... yes
checking for SDL_ttf.h... yes
checking for library containing TTF_Init... -lSDL_ttf
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for png_create_info_struct in -lpng... yes
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking GL/glu.h usability... yes
checking GL/glu.h presence... yes
checking for GL/glu.h... yes
configure: Without shader support
checking for library containing newwin... -lcurses
configure: Enabling client
configure: Enabling dedicated server
configure: Enabling ufo2map
configure: Enabling debug build
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
name@family-computer:~/ufoai$ make deb
debuild binary
set -e; if [ -d .svn ]; then \
      SRCVER=2.2~~svn11980 ;\
      CURVER=`svn info|grep ^Revision:| cut -c11-` ;\
      if [ -n "$CURVER" ] ; then \
        sed 1s/$SRCVER/${SRCVER%svn*}svn$CURVER/ < debian/changelog > debian/cl2;\
        mv debian/cl2 debian/changelog ;\
      fi ;\
    fi
dh_testdir
/usr/bin/make BUILDDIR=/home/name/ufoai/BUILD lang maps
make[1]: Entering directory `/home/name/ufoai'
Making lang
cs.po
1997 translated messages, 9 fuzzy translations, 3 untranslated messages.
da.po
1988 translated messages, 17 fuzzy translations, 4 untranslated messages.
de.po
1956 translated messages, 30 fuzzy translations, 23 untranslated messages.
el.po
1988 translated messages, 17 fuzzy translations, 4 untranslated messages.
en.po
2009 translated messages.
es.po
772 translated messages, 657 fuzzy translations, 580 untranslated messages.
es_ES.po
925 translated messages, 60Proxy-Connection: keep-alive Cache-Control: max-age=0  fuzzy translations, 483 untranslated messages.
est.po
836 translated messages, 616 fuzzy translations, 557 untranslated messages.
fi.po
428 translated messages, 236 fuzzy translations, 1345 untranslated messages.
fr.po
2008 translated messages.
it.po
1276 translated messages, 411 fuzzy translations, 322 untranslated messages.
ja.po
960 translated messages, 31 fuzzy translations, 1018 untranslated messages.
pl.po
1620 translated messages, 130 fuzzy translations, 259 untranslated messages.
pt_BR.po
1776 translated messages, 259 untranslated messages.
ru.po
1278 translated messages, 416 fuzzy translations, 315 untranslated messages.
slo.po
497 translated messages, 719 fuzzy translations, 793 untranslated messages.
sv.po
1735 translated messages, 81 fuzzy translations, 193 untranslated messages.
th.po
1349 translated messages, 371 fuzzy translations, 289 untranslated messages.
 * [MAP] src/tools/ufo2map/ufo2map.c
 * [MAP] src/tools/ufo2map/qrad3.c
 * [MAP] src/tools/ufo2map/qbsp3.c
 * [MAP] src/tools/ufo2map/brushbsp.c
 * [MAP] src/tools/ufo2map/csg.c
 * [MAP] src/tools/ufo2map/faces.c
 * [MAP] src/tools/ufo2map/levels.c
 * [MAP] src/tools/ufo2map/lightmap.c
 * [MAP] src/tools/ufo2map/map.c
 * [MAP] src/tools/ufo2map/patches.c
src/tools/ufo2map/patches.c:323: warning: 'SubdividePatch' defined but not used
 * [MAP] src/tools/ufo2map/portals.c
 * [MAP] src/tools/ufo2map/routing.c
 * [MAP] src/tools/ufo2map/textures.c
 * [MAP] src/tools/ufo2map/tree.c
 * [MAP] src/tools/ufo2map/writebsp.c
 * [MAP] src/tools/ufo2map/common/bspfile.c
 * [MAP] src/tools/ufo2map/common/cmdlib.c
src/tools/ufo2map/common/cmdlib.c: In function 'Sys_FPrintf':
src/tools/ufo2map/common/cmdlib.c:544: warning: format not a string literal and no format arguments
src/tools/ufo2map/common/cmdlib.c: In function 'Com_Printf':
src/tools/ufo2map/common/cmdlib.c:559: warning: format not a string literal and no format arguments
 * [MAP] src/tools/ufo2map/common/mathlib.c
 * [MAP] src/tools/ufo2map/common/polylib.c
 * [MAP] src/tools/ufo2map/common/scriplib.c
 * [MAP] src/tools/ufo2map/common/trace.c
 * [MAP] src/tools/ufo2map/common/imagelib.c
 * [MAP] src/shared/byte.c
 * [MAP] src/shared/shared.c
 * [MAP] src/common/unzip.c
 * [MAP] src/common/ioapi.c
 * [MAP] ... linking  (-lm   -lz -ljpeg)
make[2]: Entering directory `/home/name/ufoai/base/maps'
make[2]: *** No rule to make target `all'.  Stop.
make[2]: Leaving directory `/home/name/ufoai/base/maps'
make[1]: *** [maps] Error 2
make[1]: Leaving directory `/home/name/ufoai'
make: *** [stamps/build-indep] Error 2
debuild: fatal error at line 1316:
couldn't exec fakeroot debian/rules: 
make: *** [deb] Error 2
name@family-computer:~/ufoai$ 

If anyone could help that would be great.

---

### Post by sparky8251 on 2009-12-18
bump

---

### Post by jpv2 on 2009-12-19
I compiled UFO already twice (latest versions from SVN) without problems, using this instruction

[http://ufoai.ninex.info/wiki/index.php/Debian](http://ufoai.ninex.info/wiki/index.php/Debian)  


however I did not use "make deb". What I did was

./configure
make
make lang (some errors popped out, but it did not affected the overall compilation)
make maps

Maps compilation was painfully sloooooooow. Wiki says it may last "even a couple of hours" - for me it was rather closer to "a dozen of hours". Fortunately you can break this maps compilation at any moment and then restart it by "make maps" and it will automatically skip all already-compiled-maps.

---

### Post by sparky8251 on 2009-12-21
Even if I use "make maps" it still gives me an error saying that "there is no rule to make "all"".

---

### Post by sparky8251 on 2009-12-23
bump

---

### Post by sparky8251 on 2009-12-29
bump

---

### Post by Perfect Storm on 2009-12-29
Tried this: [http://gwos.org/doku.php/guides:64bit:ufo_alien_invasion](http://gwos.org/doku.php/guides:64bit:ufo_alien_invasion)

---

### Post by sparky8251 on 2009-12-29
Thank you. Your HOWTO solved my problem.

---

