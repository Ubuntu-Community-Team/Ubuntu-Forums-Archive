---
title: "Need help on getting tools for making the frogatto files on Ubuntu 11.04."
date: 2011-05-03
forum: Gaming &amp; Leisure
---

### Post by KingHanco on 2011-05-03
sudo apt-get install subversion

svn checkout [http://frogatto.com/svn/trunk/](http://frogatto.com/svn/trunk/) frogatto_svn

cd frogatto_svn

========================================================

Here is the part I'm having trouble with.

sudo apt-get install libsdl-dev libsdl-image-dev libsdl-mixer-dev libsdl-ttf-dev libpng-dev libglew-dev libglu-dev libboost-dev

All these are missing and can't be download. How I get these in upgrade files?

Error on downloading.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libsdl1.2-dev' instead of 'libsdl-dev'
Note, selecting 'libpng12-dev' instead of 'libpng-dev'
Note, selecting 'libglew1.5-dev' instead of 'libglew-dev'
Note, selecting 'libglu1-mesa-dev' instead of 'libglu-dev'
Package libsdl-image-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package libsdl-mixer-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libsdl-image-dev' has no installation candidate
E: Package 'libsdl-mixer-dev' has no installation candidate
E: Unable to locate package libsdl-ttf-dev

---

### Post by Perfect Storm on 2011-05-03
Make sure that the -src sources are enable in the repositories. You can do that in Ubuntu Software Center or Synaptic Package Manager.

---

### Post by KingHanco on 2011-05-03
Are you talking about enable Source Code in Software Sources?

---

### Post by Perfect Storm on 2011-05-03
Aye, make sure all of them are enabled.
If they are enabled, you might check synaptic Package Manager for each package manuaaly as they sometimes change names.

---

### Post by KingHanco on 2011-05-03
OK I will enabled it.

---

### Post by KingHanco on 2011-05-03
I found those as name change. But...

mitchell@mitchell-GT5628:~$ cd frogatto_svn
mitchell@mitchell-GT5628:~/frogatto_svn$ make
ccache g++ -DIMPLEMENT_SAVE_PNG -fno-inline-functions -g -O2 -fno-inline-functions `sdl-config --cflags` -D_GNU_SOURCE=1 -D_REENTRANT -Wnon-virtual-dtor -Wreturn-type -fthreadsafe-statics -c src/IMG_savepng.cpp
/bin/sh: ccache: not found
make: *** [IMG_savepng.o] Error 127
mitchell@mitchell-GT5628:~/frogatto_svn$

---

### Post by Perfect Storm on 2011-05-03
try with libsdl-image1.2-dev

---

### Post by KingHanco on 2011-05-03
That one already install.

---

### Post by Perfect Storm on 2011-05-03
> **KingHanco said:**
> 
/bin/sh: ccache: not found

install ccache

---

### Post by KingHanco on 2011-05-03
Thanks. It working now.

---

