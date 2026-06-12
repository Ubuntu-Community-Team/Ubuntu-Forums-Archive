---
title: "Quake4 Seg fault"
date: 2005-11-26
forum: Gaming &amp; Leisure
---

### Post by ratty on 2005-11-26
Hi, i'm attempting to run quake4 on ubuntu 5.10 on an AMD64 with an ati radeon x800 using fglrx, after sorting out the SDL stuff i get a seg fault, here's my output:

```

Quake4 Final V1.0.5.0 Build 2147.0 linux-x86 Nov 14 2005
found interface lo - loopback
found interface eth0 - 192.168.0.100/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2
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
/home/ratty/.quake4/q4base
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
222ms to load 1071k of material
90ms to load 43k of skin
147ms to load 716k of sound
21ms to load 1k of materialType
254ms to load 2078k of lipSync
75ms to load 105k of playback
957ms to load 1665k of effect
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
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
dlopen(libasound.so.2)
asoundlib version: 1.0.9
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5461 frames ( 21844 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
X..GL_NV_blend_square not found
X..GL_ARB_texture_compression not found
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..

```

---

