---
title: "[SOLVED] Quake4 - 'aas_types' Error"
date: 2008-08-12
forum: Gaming &amp; Leisure
---

### Post by Bios Element on 2008-08-12
I've been trying to get Quake4 to run in Ubuntu 8.0.4.
Specs are a Nvidia 8600 With a known working driver.
2 gigs of ram
2.4 Intel Processer.

For sound i 'do' use PulseAudio but from what i could tell that's not the problem. The game changes there resolution to something like 800x600 and shows a large menu like box thing and a custom curser (I assume it's the menu. I've never played it though so i don't know) Before it drops be back to desktop without reverting the resolution.

Honestly I've been trying for 3 hours and have no clue whats wrong... :confused:

```

Quake4  V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface eth1 - 192.168.0.101/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/william/.Games/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /home/william/.Games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /home/william/.Games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
Loaded pk4 /home/william/.Games/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /home/william/.Games/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /home/william/.Games/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /home/william/.Games/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /home/william/.Games/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /home/william/.Games/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /home/william/.Games/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /home/william/.Games/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /home/william/.Games/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /home/william/.Games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /home/william/.Games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /home/william/.Games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /home/william/.Games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /home/william/.Games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /home/william/.Games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /home/william/.Games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Addon pk4 /home/william/.Games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/william/.quake4/q4base
/home/william/.Games/quake4/q4base
/home/william/.Games/quake4/q4base/zpak_english_04.pk4 (3 files)
/home/william/.Games/quake4/q4base/zpak_english_03.pk4 (4 files)
/home/william/.Games/quake4/q4base/zpak_english_02.pk4 (21 files)
/home/william/.Games/quake4/q4base/zpak_english_01.pk4 (1 files)
/home/william/.Games/quake4/q4base/pak022.pk4 (14 files)
/home/william/.Games/quake4/q4base/pak021.pk4 (89 files)
/home/william/.Games/quake4/q4base/pak020.pk4 (11 files)
/home/william/.Games/quake4/q4base/pak019.pk4 (1206 files)
/home/william/.Games/quake4/q4base/pak018.pk4 (3 files)
/home/william/.Games/quake4/q4base/pak017.pk4 (3 files)
/home/william/.Games/quake4/q4base/pak016.pk4 (193 files)
/home/william/.Games/quake4/q4base/pak015.pk4 (34 files)
/home/william/.Games/quake4/q4base/pak014.pk4 (552 files)
/home/william/.Games/quake4/q4base/pak013.pk4 (239 files)
/home/william/.Games/quake4/q4base/pak010.pk4 (5539 files)
/home/william/.Games/quake4/q4base/game200.pk4 (9 files)
/home/william/.Games/quake4/q4base/game100.pk4 (2 files)
/home/william/.Games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
/home/william/.Games/quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 55 loaded
32ms to load 243k of material
12ms to load 43k of skin
98ms to load 723k of sound
0ms to load 0k of materialType
236ms to load 2889k of lipSync
0ms to load 0k of playback
8ms to load 25k of effect
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
1797 strings read from strings/english_mappack.lang
2273 strings read from strings/english_maps.lang
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
1440x900 1280x800 1280x768 1280x720 1152x864 1024x768 832x624 800x600 800x512 720x450 700x525 
640x480 512x384 400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
dlopen(libasound.so.2)
asoundlib version: 1.0.15
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
...using GL_ARB_texture_non_power_of_two
...using GL_NV_blend_square
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_draw_range_elements
...using GL_EXT_blend_minmax
...using GL_NV_float_buffer
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
...using GL_NV_register_combiners
...using NV_vertex_program
...using NV_fragment_program
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using GL_ARB_shader_objects
...using GL_ARB_fragment_shader
...using GL_ARB_vertex_shader
...using GL_ARB_shading_language_100
...using EXT_depth_bounds_test
---------------- R_NV20_Init ----------------
---------------------------------------------
----------------- R200_Init -----------------
Not available.
---------------- R_ARB2_Init ----------------
Available.
---------------------------------------------
------------ R_ReloadARBPrograms ------------
glprogs/test.vfp: File not found
glprogs/test.vfp: File not found
glprogs/interaction.vfp: File not found
glprogs/interaction.vfp: File not found
glprogs/bumpyEnvironment.vfp: File not found
glprogs/bumpyEnvironment.vfp: File not found
glprogs/ambientLight.vfp: File not found
glprogs/ambientLight.vfp: File not found
glprogs/SimpleInteraction.vfp: File not found
glprogs/SimpleInteraction.vfp: File not found
glprogs/shadow.vp: File not found
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp: File not found
glprogs/nv20_diffuseColor.vp: File not found
glprogs/nv20_specularColor.vp: File not found
glprogs/nv20_diffuseAndSpecularColor.vp: File not found
glprogs/environment.vfp: File not found
glprogs/environment.vfp: File not found
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
---------------------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
reloading lights/defaultpointlight.
reloading lights/defaultprojectedlight.
reloading lights/muzzleflash.
reloading gfx/guis/mainmenu/splash.
reloading gfx/guis/soundmeter/audiobg.
reloading gfx/guis/white.
reloading gfx/guis/guicursor_arrow.
reloading gfx/guis/guicursor_hand.
reloading gfx/guis/scrollbarh.
reloading gfx/guis/scrollbarv.
reloading gfx/guis/scrollbar_thumb.
reloading gfx/guis/scrollbar_right.
reloading gfx/guis/scrollbar_left.
reloading gfx/guis/scrollbar_up.
reloading gfx/guis/scrollbar_down.
reloading fonts/english/bigchars.
Could not register font fonts/chain [fonts/english/chain]
found DLL in pak file: /home/william/.Games/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/william/.quake4/q4base/gamex86.so
enabled Flush-To-Zero mode
------------- Initializing Game -------------
gamename: baseQUAKE4-1
gamedate: Jun 15 2007
33ms to load 118k of entityDef
0ms to load 0k of articulatedFigure
Initializing event system
...531 event definitions
Initializing class hierarchy
...247 classes, 598968 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 2399.97 MHz
Compiled '/home/william/.quake4/q4base/scripts/main.script': 1502.7 ms
-------------- Compile stats ----------------

Memory usage:
     Strings: 54, 8464 bytes
  Statements: 84435, 1688700 bytes
   Functions: 3361, 380380 bytes
   Variables: 324172 bytes
    Mem used: 3532564 bytes
 Static data: 4948144 bytes
   Allocated: 6313684 bytes
 Thread size: 7072 bytes

Error ERP_DROP: Unable to find entityDef for 'aas_types'
TODO: Sys_SetClipboardData
------------ Game Map Shutdown --------------
---------------------------------------------
********************
ERROR: Unable to find entityDef for 'aas_types'
********************
Sys_Error: Error during initialization
pure virtual method called
terminate called after throwing an instance of 'idException'
Aborted

```

---

### Post by 1337 on 2008-08-13
You probably didn't copy all the "pak" files from the Quake4 cd's/dvd to q4base directory or some packs you copied has wrong permission rights that can cause such error. Maybe try also installing game in some normal directory (like default value).

---

