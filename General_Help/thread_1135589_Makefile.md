---
title: "Makefile"
date: 2009-04-24
forum: General Help
---

### Post by Monotoko on 2009-04-24
Hiya, i am attempting to upgrade my video drivers as advised here: [http://ubuntuforums.org/showthread.php?t=1135474](http://ubuntuforums.org/showthread.php?t=1135474)

I downloaded the driver, and have untarred it, and i just have a load of files, if i remember rightly, i need to do something to makefile to make it install.

I dont know what to do though

Can anyone help? Thanks in advance! :)

---

### Post by kanikilu on 2009-04-24
I haven't used that driver, but it should come with some sort of README or INSTALL files, or some sort of documentation...

---

### Post by Monotoko on 2009-04-24
I cant make heads or tails of it :S
but im assuming its this bit i maybe need:
> 1.3 Building with traditional Makefiles

The traditional Mesa build system is based on a collection of pre-defined system configurations.

To see the list of configurations, just type make. Then choose a configuration from the list and type make configname.

Mesa may be built in several different ways using the predefined configurations:

    * Stand-alone/Xlib mode - Mesa will be compiled as a software renderer using Xlib to do all rendering. The libGL.so library will be a self-contained rendering library that will allow you to run OpenGL/GLX applications on any X server (regardless of whether it supports the GLX X server extension). You will not be able to use hardware 3D acceleration.

      To compile stand-alone Mesa type make in the top-level directory. You'll see a list of supported system configurations. Choose one from the list (such as linux-x86), and type:

          make linux-x86

      This will produce libGL.so and several other libraries
    * DRI/accelerated - The DRI hardware drivers for accelerated OpenGL rendering (for ATI, Intel, Matrox, etc) will be built. The libGL.so library will support the GLX extension and will load/use the DRI hardware drivers.

      Build Mesa and the DRI hardware drivers by running

         make linux-dri

      There are also linux-dri-x86, linux-dri-x86-64, and linux-ppc configurations which are optimized for those architectures.

      Make sure you have the prerequisite versions of DRM and Xserver mentioned above.

Later, if you want to rebuild for a different configuration run make realclean before rebuilding. 

so i tried to just run "make" inside the dir...for it to give me a crapload of errors :S

```
monotoko@monotoko-laptop-linux:~/Desktop/mesa$ make
make[1]: Entering directory `/home/monotoko/Desktop/mesa/src'
Making sources for linux-dri
make[2]: Entering directory `/home/monotoko/Desktop/mesa/src/glx/x11'
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" glcontextmodes.c -o glcontextmodes.o
Package libdrm was not found in the pkg-config search path.
Perhaps you should add the directory containing `libdrm.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libdrm' found
glcontextmodes.c:40:19: error: X11/X.h: No such file or directory
In file included from glcontextmodes.c:41:
../../../include/GL/glx.h:38:22: error: X11/Xlib.h: No such file or directory
../../../include/GL/glx.h:39:23: error: X11/Xutil.h: No such file or directory
In file included from ../../../include/GL/gl.h:2150,
                 from ../../../include/GL/glx.h:45,
                 from glcontextmodes.c:41:
../../../include/GL/glext.h:3943:22: error: inttypes.h: No such file or directory
In file included from ../../../include/GL/gl.h:2150,
                 from ../../../include/GL/glx.h:45,
                 from glcontextmodes.c:41:
