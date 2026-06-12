---
title: "problem compiling ZZogl plugin for PCSX2"
date: 2009-11-26
forum: Gaming &amp; Leisure
---

### Post by underworld288 on 2009-11-26
I am trying to set up the PCSX 0.9.6 PS2 emulator. I have found that the best gpu plugin is the zzogl one and I'm trying to compile it (i got the source from svn just now). When I go into the zzogl directory the is a build.sh file and a opengl folder. When I try to compile i run into this problem... 

```
$ sh build.sh
----------------------
Building ZZOpenGL
----------------------
make: *** No targets specified and no makefile found.  Stop.
$

```

does anybody have any suggestions?

---

### Post by underworld288 on 2009-11-27
ok, i'm an idiot, I have figured out what i was doing wrong with zzogl. I needed to specify 'all' after 'sh build.sh'.

---

### Post by debili on 2010-11-03
if i do that then i get
```

In file included from Conf.cpp:25:
./../GS.h:53:22: error: PS2Edefs.h: No such file or directory
In file included from Conf.cpp:25:
./../GS.h:55: error: ‘u32’ does not name a type
./../GS.h:56: error: ‘u32’ does not name a type
./../GS.h:57: error: expected initializer before ‘PS2EgetLibName’
In file included from Conf.cpp:25:
./../GS.h:68: error: ‘u32’ does not name a type
./../GS.h:76: error: expected initializer before ‘void’
./../GS.h:88: error: expected initializer before ‘void’
make[1]: *** [libZeroGSLinux_a-Conf.o] Error 1
make[1]: Leaving directory `/home/user/Desktop/ZZogl/opengl/Linux'
make: *** [install-recursive] Error 1

```

please could somebody help me with that ?
thanks

---

### Post by wingnux on 2010-11-04
Are you running 32 or 64bit version of Ubuntu? If it's the 64bit version you'll have to run it from a chroot since pcsx2 doesn't support 64bit architectures.

If you're running Ubuntu 32bit you can always download the latest beta from their website: [http://pcsx2.net/downloads.php?p=publicbeta](http://pcsx2.net/downloads.php?p=publicbeta)

---

