---
title: "Quake 4 help... ATI problems again..."
date: 2009-05-02
forum: Gaming &amp; Leisure
---

### Post by racerraul on 2009-05-02
Ok ATI gurus... I'm been looking for a solution to this problem and keep coming up empty.

When I try to run Quake4 I get this...

X..GL_EXT_texture_compression_s3tc not found

But according to my system it is there...
```
dustin@Dustin-2600:~$ glxinfo | grep -i compression
    GL_ARB_texture_compression, GL_ARB_texture_compression_rgtc, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_EXT_texture_array, GL_EXT_texture_compression_latc, 
    **GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc, **

```

direct redering is enabled...
```
dustin@Dustin-2600:~$ glxinfo | grep -i render
**direct rendering: Yes**
OpenGL renderer string: ATI Radeon HD 3200 Graphics
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, 

```

I did install the ia32-libs before installation since I am using 64bit OS.

Here is the quake4 init output...

```
dustin@Dustin-2600:~$ Quake4/quake4
Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface eth0 - 192.168.1.2/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/dustin/Quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /home/dustin/Quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /home/dustin/Quake4/q4base/game200.pk4 with checksum 0xa3c810d9
Loaded pk4 /home/dustin/Quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /home/dustin/Quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /home/dustin/Quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /home/dustin/Quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /home/dustin/Quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /home/dustin/Quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /home/dustin/Quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /home/dustin/Quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /home/dustin/Quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /home/dustin/Quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /home/dustin/Quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /home/dustin/Quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /home/dustin/Quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /home/dustin/Quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /home/dustin/Quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /home/dustin/Quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /home/dustin/Quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /home/dustin/Quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /home/dustin/Quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /home/dustin/Quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /home/dustin/Quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /home/dustin/Quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /home/dustin/Quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /home/dustin/Quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /home/dustin/Quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /home/dustin/Quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /home/dustin/Quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /home/dustin/Quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Addon pk4 /home/dustin/Quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/dustin/.quake4/q4base
/home/dustin/Quake4/q4base
/home/dustin/Quake4/q4base/zpak_english_04.pk4 (3 files)
/home/dustin/Quake4/q4base/zpak_english_03.pk4 (4 files)
/home/dustin/Quake4/q4base/zpak_english_02.pk4 (21 files)
/home/dustin/Quake4/q4base/zpak_english_01.pk4 (1 files)
/home/dustin/Quake4/q4base/zpak_english.pk4 (3457 files)
/home/dustin/Quake4/q4base/pak022.pk4 (14 files)
/home/dustin/Quake4/q4base/pak021.pk4 (89 files)
/home/dustin/Quake4/q4base/pak020.pk4 (11 files)
/home/dustin/Quake4/q4base/pak019.pk4 (1206 files)
/home/dustin/Quake4/q4base/pak018.pk4 (3 files)
/home/dustin/Quake4/q4base/pak017.pk4 (3 files)
/home/dustin/Quake4/q4base/pak016.pk4 (193 files)
/home/dustin/Quake4/q4base/pak015.pk4 (34 files)
/home/dustin/Quake4/q4base/pak014.pk4 (552 files)
/home/dustin/Quake4/q4base/pak013.pk4 (239 files)
/home/dustin/Quake4/q4base/pak012.pk4 (1081 files)
/home/dustin/Quake4/q4base/pak011.pk4 (5620 files)
/home/dustin/Quake4/q4base/pak010.pk4 (5539 files)
/home/dustin/Quake4/q4base/pak009.pk4 (1284 files)
/home/dustin/Quake4/q4base/pak008.pk4 (1289 files)
/home/dustin/Quake4/q4base/pak007.pk4 (1330 files)
/home/dustin/Quake4/q4base/pak006.pk4 (1343 files)
/home/dustin/Quake4/q4base/pak005.pk4 (1395 files)
/home/dustin/Quake4/q4base/pak004.pk4 (2249 files)
/home/dustin/Quake4/q4base/pak003.pk4 (1281 files)
/home/dustin/Quake4/q4base/pak002.pk4 (313 files)
/home/dustin/Quake4/q4base/pak001.pk4 (5837 files)
/home/dustin/Quake4/q4base/game200.pk4 (9 files)
/home/dustin/Quake4/q4base/game100.pk4 (2 files)
/home/dustin/Quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
/home/dustin/Quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 64 loaded
169ms to load 1125k of material
57ms to load 43k of skin
105ms to load 723k of sound
4ms to load 1k of materialType
252ms to load 2889k of lipSync
50ms to load 105k of playback
740ms to load 1690k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' without VO
.... found additional language 'italian' without VO
.... found additional language 'spanish' without VO
696 strings read from strings/english_code.lang
1794 strings read from strings/english_guis.lang
5756 strings read from strings/english_lips.lang
5759 strings read from strings/english_mappack.lang
6235 strings read from strings/english_maps.lang
3 strings read from strings/french_mappack.lang
3 strings read from strings/italian_mappack.lang
3 strings read from strings/spanish_mappack.lang
Couldn't open journal files
execing default.cfg
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
1280x1024 1280x960 1280x768 1280x720 1152x864 1024x768 800x600 720x480 640x480 640x400 512x384 
400x300 320x240 320x200 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.17a
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
...using GL_ARB_texture_non_power_of_two
...using GL_NV_blend_square
...using GL_ARB_texture_compression
X..GL_EXT_texture_compression_s3tc not found
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

Anyhelp is appreciated...

I got this game working on older nvidia & newer nvidia card based systems at home, and as usual... the ATI one gives me the most trouble... 

if I need to quit being a cheapskate and order an nvidia card... feel free to say so :lolflag:

But I rather see if maybe the ATI fan\supporters can help.

---

### Post by racerraul on 2009-05-10
Bought an Nvidia card... problem solved.

---

