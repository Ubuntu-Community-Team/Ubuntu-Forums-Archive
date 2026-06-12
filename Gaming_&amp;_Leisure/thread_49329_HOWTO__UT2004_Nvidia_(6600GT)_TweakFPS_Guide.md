---
title: "HOWTO:  UT2004 Nvidia (6600GT) Tweak/FPS Guide"
date: 2005-07-15
forum: Gaming &amp; Leisure
---

### Post by evilghost on 2005-07-15
While I am not new to Linux, I am quite new to the Ubuntu/Debian world and Linux as a desktop solution.  I'm an avid UT2004 gamer and have been knocking my head against the wall for the last few weeks in an attempt to eek every bit of performance out of my 6600GT card.  I will attempt to provide key pieces of information and settings that have dramatically increased my UT2004 performance making it quite playable (Read as, AVG 60FPS and above).  This document will be written from the aspect of someone familiar with xorg.conf modifications, driver installation, and how to edit files.  There are many additional forum posts that describe these operations in detail if you don't know how to do it.

**First:**
Install the latest NVidia drivers from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)  At the time of this post, 7667 are the current drivers.  Search these forums for method required to install/compile these drivers.  In all honesty, it's not very difficult.

**Second:**
After successfully installing the drivers, make the following changes to /etc/X11/xorg.conf.  Change any values that are specific to your card.  Note that your xorg.conf should be larger than the below text, these are simply snippets from my xorg.conf.  These values were derivied after hours of testing performance and changing one item at a time, coupled with research :)

```

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        #Load   "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "NV6600GT"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoDCC"
        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"         "off"
        Option          "UseInternalAGPGART"    "no"
        Option          "NvAGP"                 "3"
        Option          "RenderAccel"           "true"
        Option          "Coolbits"              "1"
        Option          "NoLogo"
        VideoRam        131072
EndSection

```

In this case, I own a 6600GT with 128MB of ram.  If your card is different be sure to adjust the VideoRam declaration.

