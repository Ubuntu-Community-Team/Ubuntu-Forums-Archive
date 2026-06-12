---
title: "Game errors! Some games work, others don't!"
date: 2011-03-28
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2011-03-28
Hi.

I noticed today that some games work while other wont. Nikwi Deluxe, Pingus, SuperTux 2, etc. work fine but these don't:

```
$ sdl-ball 
SDL-Ball v 1.01
Segmentation fault
```

```
$ supertuxkart 
Irrlicht Engine version 1.7.2
Linux 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686
[FileManager] Data files will be fetched from: '/usr/share/games/supertuxkart/'
[IrrDriver] Creating NULL device
Irrlicht Engine version 1.7.2
Linux 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686
[IrrDriver] Trying OpenGL rendering.
[IrrDriver] Tring to create device with 32 bits
Segmentation fault
```

```
$ zero-ballistics
User data directory is "/home/roy/.config/QuantiCode/Zero Ballistics/"

--------------------------------------------------------------------------------
28.3.2011, 16:30:2 : log session started
Build Dec 18 2010 - 19:31:07
Debug classes: -
Version z2.00
Vendor: NVIDIA Corporation
Renderer: GeForce 7600 GT/PCI/SSE2
GL Version: 2.1.2 NVIDIA 260.19.06
Max. Texture Units: 16
Max. Varying Floats: 32
Max. Vertex Attribs: 16
Max. Uniforms in VS: 1024
Max. Uniforms in FS: 2048
GLSL language version: 1.20 NVIDIA via Cg compiler
Shader Model: 3

ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Unknown field hint
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Unknown field hint
AL lib: alsa.c:344: Could not open playback device 'hw:0,0': Invalid argument
Game Server started, listening on port 23500 for 5 connections max.
0d0h0m5.6058 Loading bs_almrausch (Beaconstrike)
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning :  Unable to load Waypoint map for level: data/levels/bs_almrausch/waypoints.bin
 Error: Couldn't read from file data/levels/bs_almrausch/waypoints.bin  Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
connection request accepted from 127.0.0.1:23500
We are connected to 127.0.0.1:23500 and have IP 127.0.0.1:33091
Server is running version z2.00
0d0h0m6.7994 A new player connected: 127.0.0.1:33091. Number of players: 1
127.0.0.1:33091 has version z2.00
Roy auth data set to 0; 0
New player has name Roy
MSG: A base has been conquered.
MSG: Press 'h' for help.
MSG: You have been assigned to Attacker.
MSG: Game commencing...
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
        Warning : element Shape is missing attribute "mass_only".
Segmentation fault
```

Segmentation fault seems to be the common denominator. I presume there are more games that aren't working that I've yet to discover. Solutions anyone?

Thanks.

---

### Post by Arthur_D on 2011-03-28
Hm, I can't think of something right now. Making a debug build of one of the failing programs might help with finding the actual cause. This should work fine, though something could be wrong with the card/driver combo. Anyone else? :confused:
Renderer: GeForce 7600 GT/PCI/SSE2
GL Version: 2.1.2 NVIDIA 260.19.06

---

