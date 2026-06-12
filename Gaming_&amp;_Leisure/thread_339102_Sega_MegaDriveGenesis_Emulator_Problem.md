---
title: "Sega MegaDrive/Genesis Emulator Problem"
date: 2007-01-15
forum: Gaming &amp; Leisure
---

### Post by Crypto-138 on 2007-01-15
Recently I've had the urge to be able to play through all those games I played as a kid again, and though I have the consoles and everything, I'd much rather play on my computer, since my TV is always in use lately.

I looked up a couple of emulators, and I hear Gens is still a bit buggy on linux. The best sounding ones are Dgen and Generator, and Dgen is waay old.

Generator seems to have been worked on a bit more recently, so I got that, and tried to compile it with gtk and cmz80 as its z80 emulator. 
(I'd use RAZE, but that's written in ASM for intel processors; I have an AMD64. I think it would work, but I want something compiled for my own processor)

I tried downloading the source [here](http://www.squish.net/generator/download.html), and downloaded the missing dependencies, but when I try to compile, It gets to the cmzz80 and outputs this:
```
Making all in cmz80
make[2]: Entering directory `/home/david/downloads/src/generator-0.35/cmz80'
source='z80.c' object='z80.o' libtool=no \
        depfile='.deps/z80.Po' tmpdepfile='.deps/z80.TPo' \
        depmode=gcc3 /bin/bash ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../hdr -I.    -O3 -ffast-math -fomit-frame-pointer -c `test -f z80.c || echo './'`z80.c
z80.c:637: error: static declaration of &#8216;Inc&#8217; follows non-static declaration
z80stb.h:131: error: previous declaration of &#8216;Inc&#8217; was here
z80.c:650: error: static declaration of &#8216;Dec&#8217; follows non-static declaration
z80stb.h:132: error: previous declaration of &#8216;Dec&#8217; was here
make[2]: *** [z80.o] Error 1
make[2]: Leaving directory `/home/david/downloads/src/generator-0.35/cmz80'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/downloads/src/generator-0.35'
make: *** [all] Error 2

```

Anyone know what, if anything I'm doing wrong? Is there a newer, emulator for the Genesis? (MegaDrive as it's known outside of the US)

---

### Post by _simon_ on 2007-01-15
Can't help with your problem but I've been using Gens for a while and never had any problems with it.

Gens deb available here: [http://www.ubuntuforums.org/showthread.php?t=290008&highlight=Gens](http://www.ubuntuforums.org/showthread.php?t=290008&highlight=Gens)

---

### Post by Crypto-138 on 2007-01-15
I got Generator to compile using the patched version [here](http://www.ghostwhitecrab.com/generator/), but It gave me a weird green screen.

I installed gens from that .deb, and even though it's i386, it works perfectly, almost as good as the Windows version. My only complaint is the OpenGL support is a bit slow, but that's probably because my window manager is beryl.

Anyways, I tested it with the Sonic 2 Beta:
[center][IMG]http://img387.imageshack.us/img387/6141/sonic2bmt1.png[/IMG]
It worked perfectly[/center]

Thanks for the link!

---

