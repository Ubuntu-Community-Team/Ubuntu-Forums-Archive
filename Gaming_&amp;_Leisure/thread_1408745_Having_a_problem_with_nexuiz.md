---
title: "Having a problem with nexuiz"
date: 2010-02-16
forum: Gaming &amp; Leisure
---

### Post by beliyyal on 2010-02-16
Hi guys, I am having a problem with nexuiz. It begins to start, then closes out again. I ran it in terminal, this is what I got:
> 
****@Phantom:~$ nexuiz
Nexuiz Linux 09:18:31 Mar 23 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data20080229.pk3 (3982 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libOffscreenGecko.so" "/usr/lib/games/nexuiz/libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
execing config.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Unable to load GL driver "(null)": No dynamic GL support in video driver
Desired video mode fail, trying fallbacks...
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Unable to load GL driver "(null)": No dynamic GL support in video driver
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Unable to load GL driver "(null)": No dynamic GL support in video driver
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Unable to load GL driver "(null)": No dynamic GL support in video driver
Initializing Video Mode: fullscreen 640x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Unable to load GL driver "(null)": No dynamic GL support in video driver
Initializing Video Mode: fullscreen 640x480x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Unable to load GL driver "(null)": No dynamic GL support in video driver
Initializing Video Mode: fullscreen 640x480x16x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.13
Unable to load GL driver "(null)": No dynamic GL support in video driver
Quake Error: Video modes failed

The thing is, I can run alien arena, torcs, wolfenstein: enemy territory, and a few other 3D games, but not nexuiz, tremulous, and open arena. And this is what I get when I run glxgears:
> 1548 frames in 5.0 seconds = 309.427 FPS
1527 frames in 5.0 seconds = 305.318 FPS
1560 frames in 5.0 seconds = 311.893 FPS
1559 frames in 5.0 seconds = 311.723 FPS
1564 frames in 5.0 seconds = 312.640 FPS
1560 frames in 5.0 seconds = 311.864 FPS
1476 frames in 5.0 seconds = 295.049 FPS

Can someone please help me out?

---

### Post by Chesnut on 2010-02-17
Well, I'm no expert, but
```
Unable to load GL driver "(null)": No dynamic GL support in video driver
```
seems to say that it's about your video driver? Maybe try updating it?

---

### Post by tommcd on 2010-02-17
Here is the relevant problem I think:
```
Trying to load library... "libOffscreenGecko.so" "/usr/lib/games/nexuiz/libOffscreenGecko.so" - failed.
```
To troubleshoot this you should tell us:
1. What video card do you have?
2. If your video card is ati or nvidia, do you have the proper driver installed?
This thread from the Nexuiz forums confirms that this issue can be fixed by installing the proper driver:
[http://www.alientrap.org/forum/viewtopic.php?f=3&t=5767](http://www.alientrap.org/forum/viewtopic.php?f=3&t=5767)
Your FPS from glxgears are pretty low to be running a 3D game like Nexuiz.
To see if direct rendering is enabled, run this:
```
 glxinfo | grep -i direct 
```
It should report: direct rendering: Yes

---

