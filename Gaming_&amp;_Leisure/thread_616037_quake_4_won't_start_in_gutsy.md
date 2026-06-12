---
title: "quake 4 won't start in gutsy"
date: 2007-11-17
forum: Gaming &amp; Leisure
---

### Post by me208 on 2007-11-17
Help!! I installed the quake 4 demo and it ran fine so I went out and bought the full game and installed it following  [this](http://zerowing.idsoftware.com/linux/quake4/) guide. Whenever I try to start either the full game or the demo I get this:
```
daniel@ubuntu:~$ quake4
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface eth0 - 192.168.1.101/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /usr/local/games/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /usr/local/games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /usr/local/games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
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
Loaded pk4 /usr/local/games/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /usr/local/games/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /usr/local/games/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /usr/local/games/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /usr/local/games/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /usr/local/games/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /usr/local/games/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /usr/local/games/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /usr/local/games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /usr/local/games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /usr/local/games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Addon pk4 /usr/local/games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/daniel/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/usr/local/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/usr/local/games/quake4/q4base/zpak_french.pk4 (3462 files)
/usr/local/games/quake4/q4base/zpak_english_04.pk4 (3 files)
/usr/local/games/quake4/q4base/zpak_english_03.pk4 (4 files)
/usr/local/games/quake4/q4base/zpak_english_02.pk4 (21 files)
/usr/local/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/usr/local/games/quake4/q4base/zpak_english.pk4 (3457 files)
/usr/local/games/quake4/q4base/pak022.pk4 (14 files)
/usr/local/games/quake4/q4base/pak021.pk4 (89 files)
/usr/local/games/quake4/q4base/pak020.pk4 (11 files)
/usr/local/games/quake4/q4base/pak019.pk4 (1206 files)
/usr/local/games/quake4/q4base/pak018.pk4 (3 files)
/usr/local/games/quake4/q4base/pak017.pk4 (3 files)
/usr/local/games/quake4/q4base/pak016.pk4 (193 files)
/usr/local/games/quake4/q4base/pak015.pk4 (34 files)
/usr/local/games/quake4/q4base/pak014.pk4 (552 files)
/usr/local/games/quake4/q4base/pak013.pk4 (239 files)
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
/usr/local/games/quake4/q4base/game200.pk4 (9 files)
/usr/local/games/quake4/q4base/game100.pk4 (2 files)
/usr/local/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
/usr/local/games/quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 64 loaded
327ms to load 1125k of material
103ms to load 43k of skin
231ms to load 723k of sound
6ms to load 1k of materialType
469ms to load 2889k of lipSync
80ms to load 105k of playback
1096ms to load 1690k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
696 strings read from strings/english_code.lang
1794 strings read from strings/english_guis.lang
5756 strings read from strings/english_lips.lang
5759 strings read from strings/english_mappack.lang
6235 strings read from strings/english_maps.lang
632 strings read from strings/french_code.lang
1654 strings read from strings/french_guis.lang
5616 strings read from strings/french_lips.lang
5619 strings read from strings/french_mappack.lang
6088 strings read from strings/french_maps.lang
632 strings read from strings/italian_code.lang
1654 strings read from strings/italian_guis.lang
5616 strings read from strings/italian_lips.lang
5619 strings read from strings/italian_mappack.lang
6088 strings read from strings/italian_maps.lang
632 strings read from strings/spanish_code.lang
1654 strings read from strings/spanish_guis.lang
5616 strings read from strings/spanish_lips.lang
5619 strings read from strings/spanish_mappack.lang
6088 strings read from strings/spanish_maps.lang
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
SDL_ListModes:
1280x1024 SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
1 pixels multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.14a
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
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
Fatal Error: Texture compression unavailable
Shutting down SDL subsystem
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Texture compression unavailable

```

Please Help :confused:

---

