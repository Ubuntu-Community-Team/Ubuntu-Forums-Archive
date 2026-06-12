---
title: "quake 4 in chroot problem"
date: 2005-10-29
forum: Gaming &amp; Leisure
---

### Post by negatory on 2005-10-29
I've installed quake 4 in my base system but there was (known) problems with the libSDL so I've installed it in my chroot with no success...does anyone know what causes this error?
```
Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
found interface lo - loopback
found interface eth0 - 192.168.1.100/255.255.255.0
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
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Current search path:
/home/negatory/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/usr/local/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/usr/local/games/quake4/q4base/zpak_french.pk4 (3462 files)
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
1501ms to load 1071k of material
737ms to load 43k of skin
1834ms to load 716k of sound
9ms to load 1k of materialType
3191ms to load 2078k of lipSync
849ms to load 105k of playback
14643ms to load 1665k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
632 strings read from strings/english_code.lang
1654 strings read from strings/english_guis.lang
5616 strings read from strings/english_lips.lang
6085 strings read from strings/english_maps.lang
632 strings read from strings/french_code.lang
1654 strings read from strings/french_guis.lang
5616 strings read from strings/french_lips.lang
6085 strings read from strings/french_maps.lang
632 strings read from strings/italian_code.lang
1654 strings read from strings/italian_guis.lang
5616 strings read from strings/italian_lips.lang
6085 strings read from strings/italian_maps.lang
632 strings read from strings/spanish_code.lang
1654 strings read from strings/spanish_guis.lang
5616 strings read from strings/spanish_lips.lang
6085 strings read from strings/spanish_maps.lang
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
asoundlib version: 1.0.8
Alsa is available
------ Alsa Sound Initialization -----
ALSA lib confmisc.c:550:(snd_determine_driver) could not open control for card 0ALSA lib conf.c:2672:(snd_config_hooks_call) function snd_config_hook_load_for_all_cards returned error: Invalid argument
ALSA lib pcm.c:1947:(snd_pcm_open_conf) Invalid type for PCM default definition (id: default, value: cards.pcm.default)
snd_pcm_open SND_PCM_STREAM_PLAYBACK 'default' failed: Invalid argument
dlclose
WARNING: sound subsystem disabled

--------------------------------------
----------- Alsa Shutdown ------------
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
...using GL_ARB_texture_non_power_of_two
...using GL_NV_blend_square
X..GL_ARB_texture_compression not found
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..

```

I've never installed any 3D aceleration on the chroot but I can run glxinfo (wich tells me that I have 3D trough my Nvidia 6600) and glxgears just fine!
Please help me!
Thanks

---

### Post by negatory on 2005-10-29
I've also tried to change the initialization script so it looked like this:
```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/quake4"
export LD_LIBRARY_PATH=/chroot/usr/lib:/chroot/lib
./quake4.x86 $*
exit $?

```
But it exits with another error:
```
Quake4 Final V1.0.0.0 Build 2147.12 linux-x86 Oct 20 2005
found interface lo - loopback
found interface eth0 - 192.168.1.100/255.255.255.0
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
Loaded pk4 /usr/local/games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /usr/local/games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /usr/local/games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Current search path:
/home/negatory/.quake4/q4base
/usr/local/games/quake4/q4base
/usr/local/games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/usr/local/games/quake4/q4base/zpak_italian.pk4 (3500 files)
/usr/local/games/quake4/q4base/zpak_french.pk4 (3462 files)
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
1642ms to load 1071k of material
1369ms to load 43k of skin
2206ms to load 716k of sound
46ms to load 1k of materialType
3532ms to load 2078k of lipSync
945ms to load 105k of playback
18232ms to load 1665k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
632 strings read from strings/english_code.lang
1654 strings read from strings/english_guis.lang
5616 strings read from strings/english_lips.lang
6085 strings read from strings/english_maps.lang
632 strings read from strings/french_code.lang
1654 strings read from strings/french_guis.lang
5616 strings read from strings/french_lips.lang
6085 strings read from strings/french_maps.lang
632 strings read from strings/italian_code.lang
1654 strings read from strings/italian_guis.lang
5616 strings read from strings/italian_lips.lang
6085 strings read from strings/italian_maps.lang
632 strings read from strings/spanish_code.lang
1654 strings read from strings/spanish_guis.lang
5616 strings read from strings/spanish_lips.lang
6085 strings read from strings/spanish_maps.lang
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
ERROR: SDL_GL_LoadLibrary libGL.so.1 failed: Could not load OpenGL library

********************
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: SDL_GL_LoadLibrary libGL.so.1 failed: Could not load OpenGL library
```

Can't understand what I'm doing wrong...doom 3 works in base system but not in the chroot complaining about:
```
idRenderSystem::Shutdown()
Sys_Error: SDL_GL_LoadLibrary libGL.so.1 failed: Could not load OpenGL library
```

Thanks!

---

