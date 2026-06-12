---
title: "Quake 4 startup crash"
date: 2006-01-28
forum: Gaming &amp; Leisure
---

### Post by johso on 2006-01-28
Hello there!

I've been searching this forum thin. I searched for Quake, and looked at every Quake3/4 problem on all 18 pages, and got seriously tired of trying solutions that didn't work.
So now I'm hoping that someone knows what the problem is. I don't think it's a sound problem, nor a video problem. But I'm not sure of it.
I suspect that this is the problem:
"signal caught: Segmentation fault" - which you can see on the last lines of the console output.
But here goes the console output:
 (I've cut out a lot of the "WARNING" messages, because there was _alot_ of them and most of them look like this: "WARNING: Unknown string id #str_201003" - just with different numbers)

Quake4 Final V1.0.6.0 Build 2147.12 linux-x86 Dec 12 2005
found interface lo - loopback
found interface eth0 - 10.0.0.2/255.0.0.0
CPU: Intel CPU with MMX & SSE & SSE2
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /media/hda6/games/quake4/q4base/game000.pk4 with checksum 0x9321cee4
Loaded pk4 /media/hda6/games/quake4/q4base/game100.pk4 with checksum 0x6f346a2
Loaded pk4 /media/hda6/games/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /media/hda6/games/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /media/hda6/games/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /media/hda6/games/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /media/hda6/games/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /media/hda6/games/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /media/hda6/games/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /media/hda6/games/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /media/hda6/games/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /media/hda6/games/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /media/hda6/games/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /media/hda6/games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /media/hda6/games/quake4/q4base/zpak_french_01.pk4 with checksum 0xe909853f
Loaded pk4 /media/hda6/games/quake4/q4base/zpak_italian_01.pk4 with checksum 0xef0e1696
Loaded pk4 /media/hda6/games/quake4/q4base/zpak_spanish_01.pk4 with checksum 0xe829a04a
Current search path:
/home/johso/.quake4/q4base
/media/hda6/games/quake4/q4base
/media/hda6/games/quake4/q4base/zpak_spanish_01.pk4 (2 files)
/media/hda6/games/quake4/q4base/zpak_italian_01.pk4 (2 files)
/media/hda6/games/quake4/q4base/zpak_french_01.pk4 (2 files)
/media/hda6/games/quake4/q4base/zpak_english_01.pk4 (1 files)
/media/hda6/games/quake4/q4base/pak011.pk4 (5620 files)
/media/hda6/games/quake4/q4base/pak010.pk4 (5539 files)
/media/hda6/games/quake4/q4base/pak009.pk4 (1284 files)
/media/hda6/games/quake4/q4base/pak008.pk4 (1289 files)
/media/hda6/games/quake4/q4base/pak007.pk4 (1330 files)
/media/hda6/games/quake4/q4base/pak006.pk4 (1343 files)
/media/hda6/games/quake4/q4base/pak005.pk4 (1395 files)
/media/hda6/games/quake4/q4base/pak004.pk4 (2249 files)
/media/hda6/games/quake4/q4base/pak003.pk4 (1281 files)
/media/hda6/games/quake4/q4base/pak002.pk4 (313 files)
/media/hda6/games/quake4/q4base/pak001.pk4 (5837 files)
/media/hda6/games/quake4/q4base/game100.pk4 (2 files)
/media/hda6/games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 59 loaded
724ms to load 1071k of material
72ms to load 43k of skin
199ms to load 716k of sound
10ms to load 1k of materialType
369ms to load 2078k of lipSync
81ms to load 105k of playback
1160ms to load 1665k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' without VO
.... found additional language 'italian' without VO
.... found additional language 'spanish' without VO
641 strings read from strings/english_code.lang
641 strings read from strings/french_code.lang
641 strings read from strings/italian_code.lang
641 strings read from strings/spanish_code.lang
Couldn't open journal files
execing default.cfg
couldn't exec editor.cfg
execing Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother.
/dev/dsp - bit rate: 16, channels: 6, frequency: 44100
allocated a mix buffer of 49152 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_NV_blend_square
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_draw_range_elements
...using GL_EXT_blend_minmax
X..GL_NV_float_buffer not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..NV_vertex_program not found
X..GL_EXT_stencil_two_side not found
...using GL_ATI_separate_stencil
...using GL_ATI_fragment_shader
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using GL_ARB_shader_objects
...using GL_ARB_fragment_shader
...using GL_ARB_vertex_shader
...using GL_ARB_shading_language_100
X..EXT_depth_bounds_test not found
---------------- R_NV20_Init ----------------
Not available.
----------------- R200_Init -----------------
GL_NUM_FRAGMENT_REGISTERS_ATI: 6
GL_NUM_FRAGMENT_CONSTANTS_ATI: 8
GL_NUM_PASSES_ATI: 2
GL_NUM_INSTRUCTIONS_PER_PASS_ATI: 8
GL_NUM_INSTRUCTIONS_TOTAL_ATI: 16
GL_COLOR_ALPHA_PAIRING_ATI: 1
GL_NUM_LOOPBACK_COMPONENTS_ATI: 3
GL_NUM_INPUT_INTERPOLATOR_COMPONENTS_ATI: 3
FPROG_FAST_PATH
---------------------
---------------- R_ARB2_Init ----------------
Available.
---------------------------------------------
MOBILITY RADEON 9700 Generic: prefers simple lighting
------------ R_ReloadARBPrograms ------------
glprogs/test.vfp
glprogs/test.vfp
glprogs/interaction.vfp
glprogs/interaction.vfp
glprogs/bumpyEnvironment.vfp
glprogs/bumpyEnvironment.vfp
glprogs/ambientLight.vfp
glprogs/ambientLight.vfp
glprogs/SimpleInteraction.vfp
glprogs/SimpleInteraction.vfp
glprogs/shadow.vp
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt
glprogs/arbFP_glasswarp.txt
glprogs/arbVP_depth.vp
glprogs/arbFP_depth.fp
glprogs/arbFP_depth_coc.fp
---------------------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
reloading textures/common/debuggraph.
reloading makeIntensity( gfx/lights/squarelight1a).
reloading gfx/lights/squarelight1.
reloading gfx/lights/round.
reloading gfx/guis/mainmenu/splash.
reloading gfx/2d/bigchars.
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
found DLL in pak file: /media/hda6/games/quake4/q4base/game100.pk4/gamex86.so
copy gamex86.so to /home/johso/.quake4/q4base/gamex86.so
enabled Flush-To-Zero mode
------------- Initializing Game -------------
gamename: baseQUAKE4-1
gamedate: Oct 19 2005
476ms to load 634k of entityDef
87ms to load 177k of articulatedFigure
Initializing event system
...527 event definitions
Initializing class hierarchy
...242 classes, 586024 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 1495.38 MHz
Compiled '/home/johso/.quake4/q4base/scripts/main.script': 2658.9 ms
-------------- Compile stats ----------------

Memory usage:
     Strings: 54, 8464 bytes
  Statements: 84406, 1688120 bytes
   Functions: 3361, 380380 bytes
   Variables: 324172 bytes
    Mem used: 3531952 bytes
 Static data: 4948144 bytes
   Allocated: 6313652 bytes
 Thread size: 7072 bytes

...5 aas types
game initialized.
---------------------------------------------
Loading viseme file: annosoft
----------- Initializing Session ------------
----------------- BSE Init ------------------
WARNING: Unknown string id #str_200970
WARNING: idChoiceWindow:: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_system_val' has value count unequal to choices count
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_system_val' references undefined cvar 's_useOpenAL'
WARNING: Unknown string id #str_201005
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_device_val' references undefined cvar 's_deviceName'
WARNING: Unknown string id #str_200972
WARNING: Unknown string id #str_200059
WARNING: idChoiceWindow::InitVars: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_eax_val' references undefined cvar 's_useEAXReverb'
WARNING: Unknown string id #str_200152
WARNING: Unknown string id #str_200059
WARNING: idChoiceWindow:: gui 'guis/mainmenu.gui' window 'pop_set_sndAdv_surrspkrs_val' has value count unequal to choices count
WARNING: Unknown string id #str_201003
WARNING: Unknown string id #str_200323
session initialized
---------------------------------------------
------ Common Initialization Complete -------
WARNING: terminal type 'rxvt' is unknown. terminal support may not work correctly
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 10224
detecting video ram ( set sys_videoRam to force ) ..
1495 MHz CPU
1008 MB System Memory
96 MB Video Memory
Async thread started
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
------------ Game Map Shutdown --------------
---------------------------------------------
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
Shutting down SDL subsystem
--------------- Game Shutdown ---------------
rvStatAllocator:  dump of usage stats
        0 total bytes handed out in 0 requests
        begin game:      0;  end game:        0
        player hit:      0;  player kill:     0
        player death:    0;
        damage dealt:    0;  damage taken:    0
        stat team:       0
        flag capture:    0;
        flag drop:       0;  flag return:     0
------------ Game Map Shutdown --------------
---------------------------------------------
Shutdown event system
---------------------------------------------
shutdown terminal support

---

### Post by johso on 2006-01-28
Okay, I feel pretty stupid - it was all because of one file that was missing. Geeze.

---

### Post by hopstah on 2006-08-17
and that file was?????

---

### Post by johso on 2006-08-21
One of the pk4 files, I think it was pak001.pk4, but I don't remember exactly (never got the game working anyway, weird menus).
But do yourself a favor and copy the whole thing over again, that's what I did.
Hope it helps :)

---

