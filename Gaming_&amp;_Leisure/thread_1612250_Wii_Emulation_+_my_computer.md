---
title: "Wii Emulation + my computer"
date: 2010-11-02
forum: Gaming &amp; Leisure
---

### Post by JustinR on 2010-11-02
Hey everybody,

The forums @ the Dolphin website was not helpful - and I'm pretty sure 99.9% percent of the users didn't know what Linux was - and this seems to be an Ubuntu problem, so here I am.

I compiled the 32bit version of the Nintendo GameCube/Wii emulator, Dolphin-Emu from their SVN (the PPA was out of date) on top of Ubuntu 10.10 w/ full updates and all dependencies to Dolphin-emu. GameCube games run full speed - but Wii games don't seem to work.

My computer specs:
CPU: Intel Core 2 Duo 2.00GHZ 
GPU: nVidia GeForce 8600M GT (Full support for OpenGL2.1/DirectX10)
RAM: 3.00 GBs

So, Nintendo Wii games, when started - even at a low resolution (640x480) and in window mode show, "FPS: 0 VPS: 40-50 Speed: 40-80%".

I don't understand why FPS is at zero - the games are completely un-playable.

So, thinking maybe the .ISO was corrupt I booted up into Windows Vista and went to get Dolphin-emu installed on their site. There download links weren't posted in their downloads section - so I compiled Dolphin for Windows - which was a huge pain that required me to download at least 750MB of software and compiling took around 15x longer than what it did on Ubuntu - and I'm not kidding or exaggerating.
After I got it working, I added the Wii .ISO (Super Mario Bros. Wii - which is supported by Dolphin-emu). The game played - although slighty choppy. 

The only difference was that on Ubuntu Dolphin-emu was using OpenGL, Windows Dolphin-Emu was using DirectX10.

So, thinking maybe it was a graphics card issue (maybe OpenGL2.1 wasn't supported completely) I checked nVidia's website and found out that wasn't the issue.

So now, does anybody have any tips or insight on to why the emulator doesn't emulate Wii games?

Thanks, and sorry for the long post!

---

### Post by del_diablo on 2010-11-03
My guess is that its a regression on the emulator side.
Nvidia got eqaully good drivers on both platforms, so its not the GPU that is the problem. 
And wow, you actually compiled under Windows? Too much free time? I do not envy the experience.

---

### Post by JustinR on 2010-11-03
> **del_diablo said:**
> My guess is that its a regression on the emulator side.
Nvidia got eqaully good drivers on both platforms, so its not the GPU that is the problem. 
And wow, you actually compiled under Windows? Too much free time? I do not envy the experience.

Yeah that makes sense - I checked Dolphin's SVN issues page and even many windows users are having DirectX regressions. I wonder when it all will be ironed out!

And yes DirectX SDK was 587MB and Visual C++ Studio 2008 Express was another 150MB - compiling didn't seem to end!

---