../../../include/GL/glext.h:3975: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLint64EXT’
../../../include/GL/glext.h:3976: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLuint64EXT’
../../../include/GL/glext.h:7708: error: expected declaration specifiers or ‘...’ before ‘GLint64EXT’
../../../include/GL/glext.h:7709: error: expected declaration specifiers or ‘...’ before ‘GLuint64EXT’
../../../include/GL/glext.h:8059: error: expected declaration specifiers or ‘...’ before ‘GLuint64EXT’
../../../include/GL/glext.h:8060: error: expected declaration specifiers or ‘...’ before ‘GLuint64EXT’
../../../include/GL/glext.h:8063: error: expected declaration specifiers or ‘...’ before ‘GLint64EXT’
../../../include/GL/glext.h:8064: error: expected declaration specifiers or ‘...’ before ‘GLuint64EXT’
In file included from glcontextmodes.c:41:
../../../include/GL/glx.h:179: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXPixmap’
../../../include/GL/glx.h:180: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXDrawable’
../../../include/GL/glx.h:183: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXFBConfigID’
../../../include/GL/glx.h:184: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXContextID’
../../../include/GL/glx.h:185: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXWindow’
../../../include/GL/glx.h:186: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXPbuffer’
../../../include/GL/glx.h:190: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glx.h:193: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:196: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:198: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXMakeCurrent’
../../../include/GL/glx.h:201: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:204: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:206: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreateGLXPixmap’
../../../include/GL/glx.h:209: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:211: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXQueryExtension’
../../../include/GL/glx.h:213: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXQueryVersion’
../../../include/GL/glx.h:215: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXIsDirect’
../../../include/GL/glx.h:217: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:222: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXGetCurrentDrawable’
../../../include/GL/glx.h:228: error: expected ‘)’ before ‘font’
../../../include/GL/glx.h:233: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:235: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:237: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:241: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glx.h:245: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:248: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:251: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:254: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glx.h:257: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreateWindow’
../../../include/GL/glx.h:260: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:262: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreatePixmap’
../../../include/GL/glx.h:265: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:267: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXCreatePbuffer’
../../../include/GL/glx.h:270: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:272: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:275: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:279: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXMakeContextCurrent’
../../../include/GL/glx.h:282: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘glXGetCurrentReadDrawable’
../../../include/GL/glx.h:284: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:287: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:290: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:294: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:295: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:296: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:297: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glx.h:298: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glx.h:298: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:299: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:300: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glx.h:300: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:301: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:302: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glx.h:302: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:303: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:304: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:305: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:306: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glx.h:306: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:307: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glx.h:307: warning: type defaults to ‘int’ in declaration of ‘GLXDrawable’
../../../include/GL/glx.h:307: error: ‘GLXDrawable’ declared as function returning a function
../../../include/GL/glx.h:308: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glx.h:309: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:310: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:311: error: expected ‘)’ before ‘*’ token
In file included from ../../../include/GL/glx.h:336,
                 from glcontextmodes.c:41:
../../../include/GL/glxext.h:385: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXVideoSourceSGIX’
../../../include/GL/glxext.h:389: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXFBConfigIDSGIX’
../../../include/GL/glxext.h:394: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GLXPbufferSGIX’
../../../include/GL/glxext.h:398: error: expected specifier-qualifier-list before ‘Bool’
../../../include/GL/glxext.h:518: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:553: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:553: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:554: error: ‘PFNGLXGETCURRENTREADDRAWABLESGIPROC’ declared as function returning a function
../../../include/GL/glxext.h:582: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glxext.h:583: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:584: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:584: warning: type defaults to ‘int’ in declaration of ‘GLXContextID’
../../../include/GL/glxext.h:584: error: ‘GLXContextID’ declared as function returning a function
../../../include/GL/glxext.h:585: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:586: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:599: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:600: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:601: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:601: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:602: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:603: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../../../include/GL/glxext.h:604: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:616: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:616: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:617: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:618: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:619: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:620: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:628: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:640: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:641: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:642: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:643: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:644: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:662: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:671: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:672: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:672: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:680: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:680: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:688: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:696: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:696: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:704: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:704: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:712: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:712: warning: type defaults to ‘int’ in declaration of ‘Bool’
../../../include/GL/glxext.h:712: error: ‘Bool’ declared as function returning a function
../../../include/GL/glxext.h:732: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:733: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:734: error: expected declaration specifiers or ‘...’ before ‘*’ token
../../../include/GL/glxext.h:734: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:735: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:736: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:780: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:781: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:782: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:783: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:784: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:785: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:786: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:787: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:812: error: expected ‘)’ before ‘*’ token
../../../include/GL/glxext.h:813: error: expected ‘)’ before ‘*’ token
In file included from glcontextmodes.c:41:
../../../include/GL/glx.h:366: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:367: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:368: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:369: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:370: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:371: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:383: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:384: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:385: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:408: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:409: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:410: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:411: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:413: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:414: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:415: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:416: error: expected ‘)’ before ‘*’ token
../../../include/GL/glx.h:500: error: field ‘send_event’ declared as a function
../../../include/GL/glx.h:501: error: expected specifier-qualifier-list before ‘Display’
glcontextmodes.c:42:23: error: GL/glxint.h: No such file or directory
glcontextmodes.c:60:27: error: X11/Xlibint.h: No such file or directory
In file included from glcontextmodes.h:33,
                 from glcontextmodes.c:67:
