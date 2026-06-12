---
title: "pcsx2 problem at installation"
date: 2009-04-02
forum: Gaming &amp; Leisure
---

### Post by urd on 2009-04-02
> **buttons said:**
> Check it out on the official page, [here]("http://www.pcsx2.net/")!

There are 32-bit and 64-bit binaries, as well as an [SVN repository]("http://sourceforge.net/svn/?group_id=79721").

I'm running Edgy, and I managed to compile the SVN, so here is a mini-howto for compilation.  This is by no means comprehensive, as who knows what -dev packages you might be missing that I've picked up somewhere along the line.

I KNOW it requires:

libbz2-dev
subversion
libjpeg62-dev
build-essential
libgtk2.0-dev
libxxf86vm-dev
x11proto-xf86vidmode-dev
automake1.9
Nvidia Cg-Toolkit (available [HERE]("http://developer.nvidia.com/object/cg_toolkit.html"))

The automake version is important, as it will spit all sorts of errors if you have an earlier version.

It PROBABLY requires:
libglu1-mesa-dev

I can't actually say it needs that for certain, only that I have it and the INSTALL file says you need OpenGL libs in order to compile.

-----------

Okay, so let's grab our required things:

```
sudo apt-get install subversion libjpeg62-dev build-essential libgtk2.0-dev libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 libbz2-dev
```
Our maybe required things:
```
sudo apt-get install libglu1-mesa-dev
```

The SVN code:

```
svn co https://pcsx2.svn.sourceforge.net/svnroot/pcsx2 pcsx2
```

Aaaand build it!

```
cd pcsx2
sh build.sh all
```

And hopefully everything should build!

EDIT: libbz2-dev is required for the ISO plugins to compile


the nvidia toolkit its necesary for ati cards too??? i didn't install it because i don't know if i need that for ati cards too ... this the result

```
urd@urd-laptop:~/pcsx2$ sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
/usr/share/aclocal/snacc.m4:24: warning: underquoted definition of AM_PATH_SNACC
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... no
checking for GL/glu.h... no
checking for GL/glext.h... no
checking for main in -lGL... yes
checking for main in -lGLU... no
checking for main in -lGLEW... no
checking Cg... checking for main in -ljpeg... yes
checking for main in -lpthread... yes
checking for main in -lstdc++... yes
checking for main in -lz... yes
checking for main in -ldl... yes
checking for main in -lXxf86vm... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Linux/Makefile
config.status: executing depfiles commands
Configuration:
  Target system type:    
  x86-64 build?	       no
  Debug build?	       no
  Dev build?	           no
  SSE2 enabled?		   yes
Making clean in Linux
make[1]: Entering directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl/Linux'
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF ".deps/libZeroGSLinux_a-callbacks.Tpo" -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c; \
	then mv -f ".deps/libZeroGSLinux_a-callbacks.Tpo" ".deps/libZeroGSLinux_a-callbacks.Po"; else rm -f ".deps/libZeroGSLinux_a-callbacks.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -I. -I. -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF ".deps/libZeroGSLinux_a-Conf.Tpo" -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp; \
	then mv -f ".deps/libZeroGSLinux_a-Conf.Tpo" ".deps/libZeroGSLinux_a-Conf.Po"; else rm -f ".deps/libZeroGSLinux_a-Conf.Tpo"; exit 1; fi
In file included from Conf.cpp:25:
../GS.h:41:21: error: GL/glew.h: No such file or directory
../GS.h:42:19: error: GL/gl.h: No such file or directory
../GS.h:43:20: error: GL/glx.h: No such file or directory
In file included from Conf.cpp:25:
../GS.h:110: error: ‘GLXContext’ does not name a type
Conf.cpp: In function ‘void LoadConfig()’:
Conf.cpp:66: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:67: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:68: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:69: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:70: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/urd/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins

```

if is the toolkit how i install it??

i have a toshiba satelite
whit ati x1200
proccesor amd turionx2 of 1.9 ghz
2 gb ram

thanks

---

