---
title: "Savage 2 white 3d animations"
date: 2009-07-24
forum: Gaming &amp; Leisure
---

### Post by ilcontegis on 2009-07-24
Hi guys,

I have this problem......
```
teo@teo:~/Savage2$ ./savage2.bin 
warning: The VAD has been replaced by a hack pending a complete rewrite
Mesa 7.6-devel implementation error: Unsupported opcode 8 (BGNLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6-devel implementation error: Unsupported opcode 11 (BRK) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6-devel implementation error: Unsupported opcode 27 (ENDLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6-devel implementation error: Unsupported opcode 8 (BGNLOOP) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6-devel implementation error: Unsupported opcode 11 (BRK) in vertex shader
Please report at bugzilla.freedesktop.org
Mesa 7.6-devel implementation error: Unsupported opcode 27 (ENDLOOP) in vertex shader
Please report at bugzilla.freedesktop.org

```
This is my graphic card (I have a vaio tt)
```
teo@teo:~/Savage2$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090712 2009Q2 RC3 
OpenGL version string: 2.1 Mesa 7.6-devel
OpenGL shading language version string: 1.20
OpenGL extensions:

```
I upgraded on the latest intel driver available...now the game runs (before was not even running) but I have the 3d animation all in white.
Does somebody has some idea how to solve this problem?

Thank you so much
Teo

---

### Post by snargfish on 2009-07-24
I think your screwed for now. Intel drivers don't work very well with OpenGL 2.x yet.

---

### Post by ilcontegis on 2009-07-25
> **snargfish said:**
> I think your screwed for now. Intel drivers don't work very well with OpenGL 2.x yet.
First thank you very much for your answer.
Not yet? OpenGL 2.1 went out in 2006, 3 years ago....In 2008 OpenGL 3.
Intel still does not give a proper support for something so old? I'm really shocked.
There is nothing to do, I will simply never buy an intel graphic card anymore. I passed from Ati to intel because people told me that there would not be any problem with intel as gives opensource drivers. Nevertheless it seems to me that intel as well does not release good drivers as well.....Even with the latest version went out few days ago.
I will wait but I do not have so much hope.....this means that the support for OpenGL 3 will arrive in 2020....very good.....:(

---

### Post by snargfish on 2009-07-25
> **ilcontegis said:**
> First thank you very much for your answer.
Not yet? OpenGL 2.1 went out in 2006, 3 years ago....In 2008 OpenGL 3.
Intel still does not give a proper support for something so old? I'm really shocked.
There is nothing to do, I will simply never buy an intel graphic card anymore. I passed from Ati to intel because people told me that there would not be any problem with intel as gives opensource drivers. Nevertheless it seems to me that intel as well does not release good drivers as well.....Even with the latest version went out few days ago.
I will wait but I do not have so much hope.....this means that the support for OpenGL 3 will arrive in 2020....very good.....:(

Lol well yeah, Intel are about 3 years behind most other GPU manufacturers ! :lolflag:

---