../../../include/GL/internal/glcore.h:34:23: error: sys/types.h: No such file or directory
In file included from glcontextmodes.c:67:
glcontextmodes.h:39: warning: type defaults to ‘int’ in declaration of ‘__GLXvisualConfig’
glcontextmodes.h:39: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
glcontextmodes.c: In function ‘_gl_convert_to_x_visual_type’:
glcontextmodes.c:106: error: ‘TrueColor’ undeclared (first use in this function)
glcontextmodes.c:106: error: (Each undeclared identifier is reported only once
glcontextmodes.c:106: error: for each function it appears in.)
glcontextmodes.c:106: error: ‘DirectColor’ undeclared (first use in this function)
glcontextmodes.c:107: error: ‘PseudoColor’ undeclared (first use in this function)
glcontextmodes.c:107: error: ‘StaticColor’ undeclared (first use in this function)
glcontextmodes.c:108: error: ‘GrayScale’ undeclared (first use in this function)
glcontextmodes.c:108: error: ‘StaticGray’ undeclared (first use in this function)
glcontextmodes.c: At top level:
glcontextmodes.c:132: warning: type defaults to ‘int’ in declaration of ‘__GLXvisualConfig’
glcontextmodes.c:132: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
glcontextmodes.c: In function ‘_gl_context_modes_create’:
glcontextmodes.c:398: warning: implicit declaration of function ‘Xmalloc’
glcontextmodes.c:405: warning: implicit declaration of function ‘memset’
glcontextmodes.c:405: warning: incompatible implicit declaration of built-in function ‘memset’
glcontextmodes.c: In function ‘_gl_context_modes_destroy’:
glcontextmodes.c:444: warning: implicit declaration of function ‘Xfree’
make[2]: *** [glcontextmodes.o] Error 1
make[2]: Leaving directory `/home/monotoko/Desktop/mesa/src/glx/x11'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/monotoko/Desktop/mesa/src'
make: *** [default] Error 1
```

---

### Post by kanikilu on 2009-04-24
> Make sure you have the prerequisite versions of DRM and Xserver mentioned above. My guess is that you need those development packages. Try:```
sudo apt-get install libdrm-dev xorg-dev
``` :?:

---

### Post by Monotoko on 2009-04-24
I did that, and  then ran make again, it looked like it did something, but then right near the end failed.

