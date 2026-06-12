---
title: "The Mana World PPC"
date: 2007-08-17
forum: Gaming &amp; Leisure
---

### Post by Ripfox on 2007-08-17
The Mana World is supposed to work under the ppc arc. but when i try to install it it complains about libc6. I have tried to fix this and nearly borked my system with a debian package, which i learned later is a bad thing to do (install debian libc6 or any non-ubuntu libc6 package)

Is this too obscure to hope for :)

---

### Post by Perfect Storm on 2007-08-17
Where did you get the package from? The Debian unstable package from the Mana World is not compatible with Ubuntu and their Ubuntu repo is out of date. 
Try compile from the source here is the best option.

---

### Post by Ripfox on 2007-08-17
I suspected that. Thanks for the reply AI.

---

### Post by Ripfox on 2007-08-20
Well this does not want to compile...:)

I have spent hours on dependencies (compiling them)
and then after I get it all satisfied, it gives me some error about not liking my video card. Oh well, are there any mmorpgs you can play easily on ppc Ubuntu? I dont even care what it is, I just want something to wast some time and level. :lolflag:

---

### Post by KingHanco on 2007-08-20
Is this the same thing? >>> The Mana World (TMW)

[http://sourceforge.net/project/showfiles.php?group_id=106790](http://sourceforge.net/project/showfiles.php?group_id=106790)

Here is the website as well. [http://themanaworld.org/](http://themanaworld.org/)

---

### Post by Ripfox on 2007-08-21
Yes...The Mana World.

Actually, I got it to compile, but here's what I get on "make"

Build with OpenGL: yes

configure complete, now type "make"

imac@imac-desktop:~/tmw-0.0.23$ make
make  all-recursive
make[1]: Entering directory `/home/imac/tmw-0.0.23'
Making all in data
make[2]: Entering directory `/home/imac/tmw-0.0.23/data'
Making all in graphics
make[3]: Entering directory `/home/imac/tmw-0.0.23/data/graphics'
Making all in gui
make[4]: Entering directory `/home/imac/tmw-0.0.23/data/graphics/gui'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/imac/tmw-0.0.23/data/graphics/gui'
Making all in images
make[4]: Entering directory `/home/imac/tmw-0.0.23/data/graphics/images'
Making all in ambient
make[5]: Entering directory `/home/imac/tmw-0.0.23/data/graphics/images/ambient'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/imac/tmw-0.0.23/data/graphics/images/ambient'
make[5]: Entering directory `/home/imac/tmw-0.0.23/data/graphics/images'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/imac/tmw-0.0.23/data/graphics/images'
make[4]: Leaving directory `/home/imac/tmw-0.0.23/data/graphics/images'
Making all in tiles
make[4]: Entering directory `/home/imac/tmw-0.0.23/data/graphics/tiles'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/imac/tmw-0.0.23/data/graphics/tiles'
make[4]: Entering directory `/home/imac/tmw-0.0.23/data/graphics'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/imac/tmw-0.0.23/data/graphics'
make[3]: Leaving directory `/home/imac/tmw-0.0.23/data/graphics'
Making all in help
make[3]: Entering directory `/home/imac/tmw-0.0.23/data/help'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/imac/tmw-0.0.23/data/help'
Making all in icons
make[3]: Entering directory `/home/imac/tmw-0.0.23/data/icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/imac/tmw-0.0.23/data/icons'
make[3]: Entering directory `/home/imac/tmw-0.0.23/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/imac/tmw-0.0.23/data'
make[2]: Leaving directory `/home/imac/tmw-0.0.23/data'
Making all in docs
make[2]: Entering directory `/home/imac/tmw-0.0.23/docs'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/imac/tmw-0.0.23/docs'
Making all in src
make[2]: Entering directory `/home/imac/tmw-0.0.23/src'
g++ -DHAVE_CONFIG_H -I. -I..  -DTMW_DATADIR=\""/usr/local/share/tmw/"\"   -Wall -DUSE_OPENGL -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT `pkg-config --cflags libxml-2.0` -I/usr/local/include  -g -O2 -MT tmw-resizegrip.o -MD -MP -MF .deps/tmw-resizegrip.Tpo -c -o tmw-resizegrip.o `test -f 'gui/widgets/resizegrip.cpp' || echo './'`gui/widgets/resizegrip.cpp
In file included from gui/widgets/resizegrip.cpp:28:
gui/widgets/../../graphics.h:27:39: error: guichan/sdl/sdlgraphics.hpp: No such file or directory
gui/widgets/../../graphics.h:58: error: expected class-name before ‘{’ token
make[2]: *** [tmw-resizegrip.o] Error 1
make[2]: Leaving directory `/home/imac/tmw-0.0.23/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/imac/tmw-0.0.23'
make: *** [all] Error 2

---

### Post by Perfect Storm on 2007-08-22
Did you compile guichan the latest? (required)
Also which flag did you use, to compile guichan. Please post the configure output of it.

---

### Post by Ripfox on 2007-08-22
Yes I had to compile guchian. I will post the output when I get home from work. Thanks!

---

