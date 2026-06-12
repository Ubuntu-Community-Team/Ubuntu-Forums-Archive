---
title: "Fail to run Psychonauts (from Humble Bundle)"
date: 2013-05-17
forum: Gaming &amp; Leisure
---

### Post by Rhemat on 2013-05-17
Heya All,

  I just got the Psychonauts game from the Humble Indie Bundle, and installed it, however, it fails to run:

```
STUBBED: fix up the rest of the SSE code first at DetectSSESupport (/home/icculus/projects/psychonauts/Source/CommonLibs/DFMath/MathGeneral.cpp:32)
STUBBED: write me? at SetPCLanguage (/home/icculus/projects/psychonauts/Source/game/luatest/UnixMain.cpp:120)
STUBBED: fix up the rest of the SSE code first at DetectCPUCaps (/home/icculus/projects/psychonauts/Source/game/luatest/Game/PCGameApp.cpp:223)
STUBBED: check LANG envr var at _GetDefaultGameLanguage (/home/icculus/projects/psychonauts/Source/game/luatest/Game/GameApp.cpp:171)
Console created
Save  path: /home/fuzzyghost/.local/share/Psychonauts
Write path: WorkResource
STUBBED: inline asm at SSEMul_4x4_4x4_2arg (/home/icculus/projects/psychonauts/Source/CommonLibs/DFMath/Matrix.cpp:710)
STUBBED: inline asm at SSEMul_4x4_4x4_3arg (/home/icculus/projects/psychonauts/Source/CommonLibs/DFMath/Matrix.cpp:698)
******** unit test failed ********
Transport started
DaveD: NCListenSocket: Listening on port 40001
STUBBED: VK_* at InitInputNames (/home/icculus/projects/psychonauts/Source/CommonLibs/DirectX/SDLInput.cpp:1226)
No joysticks detected
ERROR: Missing required OpenGL extensions:
    - GL_EXT_texture_compression_s3tc
Start Up completed in 0.08 seconds
Segmentation fault (core dumped)

```

I'm guessing that the Segmentation fault at the bottom means that my computer is completely unable to run this game?  I may try it on my server later (that has a non nVidia Optimus GPU anyway), otherwise, if you guys have suggestions, I'm all ears.

Thanks in advance.

---

### Post by cRaZyBisCuiT on 2013-05-17
Which Ubuntu version and which kernel do you use? What are your computer specs, especially graphics card and graphics driver?

---

### Post by Rhemat on 2013-05-17
Ubuntu 12.04

Kernel Linux 3.2.0-40-generic-pae

Intel Core i7-2670QM, 2.2GHz

nVidia Optimus 555M (Bumble Bee Drivers)

8GB RAM

Gnome 3.4.2

---

### Post by Perfect Storm on 2013-05-17
You may try checking this: [http://cjenkins.wordpress.com/2013/01/01/steam-for-linux-on-optimus-enabled-computer-running-ubuntu-12-04-64bits/](http://cjenkins.wordpress.com/2013/01/01/steam-for-linux-on-optimus-enabled-computer-running-ubuntu-12-04-64bits/)

> ERROR: Missing required OpenGL extensions:
    - GL_EXT_texture_compression_s3tc

But it may that the Bumblebee driver doesn't support it (yet) or that is bugged.

Or you could try:
```
optirun steam
```

---

### Post by Rhemat on 2013-05-18
I didn't get this game through Steam, I bought it from the Humble Indie Bundle, and got a DRM free, Linux native binary.  Thanks for the reply though, Artificial Intelligence.

I also forgot, I'm using Ubuntu 12.04 32-Bit.

Once again, thanks in advance.

---

### Post by Perfect Storm on 2013-05-18
Though you could try through steam and see if it works through there. It is said that steam also are build working with Bumblebee driver. Just run the **optirun steam** to activate steam with bumblebee driver.
 You can always remove it again if you don't like steam for whatever reason.

---

### Post by Rhemat on 2013-05-18
I've actually already bought the game twice now (XBox 1 version, and the Linux version), and don't like being tied down by DRM.

---

### Post by Rhemat on 2013-06-13
I was able to get Psychonauts to work, by typing [force_s3tc_enable=true ./Psychonauts].  However, the BumbleBee drivers are not up to the task for this game.  I installed the game on my server, and it works better, but still kind of sluggish.

---

