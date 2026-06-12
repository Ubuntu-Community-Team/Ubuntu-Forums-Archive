---
title: "Installing UFO 2000???"
date: 2011-03-01
forum: Gaming &amp; Leisure
---

### Post by Nutbun on 2011-03-01
I have downloaded the source file for UFO2000, the only install instructions that came with it was to type "# make".  
I have tried this but am getting no where.  Can anyone help me to install this please?

---

### Post by Perfect Storm on 2011-03-01
Did you type # make or make?

The # indicates that you should run the command as user. So in ubuntu's case you just type make.

---

### Post by Nutbun on 2011-03-01
> **Artificial Intelligence said:**
> Did you type # make or make?

The # indicates that you should run the command as user. So in ubuntu's case you just type make.

I tried it both ways. :)
I don't know how the 'make' command would work, all I see in the folder is a 'makefile' file.  I really don't know what I am doing here.

---

### Post by Perfect Storm on 2011-03-01
Downloaded to test it.

Installing compiling tools and -dev libs to build ufo2000
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential liballegro4.2-dev libhawknl-dev libdumb1-dev
```

Downloading, compiling:
```
cd ~/Desktop
wget http://prdownloads.sourceforge.net/ufo2000/ufo2000-0.9.1142-src.tar.bz2?download
tar jxfv ufo2000-*-src.tar.bz2*
cd ufo2000*
make
```

eg. Make a launcher for the game:

sh -c "cd <path> && ./ufo2000"


Eventually if you have a copy of X-com you can copy those files into UF02000 x-com folder.

---

### Post by Nutbun on 2011-03-01
All went well up until I use the make command.  This is what was returned.


```
make: svnversion: Command not found
make: freetype-config: Command not found
g++ -MMD -funsigned-char -Wall -Wno-deprecated-declarations -I src/lua -I src/luasqlite3 -DDEBUGMODE -O2 -pipe  -DHAVE_FREETYPE -DGLYPH_TARGET=GLYPH_TARGET_ALLEGRO -DGK_NO_LEGACY -DHAVE_PNG -DLINUX -I/usr/include -c src/bullet.cpp -o obj/bullet.o
In file included from src/bullet.cpp:22:
src/stdafx.h:88: fatal error: expat.h: No such file or directory
compilation terminated.
make: *** [obj/bullet.o] Error 1
```

Have I broke something? :)

---

### Post by Perfect Storm on 2011-03-01
> src/stdafx.h:88: fatal error: expat.h: No such file or directory

Install libexpat1-dev and try again.

---

### Post by Nutbun on 2011-03-01
It got a lot further this time, thanks.
But then I get this error...


```
In file included from src/main.cpp:54:
src/zfstream.h:15: fatal error: zlib.h: No such file or directory
compilation terminated.
make: *** [obj/main.o] Error 1

```

And it repeatedly said this..

make: freetype-config: Command not found

---

### Post by Perfect Storm on 2011-03-01
> **Nutbun said:**
> It got a lot further this time, thanks.
But then I get this error...


```
In file included from src/main.cpp:54:
src/zfstream.h:15: fatal error: zlib.h: No such file or directory
compilation terminated.
make: *** [obj/main.o] Error 1

```

And it repeatedly said this..

make: freetype-config: Command not found


libfreetype6-dev

and 

zlib1g-dev

---

### Post by Nutbun on 2011-03-01
I really thought it was going to make it this time, until....


```
src/loadpng/loadpng.c:8: fatal error: png.h: No such file or directory
compilation terminated.
make: *** [obj/loadpng.o] Error 1
```

I'm thinking this game needs a entire operating system of it's own.

---

### Post by Perfect Storm on 2011-03-01
It usually requires a bunch of -dev packages to compile stuff ;)

The next thing you need to install is
libpng12-dev

---

### Post by Nutbun on 2011-03-01
Thank you AI.  At last it works, now lets hope it was all worth it. ;)

---

### Post by Ackbar's Homegirl on 2011-06-16
Hey ya'll! I followed the same steps when encountering similar problems with installing UFO2000

The post of terminal:
> (username):~/Desktop/ufo2000-0.9.1142$ make
make: svnversion: Command not found
mkdir obj
make: allegro-config: Command not found
g++ -MMD -funsigned-char -Wall -Wno-deprecated-declarations -I src/lua -I src/luasqlite3 -DDEBUGMODE -O2 -pipe -I/usr/include/freetype2 -DHAVE_FREETYPE -DGLYPH_TARGET=GLYPH_TARGET_ALLEGRO -DGK_NO_LEGACY -DHAVE_PNG -DLINUX  -c src/bullet.cpp -o obj/bullet.o
In file included from src/stdafx.h:19:0,
                 from src/bullet.cpp:22:
src/jpgalleg/jpgalleg.h:23:21: fatal error: allegro.h: No such file or directory
compilation terminated.
make: *** [obj/bullet.o] Error 1


---

