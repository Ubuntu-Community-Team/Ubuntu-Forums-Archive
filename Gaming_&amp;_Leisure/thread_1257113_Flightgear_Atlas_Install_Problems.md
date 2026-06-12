---
title: "Flightgear Atlas Install Problems"
date: 2009-09-03
forum: Gaming &amp; Leisure
---

### Post by ChrisB111 on 2009-09-03
I downloaded atlas for flightgear from their site and have tried to follow the installation instructions. When I run the configure script I get this output, it contains an error at the end, can anyone tell me what the error is and if possible how to solve it? (I have also attached the full output in the config.log).

Chris

```
chris@chris-desktop:~$ cd Atlas-0.3.0/
chris@chris-desktop:~/Atlas-0.3.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
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
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
Plib not specified
SimGear not specified
FlightGear base package location not specified
Default NONE/lib/FlightGear
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for extra include and lib directories...
   + found /usr/X11R6/bin
   + found /usr/local//include
   + found /usr/local//lib
   + found /usr/local//bin
checking for X... no
checking for cos in -lm... yes
checking for pthread_exit in -lpthread... yes
checking for socket in -lsocket... no
checking for XCreateWindow in -lX11... no
checking for XShmCreateImage in -lXext... no
checking for XGetExtensionVersion in -lXi... no
checking for IceOpenConnection in -lICE... no
checking for SmcOpenConnection in -lSM... no
checking for XtMalloc in -lXt... no
checking for XmuLookupStandardColormap in -lXmu... no
checking for glNewList in -lGLcore... no
checking for glNewList in -lGL... no
checking for glNewList in -lMesaGL... no
checking for gluLookAt in -lGLU... no
checking for gluLookAt in -lMesaGLU... no
checking for glutGetModifiers in -lglut... no
checking for glutGameModeString in -lglut... no

Unable to find the necessary OpenGL or GLUT libraries.
See config.log for automated test details and results ...
chris@chris-desktop:~/Atlas-0.3.0$ 

```

---

### Post by Perfect Storm on 2009-09-03
I'm not at my computer, so I can't give the exact info;

But from I can see you need to install libglu-dev, libglut-dev, xlib-dev, libxext-dev. Properly some more when you re-run the configure script.

---

