---
title: "eduke on 64-bit Ubuntu"
date: 2007-11-30
forum: Gaming &amp; Leisure
---

### Post by Dark Aspect on 2007-11-30
Is it possible to play eduke on a 64-bit Linux OS.I downloaded the files from [here]("http://hrp.duke4.net/download.php") for Debian and ran the files under getlibs.After manually placing several 32-bit libs in my lib32 folder I finally received this error which is the same one I received on 32-bit Ubuntu last time I tried to run eduke:

> EDuke32 1.4.0 svn (Jun 14 2007 12:39:01)
Copyright (c) 1996, 2003 3D Realms Entertainment
Copyright (c) 2007 EDuke32 team
addsearchpath(): Added /usr/share/games/eduke32/
addsearchpath(): Added /usr/share/games/eduke32/
addsearchpath(): Added /home/administrator/.eduke32/
Would you like to enable the on-disk texture cache? This feature will use an undetermined amount of space on your hard disk to store textures in your video card's native format, enabling them to load dramatically faster after the first time they are loaded.

You will generally want to say 'yes' here, especially if using the HRP.
   (type 'Y' or 'N', and press Return or Enter to continue)
y
Initialising SDL system interface (compiled with SDL version 1.2.11, DLL version 1.2.11)
Loading libGL.so
Failed loading OpenGL driver. GL modes will be unavailable.
Using "x11" video driver
Video device information:
  Can create hardware surfaces?          No
  Window manager available?              Yes
  Accelerated hardware blits?            No
  Accelerated hardware colourkey blits?  No
  Accelerated hardware alpha blits?      No
  Accelerated software blits?            No
  Accelerated software colourkey blits?  No
  Accelerated software alpha blits?      No
  Accelerated colour fills?              No
  Total video memory:                    0KB
Detecting video modes:
No fullscreen modes available!
  - 1280x1024 8-bit windowed
  - 1280x960 8-bit windowed
  - 1152x864 8-bit windowed
  - 1024x768 8-bit windowed
  - 800x600 8-bit windowed
  - 640x480 8-bit windowed
  - 640x400 8-bit windowed
  - 512x384 8-bit windowed
  - 480x360 8-bit windowed
  - 400x300 8-bit windowed
  - 320x240 8-bit windowed
  - 320x200 8-bit windowed
Using config file 'duke3d.cfg'.
Scanning for GRP files...

The game thinks I have no video memory which in reality I have my 3D video Acceleration enabled with a half way nice video card.I am currently running Duke Nukem 3D though dosemu with sound but no music.Dosbos is too slow,I have the atomic version of duke nukem..Any ideas?

Actually I found [this wiki howto for linux]("http://hrp.duke4.net/wiki/doku.php?id=documentation:installing_running_the_hrp_and_ports&s=linux") so I am going to try and install the other Linux package for eduke.

---

### Post by Dark Aspect on 2007-11-30
Ok eduke does not work with Ubuntu 64-bit.......I followed [this howto]("http://hrp.duke4.net/wiki/doku.php?id=documentation:installing_running_the_hrp_and_ports&s=linux") exactly and it does not work.eduke even sees my grp file but refuses to boot,heres a look at the new terminal output:

> Would you like to enable the on-disk texture cache? This feature will use an undetermined amount of space on your hard disk to store textures in your video card's native format, enabling them to load dramatically faster after the first time they are loaded.

You will generally want to say 'yes' here, especially if using the HRP.
   (type 'Y' or 'N', and press Return or Enter to continue)
y
Initialising SDL system interface (compiled with SDL version 1.2.11, DLL version 1.2.11)
Loading libGL.so
Loading libGLU.so
Using "x11" video driver
Video device information:
  Can create hardware surfaces?          No
  Window manager available?              Yes
  Accelerated hardware blits?            No
  Accelerated hardware colourkey blits?  No
  Accelerated hardware alpha blits?      No
  Accelerated software blits?            No
  Accelerated software colourkey blits?  No
  Accelerated software alpha blits?      No
  Accelerated colour fills?              No
  Total video memory:                    0KB
Detecting video modes:
  - 1280x1024 32-bit fullscreen
  - 1280x960 32-bit fullscreen
  - 1280x800 32-bit fullscreen
  - 1280x768 32-bit fullscreen
  - 1152x864 32-bit fullscreen
  - 1024x768 32-bit fullscreen
  - 960x600 32-bit fullscreen
  - 840x525 32-bit fullscreen
  - 832x624 32-bit fullscreen
  - 800x600 32-bit fullscreen
  - 800x512 32-bit fullscreen
  - 720x450 32-bit fullscreen
  - 640x512 32-bit fullscreen
  - 640x480 32-bit fullscreen
  - 640x400 32-bit fullscreen
  - 640x384 32-bit fullscreen
  - 576x432 32-bit fullscreen
  - 512x384 32-bit fullscreen
  - 416x312 32-bit fullscreen
  - 400x300 32-bit fullscreen
  - 320x240 32-bit fullscreen
  - 1152x864 8-bit windowed
  - 1024x768 8-bit windowed
  - 800x600 8-bit windowed
  - 640x480 8-bit windowed
  - 640x400 8-bit windowed
  - 512x384 8-bit windowed
  - 480x360 8-bit windowed
  - 400x300 8-bit windowed
  - 320x240 8-bit windowed
  - 320x200 8-bit windowed
  - 1152x864 32-bit windowed
  - 1024x768 32-bit windowed
  - 800x600 32-bit windowed
  - 640x480 32-bit windowed
  - 640x400 32-bit windowed
  - 512x384 32-bit windowed
  - 480x360 32-bit windowed
  - 400x300 32-bit windowed
  - 320x240 32-bit windowed
  - 320x200 32-bit windowed
Using config file 'duke3d.cfg'.
Scanning for GRP files...
 Checksumming duke3d.grp... Done


---

