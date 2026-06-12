---
title: "FreeOrion segmentation fault on Lucid after installing from getdeb repository"
date: 2011-04-01
forum: Gaming &amp; Leisure
---

### Post by Naggobot on 2011-04-01
Installed FreeOrion from Getdeb repository. Version is 0.0r3258-1~getdeb3. 

Linux Kernel version is 
```
2.6.32-30-generic
```and all latest upgrades should be installed. 

Glxinfo returns
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    ---- deleted to shorten post --
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
      ---- deleted to shorten post --
GLX version: 1.2
GLX extensions:
        ---- deleted to shorten post --
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GME/GLE GEM 20091221 2009Q4 x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20

```So as far as I can fathom I have OpenGL version over 2.0 so something else is wrong. Will it help if I try to compile directly from source or is it a futile attempt?

---

### Post by Soulcage on 2011-04-01
It's probably because you're using a intel gpu, but I don't know.

---

### Post by Naggobot on 2011-04-01
Pretty much my toughs also. I think I will not bother with attempting to compile from source especially since the documentation recommends having at least 2Gb ram for compiling and I have only 1 Gb.

---

