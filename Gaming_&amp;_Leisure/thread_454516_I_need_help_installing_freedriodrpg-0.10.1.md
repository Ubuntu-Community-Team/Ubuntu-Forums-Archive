---
title: "I need help installing freedriodrpg-0.10.1"
date: 2007-05-25
forum: Gaming &amp; Leisure
---

### Post by pwgthegreat on 2007-05-25
hi
I am new to linux and learning  a lot of cool things but I need help with the make command I am installing freedroidrpg-0.10.1 and installed the things I need to install this game

it is giving me errors hear is the code
```
root@blacktiger-desktop:~/freedroidrpg-0.10.1# make
make  all-recursive
make[1]: Entering directory `/home/blacktiger/freedroidrpg-0.10.1'
Making all in src
make[2]: Entering directory `/home/blacktiger/freedroidrpg-0.10.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -Wall -Wno-unused  -DFD_DATADIR='"/usr/local/share/freedroidrpg"' -ffast-math -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -MT menu.o -MD -MP -MF ".deps/menu.Tpo" -c -o menu.o menu.c; \
        then mv -f ".deps/menu.Tpo" ".deps/menu.Po"; else rm -f ".deps/menu.Tpo"; exit 1; fi
In file included from menu.c:32:
system.h:91:23: error: SDL_image.h: No such file or directory
system.h:98:21: error: SDL_net.h: No such file or directory
make[2]: *** [menu.o] Error 1
make[2]: Leaving directory `/home/blacktiger/freedroidrpg-0.10.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/blacktiger/freedroidrpg-0.10.1'
make: *** [all] Error 2

```
pleas help 

thanks.

---

### Post by DoktorSeven on 2007-05-25
1) Not a good idea to compile as root.  Do it as your user, and use sudo/root only when installing.

2) Whenever you get errors that it can't find a .h file, it's a good bet that you're missing the -dev package of a certain library.  In this case, it's SDLimage and SDLnet.  Search for "sdl image dev" and "sdl net dev" in Synaptic and install those (or using apt-cache search from a terminal).

Hint: libsdl-net1.2-dev libsdl-image1.2-dev

---

### Post by pwgthegreat on 2007-05-25
Thanks
It works great!!! :p

---

