---
title: "compiling vdrift?"
date: 2005-12-15
forum: Gaming &amp; Leisure
---

### Post by nalmeth on 2005-12-15
hey
I'm kinda new to open-source gaming, but it looks promising :) 
I've install Nexuiz and some other games but I'm having trouble installing vdrift. I have downloaded the .bz, but don't know what to do with it.
How do you compile it or install it?

Can anyone recommend some really awesome open-source 3D games?

:KS

---

### Post by nalmeth on 2005-12-15
ok, this has been a long process, and I think I'm almost there.
I had to install gcc, sdl, g++, and make. I have run ./confiugre, and managed to pull it off with no errors finally!
make runs a lot of commands fine, and then it all goes wrong near the end

```

:~/Games/vdrift-2005-09-01$ make
Making all in include
make[1]: Entering directory `/home/nalmeth/Games/vdrift-2005-09-01/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/nalmeth/Games/vdrift-2005-09-01/include'
Making all in src
make[1]: Entering directory `/home/nalmeth/Games/vdrift-2005-09-01/src'
source='main.cpp' object='main.o' libtool=no \
DEPDIR=.deps depmode=none /bin/sh ../depcomp \
g++ -DPACKAGE_NAME=\"VDrift\" -DPACKAGE_TARNAME=\"vdrift\" -DPACKAGE_VERSION=\"2005-09-01\" -DPACKAGE_STRING=\"VDrift\ 2005-09-01\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"vdrift\" -DVERSION=\"2005-09-01\" -DSTDC_HEADERS=1 -DHAVE_OPENAL=1 -Dios_base=ios  -I. -I. -I../include    -I/usr/include/SDL -D_REENTRANT -c -o main.o main.cpp
/usr/include/c++/4.0.2/iosfwd:135: error: conflicting declaration ‘typedef struct std::basic_ios<char, std::char_traits<char> > std::ios’
/usr/include/c++/4.0.2/iosfwd:105: error: ‘struct std::ios’ has a previous declaration as ‘struct std::ios’
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/nalmeth/Games/vdrift-2005-09-01/src'
make: *** [all-recursive] Error 1
nalmeth@edubuntu:~/Games/vdrift-2005-09-01$ sudo make install
Making install in include
make[1]: Entering directory `/home/nalmeth/Games/vdrift-2005-09-01/include'
make[2]: Entering directory `/home/nalmeth/Games/vdrift-2005-09-01/include'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/nalmeth/Games/vdrift-2005-09-01/include'
make[1]: Leaving directory `/home/nalmeth/Games/vdrift-2005-09-01/include'
Making install in src
make[1]: Entering directory `/home/nalmeth/Games/vdrift-2005-09-01/src'
source='main.cpp' object='main.o' libtool=no \
DEPDIR=.deps depmode=none /bin/sh ../depcomp \
g++ -DPACKAGE_NAME=\"VDrift\" -DPACKAGE_TARNAME=\"vdrift\" -DPACKAGE_VERSION=\"2005-09-01\" -DPACKAGE_STRING=\"VDrift\ 2005-09-01\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"vdrift\" -DVERSION=\"2005-09-01\" -DSTDC_HEADERS=1 -DHAVE_OPENAL=1 -Dios_base=ios  -I. -I. -I../include    -I/usr/include/SDL -D_REENTRANT -c -o main.o main.cpp
/usr/include/c++/4.0.2/iosfwd:135: error: conflicting declaration ‘typedef struct std::basic_ios<char, std::char_traits<char> > std::ios’
/usr/include/c++/4.0.2/iosfwd:105: error: ‘struct std::ios’ has a previous declaration as ‘struct std::ios’
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/nalmeth/Games/vdrift-2005-09-01/src'
make: *** [install-recursive] Error 1


```

For the past errors I've gotten over, I was able to install a package to move on. I have no idea what this one means.

Anyone know what to make of this?

---

### Post by curuxz on 2006-01-14
We realy need Deb versions of this, its getting stupid to have to do all this to get the game to work.

---

