---
title: "quake4 don't play when It is execute from linux terminal.."
date: 2015-03-15
forum: Gaming &amp; Leisure
---

### Post by fbio7 on 2015-03-15
Hi everbody..

Someone can Help me...I Install quake4 using the Linux binary following the link : 
[http://www.gamersonlinux.com/forum/threads/quake-4-guide.572/](http://www.gamersonlinux.com/forum/threads/quake-4-guide.572/)

I also see:
[https://help.ubuntu.com/community/Games/Native/Quake4](https://help.ubuntu.com/community/Games/Native/Quake4)

So...I execute the program for the terminal,..the initial screen shows up, I click for new game, the game load and show a link "click here to continue" when I click the game finish, show the terminal error and my resolution on screen change...

ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)

snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output

ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)

ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
ENABLE_INTEL_VERTEXCACHE_OPT: Possible Junk (!block->vbo)
double fault Segmentation fault, bailing out
shutdown terminal support
Segmentation fault (core dumped)

---

### Post by MikeCyber on 2015-03-16
Intel integrated graphics? Get a Nvidia card.

---

### Post by fbio7 on 2015-04-21
Today 04/21/2015...I play the game quake 4 from native linux version normaly !!!

What changes...

I remove everthing from quake4...dont forget the hidden folder /home/quake4
I rebuild the binary...
I get a system update...(update ubuntu)
I install wine version 1.7.38 32 bits for other aplication (office)
I install libsdl1.2debian:i386...( sudo apt-get install libsdl1.2debian:i386)

I hope this can help others that has the same problem...thats all !!

---

