---
title: "Trouble Installing Torcs"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by navneeth on 2007-06-09
I've wasted time downloading around 70 MB, twice, only to get this error message.

```
E: /var/cache/apt/archives/plib1.8.4c2_1.8.4-6ubuntu1_i386.deb:
corrupted filesystem tarfile - corrupted package archive

```

Btw, the above error message showed up while I tried to install it from the termnial(apt-get). Similar errors showed up when I used Add/Remove... initially.

Please help. 

Oh, btw, does the game run well with a relatively old graphics card? S3 Pro Savage DDR (32MB, I think) and 786MB RAM, P4 1.7GHz.

---

### Post by Sockerdrickan on 2007-06-09
Try download source and compile it

Yeah the game will run on lower settings

---

### Post by navneeth on 2007-06-09
I'm trying to install plib from source, since that is the broken dependancy. When I configure, the last line says 
```
configure: error: could not find working GL library

```

So I installed FreeGlut, and did the configure again. It shows the same error. :(

---

### Post by navneeth on 2007-06-09
FREEGLUT

```
~/freeglut-2.4.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for an ANSI C-conforming const... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for X... no
checking for XF86VidModeSwitchToMode in -lXxf86vm... no
checking for ANSI C header files... (cached) yes
checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no
checking GL/glu.h usability... no
checking GL/glu.h presence... no
checking for GL/glu.h... no
checking GL/glx.h usability... no
checking GL/glx.h presence... no
checking for GL/glx.h... no
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for X11/extensions/xf86vmode.h... no
checking whether gcc needs -traditional... no
checking for vprintf... yes
checking for _doprnt... no
checking for main in -lm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating include/GL/Makefile
config.status: creating include/Makefile
config.status: creating progs/Makefile
config.status: creating progs/demos/CallbackMaker/Makefile
config.status: creating progs/demos/Fractals/Makefile
config.status: creating progs/demos/Fractals_random/Makefile
config.status: creating progs/demos/Lorenz/Makefile
config.status: creating progs/demos/Makefile
config.status: creating progs/demos/One/Makefile
config.status: creating progs/demos/shapes/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands

```


```
~/freeglut-2.4.0$ make
cd . \
          && CONFIG_FILES= CONFIG_HEADERS=config.h \
             /bin/bash ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
make  all-recursive
make[1]: Entering directory `/home/navneeth/freeglut-2.4.0'
Making all in src
make[2]: Entering directory `/home/navneeth/freeglut-2.4.0/src'
source='freeglut_callbacks.c' object='libglut_la-freeglut_callbacks.lo' libtool=yes \
        depfile='.deps/libglut_la-freeglut_callbacks.Plo' tmpdepfile='.deps/libglut_la-freeglut_callbacks.TPlo' \
        depmode=gcc3 /bin/bash ../depcomp \
        /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include    -g -O2 -Wall -pedantic -Werror -c -o libglut_la-freeglut_callbacks.lo `test -f freeglut_callbacks.c || echo './'`freeglut_callbacks.c
rm -f .libs/libglut_la-freeglut_callbacks.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include -g -O2 -Wall -pedantic -Werror -c freeglut_callbacks.c -MT libglut_la-freeglut_callbacks.lo -MD -MP -MF .deps/libglut_la-freeglut_callbacks.TPlo  -fPIC -DPIC -o .libs/libglut_la-freeglut_callbacks.lo
In file included from ../include/GL/freeglut.h:17,
                 from freeglut_callbacks.c:28:
../include/GL/freeglut_std.h:114:19: error: GL/gl.h: No such file or directory
../include/GL/freeglut_std.h:115:20: error: GL/glu.h: No such file or directory
In file included from ../include/GL/freeglut.h:17,
                 from freeglut_callbacks.c:28:
../include/GL/freeglut_std.h:432: error: expected ')' before 'layer'
../include/GL/freeglut_std.h:491: error: expected ')' before 'query'
../include/GL/freeglut_std.h:492: error: expected ')' before 'query'
../include/GL/freeglut_std.h:494: error: expected ')' before 'query'
../include/GL/freeglut_std.h:509: error: expected ')' before 'size'
../include/GL/freeglut_std.h:510: error: expected ')' before 'size'
../include/GL/freeglut_std.h:511: error: expected ')' before 'radius'
../include/GL/freeglut_std.h:512: error: expected ')' before 'radius'
../include/GL/freeglut_std.h:513: error: expected ')' before 'base'
../include/GL/freeglut_std.h:514: error: expected ')' before 'base'
../include/GL/freeglut_std.h:516: error: expected ')' before 'innerRadius'
../include/GL/freeglut_std.h:517: error: expected ')' before 'innerRadius'
../include/GL/freeglut_std.h:530: error: expected ')' before 'size'
../include/GL/freeglut_std.h:531: error: expected ')' before 'size'
../include/GL/freeglut_std.h:539: error: expected ')' before 'query'
../include/GL/freeglut_std.h:544: error: expected ')' before 'query'
../include/GL/freeglut_std.h:553: error: expected declaration specifiers or '...' before 'GLfloat'
../include/GL/freeglut_std.h:553: error: expected declaration specifiers or '...' before 'GLfloat'
../include/GL/freeglut_std.h:553: error: expected declaration specifiers or '...' before 'GLfloat'
../include/GL/freeglut_std.h:554: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'glutGetColor'
In file included from ../include/GL/freeglut.h:18,
                 from freeglut_callbacks.c:28:
../include/GL/freeglut_ext.h:97: error: expected ')' before 'option_flag'
../include/GL/freeglut_ext.h:108: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'glutStrokeHeight'
../include/GL/freeglut_ext.h:117: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:117: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:118: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:118: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:119: error: expected ')' before 'radius'
../include/GL/freeglut_ext.h:120: error: expected ')' before 'radius'
In file included from freeglut_callbacks.c:29:
freeglut_internal.h:95:24: error: GL/glx.h: No such file or directory
freeglut_internal.h:96:26: error: X11/Xlib.h: No such file or directory
freeglut_internal.h:97:27: error: X11/Xatom.h: No such file or directory
freeglut_internal.h:98:28: error: X11/keysym.h: No such file or directory
In file included from freeglut_callbacks.c:29:
freeglut_internal.h:176: error: expected specifier-qualifier-list before 'GLint'
cc1: warnings being treated as errors
freeglut_internal.h:178: warning: struct has no members
freeglut_internal.h:189: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:211: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:254: error: expected specifier-qualifier-list before 'Display'
freeglut_internal.h:285: warning: struct has no members
freeglut_internal.h:304: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'SFG_WindowHandleType'
freeglut_internal.h:305: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'SFG_WindowContextType'
freeglut_internal.h:321: error: expected specifier-qualifier-list before 'SFG_WindowHandleType'
freeglut_internal.h:331: warning: struct has no members
freeglut_internal.h:342: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:503: error: expected specifier-qualifier-list before 'XVisualInfo'
freeglut_internal.h:507: warning: struct has no members
freeglut_internal.h:521: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:539: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:565: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:605: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:607: warning: struct has no members
freeglut_internal.h:617: error: expected ':', ',', ';', '}' or '__attribute__' before '*' token
freeglut_internal.h:627: error: expected specifier-qualifier-list before 'GLfloat'
freeglut_internal.h:628: warning: struct has no members
freeglut_internal.h:640: error: expected specifier-qualifier-list before 'GLfloat'
freeglut_internal.h:643: warning: struct has no members
freeglut_internal.h:650: error: expected specifier-qualifier-list before 'GLfloat'
freeglut_internal.h:732: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
freeglut_internal.h:750: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:750: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:753: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:754: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:799: error: expected ')' before 'hWindow'
freeglut_internal.h:819: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'fgCheckActiveMenu'
freeglut_callbacks.c: In function 'glutDisplayFunc':
freeglut_callbacks.c:49: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutReshapeFunc':
freeglut_callbacks.c:61: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutKeyboardFunc':
freeglut_callbacks.c:71: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpecialFunc':
freeglut_callbacks.c:80: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutIdleFunc':
freeglut_callbacks.c:89: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:90: error: 'SFG_State' has no member named 'IdleCallback'
freeglut_callbacks.c: In function 'glutTimerFunc':
freeglut_callbacks.c:101: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:103: error: 'SFG_State' has no member named 'FreeTimers'
freeglut_callbacks.c:105: error: 'SFG_State' has no member named 'FreeTimers'
freeglut_callbacks.c:118: error: 'SFG_State' has no member named 'Timers'
freeglut_callbacks.c:124: error: 'SFG_State' has no member named 'Timers'
freeglut_callbacks.c: In function 'fghVisibility':
freeglut_callbacks.c:134: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutVisibilityFunc':
freeglut_callbacks.c:144: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutKeyboardUpFunc':
freeglut_callbacks.c:159: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpecialUpFunc':
freeglut_callbacks.c:168: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutJoystickFunc':
freeglut_callbacks.c:179: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:183: error: 'SFG_WindowState' has no member named 'JoystickPollRate'
freeglut_callbacks.c:185: error: 'SFG_WindowState' has no member named 'JoystickLastPoll'
freeglut_callbacks.c:186: error: 'SFG_WindowState' has no member named 'JoystickPollRate'
freeglut_callbacks.c:188: error: 'SFG_WindowState' has no member named 'JoystickLastPoll'
freeglut_callbacks.c:189: error: 'SFG_WindowState' has no member named 'JoystickLastPoll'
freeglut_callbacks.c: In function 'glutMouseFunc':
freeglut_callbacks.c:197: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMouseWheelFunc':
freeglut_callbacks.c:206: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMotionFunc':
freeglut_callbacks.c:216: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutPassiveMotionFunc':
freeglut_callbacks.c:226: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutEntryFunc':
freeglut_callbacks.c:235: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutCloseFunc':
freeglut_callbacks.c:244: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutWMCloseFunc':
freeglut_callbacks.c:250: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMenuDestroyFunc':
freeglut_callbacks.c:257: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMenuStateFunc':
freeglut_callbacks.c:267: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:268: error: 'SFG_State' has no member named 'MenuStateCallback'
freeglut_callbacks.c: In function 'glutMenuStatusFunc':
freeglut_callbacks.c:276: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:277: error: 'SFG_State' has no member named 'MenuStatusCallback'
freeglut_callbacks.c: In function 'glutOverlayDisplayFunc':
freeglut_callbacks.c:285: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutWindowStatusFunc':
freeglut_callbacks.c:294: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpaceballMotionFunc':
freeglut_callbacks.c:303: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpaceballRotateFunc':
freeglut_callbacks.c:312: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpaceballButtonFunc':
freeglut_callbacks.c:321: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutButtonBoxFunc':
freeglut_callbacks.c:330: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutDialsFunc':
freeglut_callbacks.c:339: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutTabletMotionFunc':
freeglut_callbacks.c:348: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutTabletButtonFunc':
freeglut_callbacks.c:357: error: 'SFG_State' has no member named 'Initialised'
make[2]: *** [libglut_la-freeglut_callbacks.lo] Error 1
make[2]: Leaving directory `/home/navneeth/freeglut-2.4.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/navneeth/freeglut-2.4.0'
make: *** [all] Error 2

```


```
~/freeglut-2.4.0$ sudo make install
Making install in src
make[1]: Entering directory `/home/navneeth/freeglut-2.4.0/src'
source='freeglut_callbacks.c' object='libglut_la-freeglut_callbacks.lo' libtool=yes \
        depfile='.deps/libglut_la-freeglut_callbacks.Plo' tmpdepfile='.deps/libglut_la-freeglut_callbacks.TPlo' \
        depmode=gcc3 /bin/bash ../depcomp \
        /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include    -g -O2 -Wall -pedantic -Werror -c -o libglut_la-freeglut_callbacks.lo `test -f freeglut_callbacks.c || echo './'`freeglut_callbacks.c
rm -f .libs/libglut_la-freeglut_callbacks.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include -g -O2 -Wall -pedantic -Werror -c freeglut_callbacks.c -MT libglut_la-freeglut_callbacks.lo -MD -MP -MF .deps/libglut_la-freeglut_callbacks.TPlo  -fPIC -DPIC -o .libs/libglut_la-freeglut_callbacks.lo
In file included from ../include/GL/freeglut.h:17,
                 from freeglut_callbacks.c:28:
../include/GL/freeglut_std.h:114:19: error: GL/gl.h: No such file or directory
../include/GL/freeglut_std.h:115:20: error: GL/glu.h: No such file or directory
In file included from ../include/GL/freeglut.h:17,
                 from freeglut_callbacks.c:28:
../include/GL/freeglut_std.h:432: error: expected ')' before 'layer'
../include/GL/freeglut_std.h:491: error: expected ')' before 'query'
../include/GL/freeglut_std.h:492: error: expected ')' before 'query'
../include/GL/freeglut_std.h:494: error: expected ')' before 'query'
../include/GL/freeglut_std.h:509: error: expected ')' before 'size'
../include/GL/freeglut_std.h:510: error: expected ')' before 'size'
../include/GL/freeglut_std.h:511: error: expected ')' before 'radius'
../include/GL/freeglut_std.h:512: error: expected ')' before 'radius'
../include/GL/freeglut_std.h:513: error: expected ')' before 'base'
../include/GL/freeglut_std.h:514: error: expected ')' before 'base'
../include/GL/freeglut_std.h:516: error: expected ')' before 'innerRadius'
../include/GL/freeglut_std.h:517: error: expected ')' before 'innerRadius'
../include/GL/freeglut_std.h:530: error: expected ')' before 'size'
../include/GL/freeglut_std.h:531: error: expected ')' before 'size'
../include/GL/freeglut_std.h:539: error: expected ')' before 'query'
../include/GL/freeglut_std.h:544: error: expected ')' before 'query'
../include/GL/freeglut_std.h:553: error: expected declaration specifiers or '...' before 'GLfloat'
../include/GL/freeglut_std.h:553: error: expected declaration specifiers or '...' before 'GLfloat'
../include/GL/freeglut_std.h:553: error: expected declaration specifiers or '...' before 'GLfloat'
../include/GL/freeglut_std.h:554: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'glutGetColor'
In file included from ../include/GL/freeglut.h:18,
                 from freeglut_callbacks.c:28:
../include/GL/freeglut_ext.h:97: error: expected ')' before 'option_flag'
../include/GL/freeglut_ext.h:108: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'glutStrokeHeight'
../include/GL/freeglut_ext.h:117: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:117: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:118: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:118: error: expected declaration specifiers or '...' before 'GLdouble'
../include/GL/freeglut_ext.h:119: error: expected ')' before 'radius'
../include/GL/freeglut_ext.h:120: error: expected ')' before 'radius'
In file included from freeglut_callbacks.c:29:
freeglut_internal.h:95:24: error: GL/glx.h: No such file or directory
freeglut_internal.h:96:26: error: X11/Xlib.h: No such file or directory
freeglut_internal.h:97:27: error: X11/Xatom.h: No such file or directory
freeglut_internal.h:98:28: error: X11/keysym.h: No such file or directory
In file included from freeglut_callbacks.c:29:
freeglut_internal.h:176: error: expected specifier-qualifier-list before 'GLint'
cc1: warnings being treated as errors
freeglut_internal.h:178: warning: struct has no members
freeglut_internal.h:189: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:211: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:254: error: expected specifier-qualifier-list before 'Display'
freeglut_internal.h:285: warning: struct has no members
freeglut_internal.h:304: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'SFG_WindowHandleType'
freeglut_internal.h:305: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'SFG_WindowContextType'
freeglut_internal.h:321: error: expected specifier-qualifier-list before 'SFG_WindowHandleType'
freeglut_internal.h:331: warning: struct has no members
freeglut_internal.h:342: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:503: error: expected specifier-qualifier-list before 'XVisualInfo'
freeglut_internal.h:507: warning: struct has no members
freeglut_internal.h:521: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:539: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:565: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:605: error: expected specifier-qualifier-list before 'GLboolean'
freeglut_internal.h:607: warning: struct has no members
freeglut_internal.h:617: error: expected ':', ',', ';', '}' or '__attribute__' before '*' token
freeglut_internal.h:627: error: expected specifier-qualifier-list before 'GLfloat'
freeglut_internal.h:628: warning: struct has no members
freeglut_internal.h:640: error: expected specifier-qualifier-list before 'GLfloat'
freeglut_internal.h:643: warning: struct has no members
freeglut_internal.h:650: error: expected specifier-qualifier-list before 'GLfloat'
freeglut_internal.h:732: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
freeglut_internal.h:750: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:750: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:753: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:754: error: expected declaration specifiers or '...' before 'GLboolean'
freeglut_internal.h:799: error: expected ')' before 'hWindow'
freeglut_internal.h:819: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'fgCheckActiveMenu'
freeglut_callbacks.c: In function 'glutDisplayFunc':
freeglut_callbacks.c:49: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutReshapeFunc':
freeglut_callbacks.c:61: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutKeyboardFunc':
freeglut_callbacks.c:71: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpecialFunc':
freeglut_callbacks.c:80: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutIdleFunc':
freeglut_callbacks.c:89: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:90: error: 'SFG_State' has no member named 'IdleCallback'
freeglut_callbacks.c: In function 'glutTimerFunc':
freeglut_callbacks.c:101: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:103: error: 'SFG_State' has no member named 'FreeTimers'
freeglut_callbacks.c:105: error: 'SFG_State' has no member named 'FreeTimers'
freeglut_callbacks.c:118: error: 'SFG_State' has no member named 'Timers'
freeglut_callbacks.c:124: error: 'SFG_State' has no member named 'Timers'
freeglut_callbacks.c: In function 'fghVisibility':
freeglut_callbacks.c:134: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutVisibilityFunc':
freeglut_callbacks.c:144: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutKeyboardUpFunc':
freeglut_callbacks.c:159: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpecialUpFunc':
freeglut_callbacks.c:168: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutJoystickFunc':
freeglut_callbacks.c:179: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:183: error: 'SFG_WindowState' has no member named 'JoystickPollRate'
freeglut_callbacks.c:185: error: 'SFG_WindowState' has no member named 'JoystickLastPoll'
freeglut_callbacks.c:186: error: 'SFG_WindowState' has no member named 'JoystickPollRate'
freeglut_callbacks.c:188: error: 'SFG_WindowState' has no member named 'JoystickLastPoll'
freeglut_callbacks.c:189: error: 'SFG_WindowState' has no member named 'JoystickLastPoll'
freeglut_callbacks.c: In function 'glutMouseFunc':
freeglut_callbacks.c:197: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMouseWheelFunc':
freeglut_callbacks.c:206: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMotionFunc':
freeglut_callbacks.c:216: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutPassiveMotionFunc':
freeglut_callbacks.c:226: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutEntryFunc':
freeglut_callbacks.c:235: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutCloseFunc':
freeglut_callbacks.c:244: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutWMCloseFunc':
freeglut_callbacks.c:250: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMenuDestroyFunc':
freeglut_callbacks.c:257: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutMenuStateFunc':
freeglut_callbacks.c:267: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:268: error: 'SFG_State' has no member named 'MenuStateCallback'
freeglut_callbacks.c: In function 'glutMenuStatusFunc':
freeglut_callbacks.c:276: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c:277: error: 'SFG_State' has no member named 'MenuStatusCallback'
freeglut_callbacks.c: In function 'glutOverlayDisplayFunc':
freeglut_callbacks.c:285: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutWindowStatusFunc':
freeglut_callbacks.c:294: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpaceballMotionFunc':
freeglut_callbacks.c:303: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpaceballRotateFunc':
freeglut_callbacks.c:312: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutSpaceballButtonFunc':
freeglut_callbacks.c:321: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutButtonBoxFunc':
freeglut_callbacks.c:330: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutDialsFunc':
freeglut_callbacks.c:339: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutTabletMotionFunc':
freeglut_callbacks.c:348: error: 'SFG_State' has no member named 'Initialised'
freeglut_callbacks.c: In function 'glutTabletButtonFunc':
freeglut_callbacks.c:357: error: 'SFG_State' has no member named 'Initialised'
make[1]: *** [libglut_la-freeglut_callbacks.lo] Error 1
make[1]: Leaving directory `/home/navneeth/freeglut-2.4.0/src'
make: *** [install-recursive] Error 1

```

---

### Post by navneeth on 2007-06-09
Bumping.

---

### Post by Sockerdrickan on 2007-06-09
checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no
checking GL/glu.h usability... no
checking GL/glu.h presence... no
checking for GL/glu.h... no
checking GL/glx.h usability... no
checking GL/glx.h presence... no
checking for GL/glx.h... no

---

### Post by navneeth on 2007-06-09
So do I do apt-get install gl.h glu.h glx.h?

Thanks for your help.

---

### Post by Sockerdrickan on 2007-06-09
Have you downloaded libsdl-dev?

---

### Post by navneeth on 2007-06-09
> **Tux0r said:**
> Have you downloaded libsdl-dev?

Nope. 

I'm just going through this list...

> 
        *  Hardware accelerated OpenGL (usually provided by your distro).
        * GLUT 3.7.
        * Or FreeGlut (better for full screen support than GLUT).
        * PLIB 1.8.3 version.
        * Modified OpenAL for optimal sound.
        * libpng and zlib (usually provided by your distro).


I'm assuming that the first has been taken care of. I'll download libsdl-dec now.

---

### Post by Sockerdrickan on 2007-06-09
You installed GPU driver right?

---

### Post by navneeth on 2007-06-09
libsdl downloaded and installed. 

I tried to install freeglut, and is throwing up the same errors, and plib still says that it could not find a GL directory. 

```
~/freeglut-2.4.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for an ANSI C-conforming const... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for X... no
checking for XF86VidModeSwitchToMode in -lXxf86vm... no
checking for ANSI C header files... (cached) yes
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking GL/glu.h usability... yes
checking GL/glu.h presence... yes
checking for GL/glu.h... yes
checking GL/glx.h usability... yes
checking GL/glx.h presence... yes
checking for GL/glx.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for X11/extensions/xf86vmode.h... no
checking whether gcc needs -traditional... no
checking for vprintf... yes
checking for _doprnt... no
checking for main in -lm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating include/GL/Makefile
config.status: creating include/Makefile
config.status: creating progs/Makefile
config.status: creating progs/demos/CallbackMaker/Makefile
config.status: creating progs/demos/Fractals/Makefile
config.status: creating progs/demos/Fractals_random/Makefile
config.status: creating progs/demos/Lorenz/Makefile
config.status: creating progs/demos/Makefile
config.status: creating progs/demos/One/Makefile
config.status: creating progs/demos/shapes/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: executing default-1 commands

```

This segment was shorter when I used 'sudo make install', instead of just 'make install'. The last line shows an error.
```
:~/freeglut-2.4.0$ sudo make install
Making install in src
make[1]: Entering directory `/home/navneeth/freeglut-2.4.0/src'
/bin/bash ../libtool --mode=link gcc  -g -O2 -Wall -pedantic -Werror   -o libglut.la -rpath /usr/local/lib -version-info 11:0:8 libglut_la-freeglut_callbacks.lo libglut_la-freeglut_cursor.lo libglut_la-freeglut_display.lo libglut_la-freeglut_ext.lo libglut_la-freeglut_font.lo libglut_la-freeglut_glutfont_definitions.lo libglut_la-freeglut_font_data.lo libglut_la-freeglut_stroke_roman.lo libglut_la-freeglut_stroke_mono_roman.lo libglut_la-freeglut_gamemode.lo libglut_la-freeglut_geometry.lo libglut_la-freeglut_init.lo libglut_la-freeglut_joystick.lo libglut_la-freeglut_main.lo libglut_la-freeglut_menu.lo libglut_la-freeglut_misc.lo libglut_la-freeglut_overlay.lo libglut_la-freeglut_state.lo libglut_la-freeglut_structure.lo libglut_la-freeglut_teapot.lo libglut_la-freeglut_videoresize.lo libglut_la-freeglut_window.lo -lm  -lGL -lGLU -lXext -lX11  
rm -fr .libs/libglut.la .libs/libglut.* .libs/libglut.*
gcc -shared  libglut_la-freeglut_callbacks.lo libglut_la-freeglut_cursor.lo libglut_la-freeglut_display.lo libglut_la-freeglut_ext.lo libglut_la-freeglut_font.lo libglut_la-freeglut_glutfont_definitions.lo libglut_la-freeglut_font_data.lo libglut_la-freeglut_stroke_roman.lo libglut_la-freeglut_stroke_mono_roman.lo libglut_la-freeglut_gamemode.lo libglut_la-freeglut_geometry.lo libglut_la-freeglut_init.lo libglut_la-freeglut_joystick.lo libglut_la-freeglut_main.lo libglut_la-freeglut_menu.lo libglut_la-freeglut_misc.lo libglut_la-freeglut_overlay.lo libglut_la-freeglut_state.lo libglut_la-freeglut_structure.lo libglut_la-freeglut_teapot.lo libglut_la-freeglut_videoresize.lo libglut_la-freeglut_window.lo  -lm -lGL -lGLU -lXext -lX11  -Wl,-soname -Wl,libglut.so.3 -o .libs/libglut.so.3.8.0
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
make[1]: *** [libglut.la] Error 1
make[1]: Leaving directory `/home/navneeth/freeglut-2.4.0/src'
make: *** [install-recursive] Error 1

```

**PLIB**

```
 ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
includedir changed to ${prefix}/include/plib libdir is ${exec_prefix}/lib
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for X... no
checking for pthread_create in -lpthread... no
checking for glNewList in -lGL... no
checking for glNewList in -lMesaGL... no
configure: error: could not find working GL library

```

---

### Post by navneeth on 2007-06-09
> **Tux0r said:**
> You installed GPU driver right?
I don't remember doing such a thing. Looking at its name, I'm guessing it has something to do with graphics cards... 

When I open the restricted drivers manager, it says that "Your hardware does not need any restricted drivers."

---

### Post by Sockerdrickan on 2007-06-09
The GLX error somehow makes me think of graphics card stuff but could that prevent one from compiling a 3D game? :S

---

### Post by navneeth on 2007-06-09
All this work really shows how advantageous a package management system is. :)

---

### Post by Sockerdrickan on 2007-06-09
Yeah that would be something B. Gates would want to have for his 9999 updates

---