**Third:**
Read and apply the changes documented in [http://www.ubuntuforums.org/showthread.php?t=40069](http://www.ubuntuforums.org/showthread.php?t=40069)

**Fourth:**
Modify ~/.ut2004/System/UT2004.ini to look like this, note these are **snippets**, not the entire UT2004.ini.

```

[Engine.GameEngine]
CacheSizeMegs=512

[OpenGLDrv.OpenGLRenderDevice]
DetailTextures=True
HighDetailActors=False
SuperHighDetailActors=False
UsePrecaching=True
UseCompressedLightmaps=True
UseTrilinear=False
UseStencil=False
MaxTextureUnits=8
VARSize=64
ReduceMouseLag=False
UseVSync=False
LevelOfAnisotropy=0.000000
DetailTexMipBias=0.000000
DefaultTexMipBias=-0.5
UseVBO=False
UseVSync=False
AppleVA=0
MultisampleBuffers=0
MultisampleSamples=0
MultisampleHint=2
UsePixelShaders=True
DesiredRefreshRate=0
ForceCompression=True
TerrainLOD=0
SkyboxHack=False
LowQualityTerrain=False
Use16bitTextures=False
Use16bit=False

```

**Fifth**:
Reboot, hopefully everything should work great.  You can additionally use the CoolBits tab on the "nvidia-settings" application to overclock the card.  Note however that upon reboot clock settings are lost.  You can however issue command-line arguments to nvidia-settings.  I wrote a simple script that will overclock the card.  It is not advised that you use my clock settings, as your card may not support them, however, you can use the script as a base-line and apply changes specific to your card.

```

#!/bin/sh
nvidia-settings -a GPUOverclockingState=1 -a GPU3DClockFreqs=571,1044

```

Where 571Mhz is the core frequency and 1044Mhz is the memory frequency.

**Sixth:**
Link the libSDL in the UT2004 installation folder to your system compiled libSDL.
```

mv libSDL-1.2.so.0 libSDL-1.2.so.0-UT2004
ln -s /usr/lib/libSDL-1.2.so.0 libSDL-1.2.so.0

```

**Seventh:**
If you have a SoundBlaster Live or SoundBlaster Audigy, see [http://ubuntuforums.org/showthread.php?p=257782](http://ubuntuforums.org/showthread.php?p=257782)

By recompiling OpenAL you can gain 10 to 20fps.

**Conclusion**:
I hope this helped, and please feel free to contribute to this thread-topic.  I will continue to update this "HOWTO" should additional clarification be needed or any questions are raised.  There may be parts of the configuration that may have adverse affects on cards that are not a 6600GT, however, it couldn't hurt to try.  Be sure to "stat fps" in UT2004's console to view your current FPS rate.

---

### Post by evilghost on 2005-07-15
Sorry to reply to my own post, I am doing so to show my signature so one can have room for comparison on hardware spec, as well as so I can subscribe to this thread and receive email-alerts should anyone post.

Here are some benchmark results runniing at 571Mhz Core, 1044Mhz Memory (OC'd via CoolBits).

```

luser@400sc:~$ fgl_glxgears
7086 frames in 5.0 seconds = 1417.200 FPS
8499 frames in 5.0 seconds = 1699.800 FPS
8518 frames in 5.0 seconds = 1703.600 FPS
8496 frames in 5.0 seconds = 1699.200 FPS
8503 frames in 5.0 seconds = 1700.600 FPS
8442 frames in 5.0 seconds = 1688.400 FPS

luser@400sc:~$ glxgears
35786 frames in 5.0 seconds = 7157.200 FPS
38202 frames in 5.0 seconds = 7640.400 FPS
38176 frames in 5.0 seconds = 7635.200 FPS
38214 frames in 5.0 seconds = 7642.800 FPS
38195 frames in 5.0 seconds = 7639.000 FPS

luser@400sc:~$

```

---

### Post by sol77 on 2005-07-16
Nice. I will have to try this out soon.

---

### Post by evilghost on 2005-07-16
For an additional increase in performance, disable Projectors, Dynamic Lights, and Corona's.  When I'm gaming and it's fast-paced I hardly notice the difference in detail.

Doing a "playdemo utbench?timedemo" (see [http://www.ataricommunity.com/forums/showthread.php?threadid=372370&perpage=30&highlight=Benchmark&pagenumber=1](http://www.ataricommunity.com/forums/showthread.php?threadid=372370&perpage=30&highlight=Benchmark&pagenumber=1)) I am getting:

36.515 FPS with a libSDL I compiled, the system libSDL gave me 35.264 FPS.

Using the recompiled openal.so for the Sound Blaster Live/Audigy cards gave me an increase of 36.254fps from 35.909.

Disabling RenderAccel gave me an increase of 36.245 from 35.924

Running with no sound (ie, openal.so moved/renamed) gives a score of 38.626 FPS.  For some odd reason, it appears sound is still stealing framerate.  I don't know if this is normal or abnormal.

No Projectors:  36.515 FPS
No Dynamic Lights/Coronas:  38.593 FPS

Hopefully this will help someone out.

My brother-in-law has the exact same system I have, memory, CPU, HDD, except he has a Built-By-ATI Radeon 9800 PRO oc'd to 9800 XT.  He is running Windows XP SP2 while I am running Ubuntu 5.04.  Running at 1024x768 with all settings Normal and Blob shadows he pulls 33.346 FPS, while I pull 32.670 FPS.  He's Direct3D and I'm using the OpenGL rendering path.  **Very** close in performance.

---

### Post by rutty on 2005-07-19
I have one of these cards too and implemented the xorg.conf changes you suggest. I have no idea what half of them do, but now my World of Warcraft plays MUCH smoother - thanks!

---

### Post by evilghost on 2005-07-19
[QUOTE=rutty]I have one of these cards too and implemented the xorg.conf changes you suggest. I have no idea what half of them do, but now my World of Warcraft plays MUCH smoother - thanks![/QUOTE]

Nice, and you're welcome.  Be sure to do the following steps, if you haven't, and you should see some great framerates:

Steps 1, 2, 3, and 5.

---

