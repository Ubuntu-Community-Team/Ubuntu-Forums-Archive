---
title: "Quake 4 crash"
date: 2005-11-23
forum: Gaming &amp; Leisure
---

### Post by Xyxex on 2005-11-23
I have an ATI-radeon card(9600 XT). I have installed the radeon-drivers.  I also installed the ibsdl1.2debian-alsa.

Well, when i type "quake4" in the terminal i got this error:

root@Flamman:/usr/local/games/quake4# quake4
Quake4 Final V1.0.5.0 Build 2147.0 linux-x86 Nov 14 2005
found interface lo - loopback
found interface eth0 - 85.194.56.64/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x6f346a2
Loaded pk4 /usr/local/games/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /usr/local/games/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /usr/local/games/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /usr/local/games/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /usr/local/games/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /usr/local/games/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /usr/local/games/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /usr/local/games/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /usr/local/games/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /usr/local/games/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /usr/local/games/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /usr/local/games/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french_01.pk4 with checksum 0xe909853f
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian_01.pk4 with checksum 0xef0e1696
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish_01.pk4 with checksum 0xe829a04a
Current search path:
/home/speedy/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_spanish_01.pk4 (2 files)
/usr/local/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/usr/local/games/quake4/q4base/zpak_italian_01.pk4 (2 files)
/usr/local/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/usr/local/games/quake4/q4base/zpak_french_01.pk4 (2 files)
/usr/local/games/quake4/q4base/zpak_french.pk4 (3462 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
/usr/local/games/quake4/q4base/pak012.pk4 (1081 files)
/usr/local/games/quake4/q4base/pak011.pk4 (5620 files)
/usr/local/games/quake4/q4base/pak010.pk4 (5539 files)
/usr/local/games/quake4/q4base/pak009.pk4 (1284 files)
/usr/local/games/quake4/q4base/pak008.pk4 (1289 files)
/usr/local/games/quake4/q4base/pak007.pk4 (1330 files)
/usr/local/games/quake4/q4base/pak006.pk4 (1343 files)
/usr/local/games/quake4/q4base/pak005.pk4 (1395 files)
/usr/local/games/quake4/q4base/pak004.pk4 (2249 files)
/usr/local/games/quake4/q4base/pak003.pk4 (1281 files)
/usr/local/games/quake4/q4base/pak002.pk4 (313 files)
/usr/local/games/quake4/q4base/pak001.pk4 (5837 files)
/usr/local/games/quake4/q4base/game100.pk4 (2 files)
/usr/local/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 59 loaded
286ms to load 1071k of material
97ms to load 43k of skin
193ms to load 716k of sound
23ms to load 1k of materialType
333ms to load 2078k of lipSync
89ms to load 105k of playback
1214ms to load 1665k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
641 strings read from strings/english_code.lang
1663 strings read from strings/english_guis.lang
5625 strings read from strings/english_lips.lang
6094 strings read from strings/english_maps.lang
641 strings read from strings/french_code.lang
1663 strings read from strings/french_guis.lang
5625 strings read from strings/french_lips.lang
6094 strings read from strings/french_maps.lang
641 strings read from strings/italian_code.lang
1663 strings read from strings/italian_guis.lang
5625 strings read from strings/italian_lips.lang
6094 strings read from strings/italian_maps.lang
641 strings read from strings/spanish_code.lang
1663 strings read from strings/spanish_guis.lang
5625 strings read from strings/spanish_lips.lang
6094 strings read from strings/spanish_maps.lang
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


Plss help me! :(

---

### Post by djselbeck on 2005-11-24
Hello,

can you please post the output of this command?

```
glxinfo |grep direct
```

DJSelbeck

---

### Post by Xyxex on 2005-11-24
speedy@Flamman:~$ glxinfo |grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by djselbeck on 2005-11-26
Hello,

it seems that your Graficcard is not accelerated. please check your xorg.conf or post it here. 

cat /etc/X11/xorg.conf

DJSelbeck

---

### Post by barfos on 2005-12-24
Hello, I am getting the same error, when i run the glxinfo thing, i get 

direct rendering: Yes

as the answer.

This page (the doomIII faq)
[http://zerowing.idsoftware.com/linux/doom/Doom3FrontPage?action=show&redirect=FrontPage#head-37a70860392f09490de7dde78bea00dba55c707a](http://zerowing.idsoftware.com/linux/doom/Doom3FrontPage?action=show&redirect=FrontPage#head-37a70860392f09490de7dde78bea00dba55c707a)
says that you need to be running a 24bpp desktop.  When I run glxinfo, my output doesn't match theirs, so i will now attempt to change my desktop's bpp.  Somehow...

barfos

---

### Post by barfos on 2005-12-24
Got it.  To switch to 24bpp desktop as per that faq, you need to edit the xorg.conf.  See my recent post over [here]("http://ubuntuforums.org/showthread.php?t=107837") in order to see details.


Hope this helps someone!
barfos

---

