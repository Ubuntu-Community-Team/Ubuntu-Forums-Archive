---
title: "Quake4 Demo install ?"
date: 2006-07-01
forum: Gaming &amp; Leisure
---

### Post by Drakkor on 2006-07-01
Installed the quake4-linux 1.0-demo.x86.run file,and got this, any ideas to fix? 
Thanks
drakkor@drakkor:~$ cd Desktop
drakkor@drakkor:~/Desktop$ sudo sh quake4-linux-1.0-demo.x86.run
Verifying archive integrity... All good.
Uncompressing Quake 4 (TM) demo.................................................................................
Removing existing quake4-demo symlink
Installing symlink /usr/local/bin/quake4-demo -> /usr/local/games/quake4-demo/quake4-demo
Removing existing quake4-demoded symlink
Installing symlink /usr/local/bin/quake4-demoded -> /usr/local/games/quake4-demo/quake4-demoded
Quake4 Demo Final V1.0.0 linux-x86 Nov 28 2005
found interface lo - loopback
found interface eth1 - 67.172.184.61/255.255.248.0
CPU: Intel CPU with MMX & SSE & SSE2
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4-demo/q4base/game000.pk4 with checksum 0xc01bb9a0
Loaded pk4 /usr/local/games/quake4-demo/q4base/game100.pk4 with checksum 0xe71d2aa2
Loaded pk4 /usr/local/games/quake4-demo/q4base/pak001.pk4 with checksum 0x4a4195c2
Loaded pk4 /usr/local/games/quake4-demo/q4base/zpak_english.pk4 with checksum 0xab62ab5e
Loaded pk4 /usr/local/games/quake4-demo/q4base/zpak_french.pk4 with checksum 0x88c09a6b
Loaded pk4 /usr/local/games/quake4-demo/q4base/zpak_italian.pk4 with checksum 0xb7cf593a
Loaded pk4 /usr/local/games/quake4-demo/q4base/zpak_spanish.pk4 with checksum 0x1dec3532
Current search path:
/home/drakkor/.quake4-demo/q4base
/usr/local/games/quake4-demo/q4base
/usr/local/games/quake4-demo/q4base/zpak_spanish.pk4 (864 files)
/usr/local/games/quake4-demo/q4base/zpak_italian.pk4 (822 files)
/usr/local/games/quake4-demo/q4base/zpak_french.pk4 (784 files)
/usr/local/games/quake4-demo/q4base/zpak_english.pk4 (779 files)
/usr/local/games/quake4-demo/q4base/pak001.pk4 (7663 files)
/usr/local/games/quake4-demo/q4base/game100.pk4 (2 files)
/usr/local/games/quake4-demo/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------

Running in restricted demo mode.

------------ Initializing Decls -------------
Loading guides.... 59 loaded
362ms to load 1064k of material
63ms to load 43k of skin
238ms to load 719k of sound
2ms to load 1k of materialType
417ms to load 2078k of lipSync
92ms to load 105k of playback
1216ms to load 1666k of effect
---------------------------------------------
/proc/cpuinfo CPU frequency: 2009.14 MHz
detecting video ram ( set sys_videoRam to force ) ..
guess failed, return default low-end VRAM setting ( 64MB VRAM )
Detected
        2.01 GHz CPU
        496 MB of System memory
        64 MB of Video memory on an optimal video architecture

This system qualifies for Low quality.
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
641 strings read from strings/english_code.lang
1669 strings read from strings/english_guis.lang
5631 strings read from strings/english_lips.lang
6100 strings read from strings/english_maps.lang
641 strings read from strings/french_code.lang
1668 strings read from strings/french_guis.lang
5630 strings read from strings/french_lips.lang
6099 strings read from strings/french_maps.lang
641 strings read from strings/italian_code.lang
1668 strings read from strings/italian_guis.lang
5630 strings read from strings/italian_lips.lang
6099 strings read from strings/italian_maps.lang
641 strings read from strings/spanish_code.lang
1668 strings read from strings/spanish_guis.lang
5630 strings read from strings/spanish_lips.lang
6099 strings read from strings/spanish_maps.lang
Couldn't open journal files
execing default.cfg
"ALT" isn't a valid key
"CTRL" isn't a valid key
couldn't exec editor.cfg
couldn't exec Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
TODO: Sys_SetClipboardData
********************
ERROR: SDL_SetVideoMode failed: Couldn't find matching GLX visual
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: SDL_SetVideoMode failed: Couldn't find matching GLX visual
drakkor@drakkor:~/Desktop$

---

### Post by KenSentMe on 2006-07-01
Is your videocard configured well? Have you played other 3d games yet? If not, maybe you should look at this page:

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by Drakkor on 2006-07-02
Thanks,KenSentMe, got it working ! :p

---

