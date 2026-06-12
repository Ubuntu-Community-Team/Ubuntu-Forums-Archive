---
title: "zdoom on Gutsy?"
date: 2007-11-04
forum: Gaming &amp; Leisure
---

### Post by Dark Aspect on 2007-11-04
I am trying to compile zdoom on Ubuntu 7.10 but I get this error:

> sh: svnversion: not found
/bin/sh: sdl-config: not found
Compiling sc_man.cpp:                                                 [ERROR]  
g++ -fno-rtti -pipe -Wall -Wno-unused -fno-strict-aliasing -O2 -fomit-frame-pointer -MMD -DHAVE_FILELENGTH -D__forceinline=inline -Izlib -IFLAC -Dstricmp=strcasecmp -Dstrnicmp=strncasecmp -DNEED_STRUPR -Isrc/ -Isrc/g_doom/ -Isrc/g_heretic/ -Isrc/g_hexen/ -Isrc/g_raven/ -Isrc/g_shared/ -Isrc/g_strife/ -Isrc/oplsynth/ -Isrc/sound/ -Isrc/sdl/ -Isrc/textures/ -DUSEASM=1 -DNDEBUG -o releaseobj/sc_man.o -c src/sc_man.cpp
================================================================================src/sc_man_scanner.re: In function ‘bool SC_GetString()’:
src/sc_man_scanner.re:144: error: no matching function for call to ‘MIN(long int, int)’
make: *** [releaseobj/sc_man.o] Error 1

I am using the 64-bit version of Ubuntu so that may have something to do with it.I have installed all of the dependences (I think).Any ideas?

---

### Post by Crafty Kisses on 2007-11-04
> **Dark Aspect said:**
> I am trying to compile zdoom on Ubuntu 7.10 but I get this error:



I am using the 64-bit version of Ubuntu so that may have something to do with it.I have installed all of the dependences (I think).Any ideas?

Not sure about zdoom, but lxdoom works fine for me. :)

---

### Post by Dark Aspect on 2007-11-04
well I can't get lxldoom to play back in full screen and prboom hangs on Ubuntu.Prboom did this in 7.04 and 6.10 AND apparently its a known problem because when I searched google for an answer I found [this]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg462114.html") .

Doomsday does not work with 64-bit Linux so it would seem I have no way to play Doom back natively.Ideas for any other ports?

---

### Post by disturbedite on 2007-11-04
i'd like to recommend skulltag on ubuntu.  (its based on zdoom).  its the best 2d doom port there is imo.

there is an ubuntu pacakge available on the skulltag website.

---

### Post by Dark Aspect on 2007-11-05
Hm I have a problem with lxldoom now:

> LxDoom v1.4.4 ([http://lxdoom.linuxgames.com/](http://lxdoom.linuxgames.com/))
lxdoom: z_zone.c:226: Z_Init: Assertion `32 >= sizeof(memblock_t) && (4*1024*1024) > (128*1024)' failed.
Aborted (core dumped)


I haven't tried skulltag yet.

---

