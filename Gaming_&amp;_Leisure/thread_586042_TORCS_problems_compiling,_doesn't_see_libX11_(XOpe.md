---
title: "TORCS problems compiling, doesn't see libX11 (XOpenDisplay), on an AMD64"
date: 2007-10-21
forum: Gaming &amp; Leisure
---

### Post by kundalinikat on 2007-10-21
Hello, I'm running 64-bit Gutsy on an AMD64, trying to compile TORCS 1.3.0. I've poked through Synaptic and installed many libx*-dev packages that mentioned X11 in the description. 

```
rrrob@machine:~/Desktop/torcs-1.3.0$ ./configure
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
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C++ preprocessor... g++ -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking for ar... ar
checking for ld... ld
checking whether byte ordering is bigendian... no
checking for X... libraries , headers 
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking GL/glut.h usability... yes
checking GL/glut.h presence... yes
checking for GL/glut.h... yes
checking GL/glx.h usability... yes
checking GL/glx.h presence... yes
checking for GL/glx.h... yes
checking X11/Xlib.h usability... yes
checking X11/Xlib.h presence... yes
checking for X11/Xlib.h... yes
checking X11/Xatom.h usability... yes
checking X11/Xatom.h presence... yes
checking for X11/Xatom.h... yes
checking X11/keysym.h usability... yes
checking X11/keysym.h presence... yes
checking for X11/keysym.h... yes
checking plib/ssg.h usability... yes
checking plib/ssg.h presence... yes
checking for plib/ssg.h... yes
checking AL/al.h usability... yes
checking AL/al.h presence... yes
checking for AL/al.h... yes
checking AL/alut.h usability... yes
checking AL/alut.h presence... yes
checking for AL/alut.h... yes
checking for sin in -lm... yes
checking for XOpenDisplay in -lX11... no
configure: error: Can't find libX11. Please check config.log and if you can't solve the problem send the file to torcs-users@lists.sourceforge.net with the subject "torcs compilation problem"
rrrob@machine:~/Desktop/torcs-1.3.0$ 

```

---

### Post by buntunub on 2007-10-22
I am having this same problem. Any suggestions?

---

### Post by JAwuku on 2007-12-08
I'm having the same problem with Gutsy. The build of torcs 1.3.0 in the repository is lacking seriously in cars. I thus decided to compile it on my own.

I am getting the same errors i.e
```
[checking for XOpenDisplay in -lX11... no
configure: error: Can't find libX11.
```

I got around this by issuing the command:
```
./configure --x-libraries=/usr/lib/ 
```

I then got another error, and this was solved with installing

[B]libalut-dev
freeglut3-dev
build-essential
libopenal-dev
libpng12-dev
libxmu-dev
zlib1g-dev
plib1.8.4-dev
libxxf86vm-dev
libxrandr-dev
libxrender-dev
[/B]

together with all their dependencies, in Synaptic

Redo the command

```
./configure --x-libraries=/usr/lib/ 
make
make install
```

and all should be well....


A more elegant way would be to use checkinstall (install via synaptic)

The most elegant way would be to install the torcs sources and patch them with the full torcs data sources and rebuild, if anyone out there knows how to do this.

---

### Post by megazayed on 2008-05-27
i have ubuntu 8.4 with 32-bit intel processor and i have problem with compiling this game and this what happen after writing "make" command :


make[5]: *** [CarSoundData.o] Error 1
make[5]: Leaving directory `/home/ahmed/Desktop/torcs-1.3.0/src/modules/graphic/ssggraph'
make[4]: *** [subdirs] Error 1
make[4]: Leaving directory `/home/ahmed/Desktop/torcs-1.3.0/src/modules/graphic'
make[3]: *** [subdirs] Error 1
make[3]: Leaving directory `/home/ahmed/Desktop/torcs-1.3.0/src/modules'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/ahmed/Desktop/torcs-1.3.0/src'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/ahmed/Desktop/torcs-1.3.0'
make: *** [restart] Error 2




what can i do ?

---

### Post by Perfect Storm on 2008-05-27
See if this help; [http://gaming.gwos.org/doku.php/guides:64bit:torcs](http://gaming.gwos.org/doku.php/guides:64bit:torcs)

---

### Post by megazayed on 2008-05-27
sorry this is me again !
HOWTO ? uninstall torcs-1.2.4-openal.tar.bz2 
becouse i think it makes a problem for installing trocs-1.3.0

---

### Post by Perfect Storm on 2008-05-27
Download 1.2.4.
Unpack it.
configure it
make
then sudo make uninstall

---

