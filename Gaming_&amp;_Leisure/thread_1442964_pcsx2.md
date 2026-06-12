---
title: "pcsx2"
date: 2010-03-30
forum: Gaming &amp; Leisure
---

### Post by jklopez on 2010-03-30
anyone know how to download,install pcsx2 ,none of whats in the forum worked for me and i tried them all ,the closes thing that worked gave me errors at the end ...               sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
Linux/Makefile.am:5: shell pkg-config --cflags gtk+-2.0: non-POSIX variable name
Linux/Makefile.am:5: (probably a GNU make extension)
Linux/Makefile.am:6: compiling `callbacks.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.ac'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for ranlib... ranlib
checking dependency style of gcc... gcc3
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
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
  x86-64 build?           no
  Debug build?           no
  Dev build?               no
  SSE2 enabled?           yes
Making clean in Linux
make[1]: Entering directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl/Linux'
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE_URL=\"\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF .deps/libZeroGSLinux_a-callbacks.Tpo -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c
mv -f .deps/libZeroGSLinux_a-callbacks.Tpo .deps/libZeroGSLinux_a-callbacks.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE_URL=\"\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF .deps/libZeroGSLinux_a-Conf.Tpo -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp
In file included from Conf.cpp:25:
../GS.h:41:21: error: GL/glew.h: No such file or directory
Conf.cpp: In function ‘void LoadConfig()’:
Conf.cpp:66: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:67: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:68: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:69: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:70: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins
roots@roots-laptop:~/pcsx2$ sudo apt-get install libbz2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libbz2-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
roots@roots-laptop:~/pcsx2$ sh build.sh all
----------------------------------------
Building Graphics Synthesizer plugins...
----------------------------------------
----------------------
Building ZeroGS OpenGL
----------------------
Linux/Makefile.am:5: shell pkg-config --cflags gtk+-2.0: non-POSIX variable name
Linux/Makefile.am:5: (probably a GNU make extension)
Linux/Makefile.am:6: compiling `callbacks.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.ac'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for ranlib... ranlib
checking dependency style of gcc... gcc3
checking debug build... no
checking for _aligned_malloc... no
checking for _aligned_free... no
checking for development build...... no
checking check for sse2...... yes
checking for a x86-64 CPU... no
checking gtk2+... checking for pkg-config... pkg-config
checking OpenGL... checking for GL/gl.h... yes
checking for GL/glu.h... yes
checking for GL/glext.h... yes
checking for main in -lGL... yes
checking for main in -lGLU... yes
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
  x86-64 build?           no
  Debug build?           no
  Dev build?               no
  SSE2 enabled?           yes
Making clean in Linux
make[1]: Entering directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl/Linux'
test -z "libZeroGSLinux.a" || rm -f libZeroGSLinux.a
rm -f *.o
make[1]: Leaving directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl/Linux'
Making clean in .
make[1]: Entering directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl'
test -z "libZeroGSogl.a" || rm -f libZeroGSogl.a
test -z "libZeroGSoglr.so.0.96.2" || rm -f libZeroGSoglr.so.0.96.2
rm -f *.o
make[1]: Leaving directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl'
Making install in Linux
make[1]: Entering directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl/Linux'
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE_URL=\"\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-callbacks.o -MD -MP -MF .deps/libZeroGSLinux_a-callbacks.Tpo -c -o libZeroGSLinux_a-callbacks.o `test -f 'callbacks.c' || echo './'`callbacks.c
mv -f .deps/libZeroGSLinux_a-callbacks.Tpo .deps/libZeroGSLinux_a-callbacks.Po
gcc -DPACKAGE_NAME=\"ZeroGSogl\" -DPACKAGE_TARNAME=\"zerogsogl\" -DPACKAGE_VERSION=\"0.96.2\" -DPACKAGE_STRING=\"ZeroGSogl\ 0.96.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE_URL=\"\" -DPACKAGE=\"ZeroGSogl\" -DVERSION=\"0.96.2\" -DNDEBUG=1 -DRELEASE_TO_PUBLIC=1 -DZEROGS_SSE2=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLEXT_H=1 -I. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I../ -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -fPIC -I/opt/cg/include -L/opt/cg/lib -O3 -fomit-frame-pointer  -MT libZeroGSLinux_a-Conf.o -MD -MP -MF .deps/libZeroGSLinux_a-Conf.Tpo -c -o libZeroGSLinux_a-Conf.o `test -f 'Conf.cpp' || echo './'`Conf.cpp
In file included from Conf.cpp:25:
../GS.h:41:21: error: GL/glew.h: No such file or directory
Conf.cpp: In function ‘void LoadConfig()’:
Conf.cpp:66: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:67: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:68: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:69: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
Conf.cpp:70: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/roots/pcsx2/plugins/gs/zerogs/opengl/Linux'
make: *** [install-recursive] Error 1
Error with building plugins
    anyone know what all that stuff means and what went wrong and most important how to fix it so i can use it ,i know something is wrong because pcsx2 is not in my menu and its not in the  software center only pcsx is there not pcsx2 btw i'm running karmic and pcsx2 worked fine on this compter with windows 7 so hheellpp!!!!!!!!!!!!!!

---

### Post by portets on 2010-03-30
does the linux binary on their download page work?  [here]("http://pcsx2.net/downloads.php")

---

### Post by jklopez on 2010-03-30
i downloaded it earlyer today but dont know what to do with it...

---

### Post by portets on 2010-03-30
just extract the zipped folder somewhere and double click the "pcsx2" file. you might need to right click it>properties>permissions then check the box next to "allow executing file as program".

you might be missing some important dependencies for pcsx2 to run. i'm not sure what the exact names are in ubuntu, so open up the synaptic package manager and search for each of these items and install them:
> gtk2, libbz2, libjpeg, glew-dev, libxxf86vm-dev,  x11proto-xf86vidmodeautomake, autoconf, Nvidia  Cg-Toolkit,  libasound-dev, joystick

if you're running 64 bit, that might be the problem. the pcsx2 team doesn't officially support 64-bit.

---

### Post by jklopez on 2010-03-30
i'm running 32 bit and i got the  libxxf86vm-dev,autoconf, Nvidia  Cg-Toolkit, joystick,but the others arent in the pakge mngr ,no gtk2 but i have gtk-engines,gtk-engine-murrine,gtk-enine-pixbuf ,is any of these right,  no libz2 but i got libz2-dev,libz2-1.0 are these right,no libjpegbut i have libjpeg62,libjpeg62-dev are these right,no glew-dev but i got glew-utils dose that work, no libasound-dev but i got libasound2 and libasound2-plugins hows that work and no x11-proto-xf86vidmodeautomake only x11-proto-xf86vidmode-dev is that it ...if i need more where ealse can i get it...btw,thanx 4 the help...it's hard to find...btw ,i did'nt double click on the pcsx2 icon yet cuz you say'd i need those things first,

---

### Post by portets on 2010-03-30
okay, all of those should be correct. so yes to all of those packages you asked about.

now search for:

> libgtk2.0(install all that come up), libglew1.5(install both that come up),

after that, go ahead and click the pcsx2 file. also, did you put your ps2 bios file into the "bios" folder?

---

### Post by jklopez on 2010-03-30
[SIZE=6]I cant believe it...it works,it finely works.....your the man....portets is god....:guitar:[/SIZE]...i havent tried any games yet but it works it opens i can configure and everything ,i going hunting 4 games now thanx again...

---

