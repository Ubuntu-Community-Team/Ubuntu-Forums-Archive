---
title: "Poor performance on a Dell D600"
date: 2006-06-05
forum: Desktop Environments
---

### Post by conan1 on 2006-06-05
Hi, I have a problem with a Dell Latitude D600. The user interface is generally slow and unresponsive (just moving my cursor across the menus increases my cpu usage to about 50%. I have a Radeon R250 Lf, although I am not sure that it is to blame. It sounds a lot like the problem described in [http://ubuntuforums.org/showthread.php?t=148669](http://ubuntuforums.org/showthread.php?t=148669). I need help!!! What must I do??

I just tried to install fglrx, but when i run fglrxinfo i get:

[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI

and about 200 more entries like this.... 

dmesg | grep fglrx

outputs this:

[4294742.627000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294742.638000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294742.639000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294744.726000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294744.727000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294744.728000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4294744.733000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294744.828000] [fglrx] total      GART = 134217728
[4294744.829000] [fglrx] free       GART = 118222848
[4294744.830000] [fglrx] max single GART = 118222848
[4294744.830000] [fglrx] total      LFB  = 28307456
[4294744.831000] [fglrx] free       LFB  = 22016000
[4294744.831000] [fglrx] max single LFB  = 22016000
[4294744.832000] [fglrx] total      Inv  = 0
[4294744.832000] [fglrx] free       Inv  = 0
[4294744.849000] [fglrx] max single Inv  = 0
[4294745.003000] [fglrx] total      TIM  = 0
[4295158.172000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4295158.173000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4295158.173000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4295158.177000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4295158.218000] [fglrx] total      GART = 134217728
[4295158.218000] [fglrx] free       GART = 118222848
[4295158.219000] [fglrx] max single GART = 118222848
[4295158.219000] [fglrx] total      LFB  = 28307456
[4295158.219000] [fglrx] free       LFB  = 22016000
[4295158.220000] [fglrx] max single LFB  = 22016000
[4295158.220000] [fglrx] total      Inv  = 0
[4295158.220000] [fglrx] free       Inv  = 0
[4295158.221000] [fglrx] max single Inv  = 0
[4295158.221000] [fglrx] total      TIM  = 0



I really hope this will provide some clues for a clever brain somewhere :)

---

### Post by conan1 on 2006-06-07
bump?

---

### Post by jgcamp99 on 2006-06-07
That's about what my bosses D610 laptop spit out. 6.06 won't even go onto my old Compaq 12XL125 without being a miserable experience. I like 6.06 on my desktops though.

---

### Post by eeclark on 2006-06-07
I have a Dell Lat D800 with an ATI card running 6.06 with compiz/XGL.
No problems here.
Have you checked the memory to make sure there isn't a hardware issue?

---

### Post by conan1 on 2006-06-08
How do I check the memory?

---

### Post by eeclark on 2006-06-08
in the grub menu (when you boot) there should be / could be a memtest entry

---

