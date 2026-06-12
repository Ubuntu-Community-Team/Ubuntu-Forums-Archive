---
title: "NETGEN 5.3.1 on Ubuntu 16.04 LTS (64 bit)"
date: 2017-03-05
forum: Education &amp; Science
---

### Post by durza on 2017-03-05
Hello,

I am trying to compile and install the Netgen. I have already read some previous discussion, and it seems that there is no sufficient and actual guide for right installation.

I am following instructions from here:
[https://sourceforge.net/p/netgen-mesher/wiki/Home/](https://sourceforge.net/p/netgen-mesher/wiki/Home/)

Moreover, based on the previous unsuccessful steps the folloving packages are installed:
```
sudo apt-get install tk8.5 tcl8.5
sudo apt-get install tcl-dev tk-dev mesa-common-dev libjpeg-dev libtogl-dev
sudo apt install libglu1-mesa-dev freeglut3-dev
```
  
My compilation terminates by this way:
```

.
.
.
libtool: link: g++ -g -O2 -rdynamic -o .libs/netgen demoview.o ngappinit.o onetcl.o parallelfunc.o ngpkg.o  ../libsrc/visualization/libvisual.a ../libsrc/csg/.libs/libcsgvis.so ../libsrc/csg/.libs/libcsg.so ../libsrc/interface/.libs/libinterface.so ../libsrc/meshing/.libs/libmesh.so -L/usr/lib/Togl1.7 -lTogl -lGLU -L/usr/lib/x86_64-linux-gnu -ltk8.6 -ltcl8.6 -lGL -lXmu -lpthread -Wl,-rpath -Wl,/opt/netgen/lib
/usr/bin/ld: cannot find -lXmu
collect2: error: ld returned 1 exit status
Makefile:404: recipe for target 'netgen' failed
make[2]: *** [netgen] Error 1
make[2]: Leaving directory '/home/jc/.local/share/Trash/files/netgen-5.0.0/ng'
Makefile:352: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/jc/.local/share/Trash/files/netgen-5.0.0'
Makefile:283: recipe for target 'all' failed
make: *** [all] Error 2
```

I there anybody who is willing to help me please?

Thank you in advance

D.

---

### Post by Gemnoc on 2017-03-06
Hello durza,

```
libtool: link: g++ -g -O2 -rdynamic -o .libs/netgen demoview.o ngappinit.o onetcl.o parallelfunc.o ngpkg.o  ../libsrc/visualization/libvisual.a ../libsrc/csg/.libs/libcsgvis.so ../libsrc/csg/.libs/libcsg.so ../libsrc/interface/.libs/libinterface.so ../libsrc/meshing/.libs/libmesh.so -L/usr/lib/Togl1.7 -lTogl -lGLU -L/usr/lib/x86_64-linux-gnu -ltk8.6 -ltcl8.6 -lGL -lXmu -lpthread -Wl,-rpath -Wl,/opt/netgen/lib
/usr/bin/ld: cannot find -lXmu
```
Funny I got that same error last week while compiling else. It means that libxmu-dev is missing, you need to install it.

Getting netgen 5.3.1 on Ubuntu... What a challenge! It's so old now, I don't understand why it hasn't been packaged in Debian/Ubuntu yet!

I am part of the FreeCAD Maintainers team on Launchpad, we provide two PPA repositories of more up-to-date versions of FreeCAD than the ones found in the official Ubuntu repositories. The latest changes in the FEM workbench of FreeCAD as well as migrating to open cascade 7.1.0 (not present in the Ubuntu repositories either) forces us to try to package netgen 5.3.1. So I am just starting to look into it, but even though I've been packaging FreeCAD for a few years I still have much to learn. We also need to patch it to be compatible with OCCT 7.1.0, this work has already been done by others.

I am not sure what you intend to use netgen for, but the netgen 4.9.13 package in the Ubuntu repositories depend on liboce, have you installed those packages as well?
[http://packages.ubuntu.com/xenial/netgen](http://packages.ubuntu.com/xenial/netgen)

Cheers,

Norm

---

