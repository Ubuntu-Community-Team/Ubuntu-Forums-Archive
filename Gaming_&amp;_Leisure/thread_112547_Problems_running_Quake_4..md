---
title: "Problems running Quake 4."
date: 2006-01-04
forum: Gaming &amp; Leisure
---

### Post by Stork on 2006-01-04
Well I installed quake4 according to the tutorial, but when trying to run it I get this error.

Here's my error:
alex@main:~/quake4$ ./quake4
./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

Any ideas? I'd hate to have to move back to windows :(


Note: I'm using 64-bit ubuntu.

---

### Post by Lord Illidan on 2006-01-04
Enable the repos as per this site : [Ubuntu Wiki (community-edited website)]("http://www.ubuntulinux.org/wiki/FrontPage")

And use synaptic to install SDL. (search for sdl)

---

### Post by Stork on 2006-01-04
[QUOTE=Lord Illidan]Enable the repos as per this site : [Ubuntu Wiki (community-edited website)]("http://www.ubuntulinux.org/wiki/FrontPage")

And use synaptic to install SDL. (search for sdl)[/QUOTE]
Ok, got that working, only to find more, scarier, errors:

```
alex@main:~/quake4$ sudo ./quake4
Quake4 Final V1.0.6.0 Build 2147.12 linux-x86 Dec 12 2005
found interface lo - loopback
found interface eth0 - 192.168.0.12/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/alex/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /home/alex/quake4/q4base/game100.pk4 with checksum 0x6f346a2
Loaded pk4 /home/alex/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8bLoaded pk4 /home/alex/quake4/q4base/zpak_french_01.pk4 with checksum 0xe909853f
Loaded pk4 /home/alex/quake4/q4base/zpak_italian_01.pk4 with checksum 0xef0e1696Loaded pk4 /home/alex/quake4/q4base/zpak_spanish_01.pk4 with checksum 0xe829a04aCurrent search path:
/home/alex/.quake4/q4base
/home/alex/quake4/q4base
/home/alex/quake4/q4base/zpak_spanish_01.pk4 (2 files)
/home/alex/quake4/q4base/zpak_italian_01.pk4 (2 files)
/home/alex/quake4/q4base/zpak_french_01.pk4 (2 files)
/home/alex/quake4/q4base/zpak_english_01.pk4 (1 files)
/home/alex/quake4/q4base/game100.pk4 (2 files)
/home/alex/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
TODO: Sys_SetClipboardData
********************
ERROR: Couldn't load default.cfg  -  Check your working folder.
********************
Unknown command 'vid_restart'
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg  -  Check your working folder.
```

---

### Post by Stork on 2006-01-05
```
alex@main:/usr/local/games/quake4$ ./quake4
Quake4 Final V1.0.6.0 Build 2147.12 linux-x86 Dec 12 2005
found interface lo - loopback
found interface eth0 - 192.168.0.12/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
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
/home/alex/.quake4/q4base
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
235ms to load 1071k of material
115ms to load 43k of skin
153ms to load 716k of sound
26ms to load 1k of materialType
303ms to load 2078k of lipSync
90ms to load 105k of playback
1033ms to load 1665k of effect
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
```
New error ^^ :|

---

### Post by Lord Illidan on 2006-01-05
Do you have the drivers for your graphics card?

---

### Post by Stork on 2006-01-05
[QUOTE=Lord Illidan]Do you have the drivers for your graphics card?[/QUOTE]
Indeed, I do.

---

### Post by Zeroedout on 2006-01-05
are you 100% sure you installed the graphics drivers? Run glxgears and make sure it's all working smooth, otherwise, the only time I get those errors are when my computer is too hot. Try running the game when you first bootup. If not, it's most likely the graphics drivers. Also what vidcard? Since it's 64 bit ubuntu, did you also try running the game in a 32bit environment?

---

### Post by Stork on 2006-01-05
[QUOTE=Zeroedout]are you 100% sure you installed the graphics drivers? Run glxgears and make sure it's all working smooth, otherwise, the only time I get those errors are when my computer is too hot. Try running the game when you first bootup. If not, it's most likely the graphics drivers. Also what vidcard? Since it's 64 bit ubuntu, did you also try running the game in a 32bit environment?[/QUOTE]
Glxgears works fine. How could I run the game in a 32bit environment?

---

