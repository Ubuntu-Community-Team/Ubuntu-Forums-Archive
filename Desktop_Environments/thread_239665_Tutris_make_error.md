---
title: "Tutris make error"
date: 2006-08-19
forum: Desktop Environments
---

### Post by DirtDawg on 2006-08-19
Hi. Using Xubuntu trying to install Tutris via the [instructions in the community documents]("https://help.ubuntu.com/community/Tutris"). I have installed build-essential, and libsdl1.2-dev after an SDL error during ./config. 

But during make I get the following error:
```

~/packages/Tutris-1.0.1$ make

make  all-recursive
make[1]: Entering directory `/home/dirtdawg/packages/Tutris-1.0.1'
Making all in data
make[2]: Entering directory `/home/dirtdawg/packages/Tutris-1.0.1/data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dirtdawg/packages/Tutris-1.0.1/data'
Making all in src
make[2]: Entering directory `/home/dirtdawg/packages/Tutris-1.0.1/src'
source='cTutris.cpp' object='cTutris.o' libtool=no \
        depfile='.deps/cTutris.Po' tmpdepfile='.deps/cTutris.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        g++ -DHAVE_CONFIG_H -I. -I. -I..  -DDATA_DIR=\"/usr/local/share/games/tu tris/\" -g -O2 -I/usr/include/SDL -D_REENTRANT -Wall  -g -O2 -c -o cTutris.o `te st -f 'cTutris.cpp' || echo './'`cTutris.cpp
source='SoFont.cpp' object='SoFont.o' libtool=no \
        depfile='.deps/SoFont.Po' tmpdepfile='.deps/SoFont.TPo' \
        depmode=gcc3 /bin/sh ../depcomp \
        g++ -DHAVE_CONFIG_H -I. -I. -I..  -DDATA_DIR=\"/usr/local/share/games/tu tris/\" -g -O2 -I/usr/include/SDL -D_REENTRANT -Wall  -g -O2 -c -o SoFont.o `tes t -f 'SoFont.cpp' || echo './'`SoFont.cpp
g++  -g -O2   -o tutris  Main.o cTutris.o SoFont.o  -L/usr/lib -lSDL -lpthread
cTutris.o: In function `cTutris::LoadImage(std::basic_string<char, std::char_tra its<char>, std::allocator<char> >, bool)':/home/dirtdawg/packages/Tutris-1.0.1/s rc/cTutris.cpp:848: undefined reference to `IMG_Load'
:/home/dirtdawg/packages/Tutris-1.0.1/src/cTutris.cpp:854: undefined reference t o `IMG_Load'
collect2: ld returned 1 exit status
make[2]: *** [tutris] Error 1
make[2]: Leaving directory `/home/dirtdawg/packages/Tutris-1.0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dirtdawg/packages/Tutris-1.0.1'
make: *** [all] Error 2

```

 I have no idea how to even begin to fix it. Maybe it's best to let it go? 

Any ideas would be appreciated.

---

### Post by DirtDawg on 2006-08-19
I figured it out by just starting over with step one. :???:

---