```
monotoko@monotoko-laptop-linux:~/Desktop/mesa$ make
make[1]: Entering directory `/home/monotoko/Desktop/mesa/src'
Making sources for linux-dri
make[2]: Entering directory `/home/monotoko/Desktop/mesa/src/glx/x11'
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" glcontextmodes.c -o glcontextmodes.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" clientattrib.c -o clientattrib.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" compsize.c -o compsize.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" eval.c -o eval.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" glxcmds.c -o glxcmds.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" glxcurrent.c -o glxcurrent.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" glxext.c -o glxext.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" glxextensions.c -o glxextensions.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" indirect.c -o indirect.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" indirect_init.c -o indirect_init.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" indirect_size.c -o indirect_size.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" indirect_window_pos.c -o indirect_window_pos.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" indirect_texture_compression.c -o indirect_texture_compression.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" indirect_transpose_matrix.c -o indirect_transpose_matrix.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" indirect_vertex_array.c -o indirect_vertex_array.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" indirect_vertex_program.c -o indirect_vertex_program.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" pixel.c -o pixel.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" pixelstore.c -o pixelstore.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" render2.c -o render2.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" renderpix.c -o renderpix.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" single2.c -o single2.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" singlepix.c -o singlepix.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" vertarr.c -o vertarr.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" xfont.c -o xfont.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" glx_pbuffer.c -o glx_pbuffer.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" glx_query.c -o glx_query.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" drisw_glx.c -o drisw_glx.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" dri_common.c -o dri_common.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" dri_glx.c -o dri_glx.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" XF86dri.c -o XF86dri.o
XF86dri.c:617: warning: no previous prototype for ‘XF86DRIOpenFullScreen’
XF86dri.c:628: warning: no previous prototype for ‘XF86DRICloseFullScreen’
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" glxhash.c -o glxhash.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa -I../../../src/mesa/glapi `pkg-config --cflags libdrm`  -I/usr/X11R6/include -Wall -Wmissing-prototypes -std=c99 -ffast-math -O -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_POSIX_MEMALIGN  -fno-strict-aliasing -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DDEFAULT_DRIVER_DIR=\"/usr/local/lib/dri\" dri2_glx.c -o dri2_glx.o
In file included from dri2_glx.c:47:
dri2.h:37:39: error: X11/extensions/dri2tokens.h: No such file or directory
dri2_glx.c: In function ‘dri2CopySubBuffer’:
dri2_glx.c:207: error: ‘DRI2BufferFrontLeft’ undeclared (first use in this function)
dri2_glx.c:207: error: (Each undeclared identifier is reported only once
dri2_glx.c:207: error: for each function it appears in.)
dri2_glx.c:207: error: ‘DRI2BufferBackLeft’ undeclared (first use in this function)
dri2_glx.c: In function ‘dri2WaitX’:
dri2_glx.c:235: error: ‘DRI2BufferFakeFrontLeft’ undeclared (first use in this function)
dri2_glx.c:235: error: ‘DRI2BufferFrontLeft’ undeclared (first use in this function)
dri2_glx.c: In function ‘dri2WaitGL’:
dri2_glx.c:255: error: ‘DRI2BufferFrontLeft’ undeclared (first use in this function)
dri2_glx.c:255: error: ‘DRI2BufferFakeFrontLeft’ undeclared (first use in this function)
make[2]: *** [dri2_glx.o] Error 1
make[2]: Leaving directory `/home/monotoko/Desktop/mesa/src/glx/x11'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/monotoko/Desktop/mesa/src'
make: *** [default] Error 1

```

---

### Post by Monotoko on 2009-04-24
Anyone?

---

### Post by Monotoko on 2009-04-24
Is this just uninstallable then?

---

### Post by paradigm2 on 2009-04-24
> **Monotoko said:**
> Anyone?

Hello.  I've seen you help others here today so I will try to help you.  I had to compile a different mesa driver mysel (Here is where I learned to do this: [http://ubuntuforums.org/showpost.php?p=7112705&postcount=16](http://ubuntuforums.org/showpost.php?p=7112705&postcount=16) ).

First make sure you have autoconf installed.

If not,

```

sudo apt-get install autoconf

```

then do

```
sudo apt-get build-dep mesa
```

If you have not already.

Now in the main source directory, do

```

./autogen.sh

```

This should check dependencies and show you what you don't have and need to get.

When it is finally good (will probably take few cycles of getting errors, installing dependencies, running ./autogen.sh again, etc) backup your old driver then,

```

make

```

in the main source directory.

This ought to do it.

You [probably then need to copy the correct driver over to where they told you to put it, then reboot, etc.

---

### Post by Monotoko on 2009-04-24
It worked! Thank you very much :)

And i try to help anyone i can as much as possible, whats the point in being knowledgeable about something if you cant share that knowledge?

Popcorn for all! :) :popcorn:

---

