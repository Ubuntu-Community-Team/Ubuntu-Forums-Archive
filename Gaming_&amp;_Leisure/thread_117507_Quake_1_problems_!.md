---
title: "Quake 1 problems !"
date: 2006-01-15
forum: Gaming &amp; Leisure
---

### Post by drfalkor on 2006-01-15
I downloaded the glxquake, and put it in the folders etc ...
tryed to start quake like this:
```
./glquake
```

but then I got this:
```
Added packfile ./id1/pak0.pak (339 files)
Added packfile ./id1/pak1.pak (85 files)
PackFile: ./id1/pak1.pak : gfx/pop.lmp
Playing registered version.
PackFile: ./id1/pak0.pak : gfx.wad
Console initialized.
UDP Initialized
Exe: 15:26:37 Nov 12 2001
16.0 megabyte heap
PackFile: ./id1/pak0.pak : gfx/palette.lmp
PackFile: ./id1/pak0.pak : gfx/colormap.lmp
Using XFree86-VidModeExtension Version 2.2
GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce FX 5200/AGP/SSE/3DNOW!
GL_VERSION: 2.0.0 NVIDIA 76.67
Error: memory overwrite in Sys_Printf

```

hmmm, I searched at google for [COLOR="Red"]memory overwrite in Sys_Printf "quake"[/COLOR]

and then I found this answer:
[COLOR="Blue"]This error means you need to edit file sys_linux.c, procedure Sys_Printf, at or near line 89, and change text[1024] to text[4096] and recompile.[/COLOR]

ok, here is my question - how can I recompile a kernel I have installed via apt ? do I need to recompile the whole kernel just for that ? Isn't there a cool trick to do ? anyway, If I must recompile the whole kernel, I want ALL the settings from this kernel .

thnx :razz:

---

### Post by Mr_Grieves on 2006-01-15
sys_linux.c seems to be a kernel source file.. If you will need to compile the kernel, you'll need to download the kernel source to be able to do a compile of it. It's available with all the other stuff via Synaptic ;) You'll also need build-essentials and some other stuff..

Read more here: [https://wiki.ubuntu.com/KernelCompileHowto](https://wiki.ubuntu.com/KernelCompileHowto)

---

### Post by drfalkor on 2006-01-15
damn, recompiling :???: anway - thank you very much :)

---

### Post by drfalkor on 2006-01-15
hmm, weird (for me) ..
```
# apt-get install linux-tree-2.6.12
# cd /usr/src
# tar jxf linux-source-2.6.12.tar.bz2
# updatedb
# locate sys_linux.c
#
```

I could not find the sys_linux.c file :???:

---

### Post by drfalkor on 2006-01-15
Nevermind, got it to work with this:
[http://www.wh-hms.uni-ulm.de/~mfcn/shared/glxquake/glxquake.tar.gz](http://www.wh-hms.uni-ulm.de/~mfcn/shared/glxquake/glxquake.tar.gz) :oops:

---

### Post by minisori on 2006-01-15
These are engine modifications of QuakeWorld and Quake. They work much better and add alot new features.. like 16bits textures, dynamic lights, new particles, etc..

There are others like telejano, tenebrae (give a look&feel to doom3).. and others. As far i remember they are programing now tenebrae 2 engine wich will be a new completly game.

Look in fuhquake forums to find the high resolution textures pack or in google for quake retexturing project. There was also another for models and sounds.

[http://www.fuhquake.net/](http://www.fuhquake.net/)
[http://icculus.org/twilight/darkplaces/](http://icculus.org/twilight/darkplaces/)

---

### Post by Asraniel on 2006-01-15
play nexuiz ;-)
darkplace is also a nice quake engine (nexuiz is based on it)

---

### Post by drfalkor on 2006-01-15
I play nexuiz to ;)

---

