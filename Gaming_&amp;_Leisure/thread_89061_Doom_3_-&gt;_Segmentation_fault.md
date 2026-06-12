---
title: "Doom 3 -&gt; Segmentation fault"
date: 2005-11-11
forum: Gaming &amp; Leisure
---

### Post by kaamos on 2005-11-11
Hey!

I installed doom 3 on breezy and now I'm having some trouble with it. The game segfaults almost instantly when the it has started (I can usually move around for a couple of second before the disaster happens and everything freezes). I had this problem in Hoary as well, but then I usually could play for almost an hour before the segfault occured.

I have an ATI card that runs 3d with fglrx driver 8.18.8.

Anyway, if anyone knows what could cause this please let me know. Thanks!
Log:```

DOOM 1.1.1286 linux-x86 Nov 24 2004 17:56:04
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntu
local IP: 127.0.0.1
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0x7dafc4d4
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x16cf3b8a
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Current search path:
/home/alaisi/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5151 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
execing DoomConfig.cfg
couldn't exec autoexec.cfg
5151 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
Failed to detect DGA DirectVideo Mouse
Free86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: FireMV 2400 PCI DDR Generic
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_ATI_element_array GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_map_object_buffer GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_vertex_array_object GL_ATI_vertex_attrib_array_object GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_blend_square GL_NV_occlusion_query GL_NV_texgen_reflection GL_SGI_color_matrix GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother./dev/dsp - bit rate: 16, channels: 2, frequency: 44100
allocated a mix buffer of 16384 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
...using GL_ATI_fragment_shader
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
X..GL_ARB_fragment_program not found
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
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
---------- R_ARB2_Init ----------
Not available.
---------- R_Exp_Init -----------
Disabled at compile time.
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfp
glprogs/test.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/interaction.vfp
glprogs/interaction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp
glprogs/bumpyEnvironment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/ambientLight.vfp
glprogs/ambientLight.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/shadow.vp
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
-------------------------------
using ARB_vertex_buffer_object memory
using R200 renderSystem
glGetError() = 0x500
found DLL in pak file: /usr/local/games/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/alaisi/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Oct  4 2004
Initializing event system
...472 event definitions
Initializing class hierarchy
...141 classes, 381376 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 2665.66 MHz
Compiled 'removeInitialSplineAngles': 3503.2 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67783, 1355660 bytes
   Functions: 2108, 250452 bytes
   Variables: 147320 bytes
    Mem used: 2476244 bytes
 Static data: 2277552 bytes
   Allocated: 3283340 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
--- Common Initialization Complete ---
------------- Warnings ---------------
during DOOM 3 initialization...
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
1 warnings
terminal support disabled
pid: 8842
496 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
32 MB Video Memory
Async thread started
--------- Game Map Shutdown ----------
--------------------------------------
reloading guis/mainmenu.gui.
reloading guis/restart.gui.
reloading guis/gameover.gui.
reloading guis/msg.gui.
reloading guis/takeNotes.gui.
reloading guis/intro.gui.
--------- Map Initialization ---------
Map: game/mars_city1
glprogs/heatHaze.vfp
glprogs/heatHaze.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/heatHazeWithMask.vfp
glprogs/heatHazeWithMask.vfp: GL_FRAGMENT_PROGRAM_ARB not available
----------- Game Map Init ------------
collision data:
   421 models
 30823 vertices (722 KB)
 54551 edges (1917 KB)
 22257 polygons (1564 KB)
  4068 brushes (556 KB)
 12449 nodes (340 KB)
 43444 polygon refs (339 KB)
 14219 brush refs (111 KB)
 18352 internal edges
  1461 sharp edges
     0 contained polygons removed
     0 polygons merged
  5551 KB total memory used
449 msec to load collision data.
map bounds are (19640.0, 22168.0, 29496.0)
max clip sector is (1227.5, 1385.5, 1843.5)
    2 KB passage memory used to build PVS
    2 msec to calculate PVS
   56 areas
  110 portals
    9 areas visible on average
  448 bytes PVS data
[Load AAS]
loading maps/game/mars_city1.aas48
done.
[Load AAS]
loading maps/game/mars_city1.aas96
[Load AAS]
loading maps/game/mars_city1.aas_guardian
[Load AAS]
loading maps/game/mars_city1.aas_mancubus
[Load AAS]
loading maps/game/mars_city1.aas_sabaoth
[Load AAS]
loading maps/game/mars_city1.aas_cyberdemon
Entering doom_main()
Exiting doom_main()
Spawning entities
loaded collision model models/mapobjects/com/platguistand/mc_platguistand.lwo
WARNING: marscity_cinematic_sarge_1 has no AAS file
WARNING: marscity_cinematic_sarge2_1 has no AAS file
loaded collision model models/mapobjects/filler/burgerboxopen.lwo
glprogs/heatHazeWithMaskAndVertex.vfp
glprogs/heatHazeWithMaskAndVertex.vfp: GL_FRAGMENT_PROGRAM_ARB not available
loaded collision model models/mapobjects/lab/diamondbox/diamondbox_sm.lwo
loaded collision model models/mapobjects/com/modconsole1.lwo
loaded collision model models/mapobjects/filler/burgereat.lwo
loaded collision model models/mapobjects/filler/burgerboxclose.lwo
loaded collision model models/mapobjects/filler/mkeyboard.lwo
loaded collision model models/mapobjects/lights/florescent_bulbflare.ASE
loaded collision model models/mapobjects/base/misc/emerlight.ase
loaded collision model models/mapobjects/monitors/controlmonitor.lwo
loaded collision model models/mapobjects/doors/mcitydoor2l.lwo
loaded collision model models/mapobjects/doors/mcitydoor2r.lwo
loaded collision model models/mapobjects/doors/mcdoor2frame.lwo
loaded collision model models/mapobjects/tables/conf_table/conf_table.lwo
loaded collision model models/mapobjects/filler/cola1.lwo
loaded collision model models/mapobjects/filler/foamcup.lwo
loaded collision model models/mapobjects/signs/marquee/marquee.lwo
loaded collision model models/mapobjects/doors/mcitydoorframe.lwo
loaded collision model models/mapobjects/doors/mcitydoorframegui.lwo
loaded collision model models/items/keycard/keycard3.lwo
loaded collision model models/mapobjects/doors/mcitydoor.lwo
loaded collision model models/mapobjects/cpu/pullhandle.lwo
loaded collision model models/mapobjects/doors/delelev/delelevlf.lwo
loaded collision model models/mapobjects/guiobjects/techdrpanel1/techdrpanel1.lwo
loaded collision model models/mapobjects/doors/delelev/delelevrt.lwo
loaded collision model models/mapobjects/filler/ktable.lwo
loaded collision model models/mapobjects/cpu/heater.lwo
loaded collision model models/mapobjects/cpu/heater2.lwo
loaded collision model models/mapobjects/cpu/comrack2.lwo
loaded collision model models/mapobjects/lab/sink2/sink2.lwo
loaded collision model models/mapobjects/filler/sodamachine.lwo
loaded collision model models/mapobjects/filler/binder1.ase
loaded collision model models/mapobjects/lab/bubbler2/bubbler2.lwo
loaded collision model models/mapobjects/filler/tbox7.ase
loaded collision model models/mapobjects/filler/binder3.ase
loaded collision model models/mapobjects/chairs/modchair/modtable.lwo
loaded collision model models/mapobjects/chairs/modchair/modseat.lwo
loaded collision model models/mapobjects/chairs/modchair/modarm.lwo
removed 2 degenerate triangles
loaded collision model models/mapobjects/lab/newfridge/newfridge.lwo
loaded collision model models/mapobjects/filler/paper1.ase
loaded collision model models/mapobjects/filler/tbox6.ase
loaded collision model models/mapobjects/filler/tbox_open.ase
loaded collision model models/mapobjects/filler/toolchest.lwo
loaded collision model models/mapobjects/doors/deldoor1/deldoor1frm.lwo
loaded collision model models/mapobjects/doors/deldoor1/deldoor1.lwo
loaded collision model models/mapobjects/com/modconsole2.lwo
loaded collision model models/mapobjects/com/modconsole5.lwo
loaded collision model models/mapobjects/cpu/cpumaze1.lwo
loaded collision model models/mapobjects/doors/deldoor1/deldoor1win.lwo
loaded collision model models/mapobjects/com/modconsole4.lwo
loaded collision model models/mapobjects/lab/gizmo2/gizmo2.lwo
loaded collision model models/mapobjects/lab/autable/autable.lwo
loaded collision model models/mapobjects/lab/roboarm1/roboarm1.lwo
loaded collision model models/mapobjects/utility/tecknob2/tecknob2.lwo
loaded collision model models/mapobjects/cpu/comrack.lwo
loaded collision model models/mapobjects/tables/gendesk/gendesk2.lwo
loaded collision model models/mapobjects/filler/tbox2.ase
loaded collision model models/mapobjects/cpu/serverplate.lwo
loaded collision model models/mapobjects/filler/snackmachine.lwo
loaded collision model models/mapobjects/filler/tbox1.ase
loaded collision model models/mapobjects/washroom/clamp.ase
loaded collision model models/mapobjects/washroom/urinal2.ase
loaded collision model models/mapobjects/washroom/dryer.ase
loaded collision model models/mapobjects/washroom/bsink.ase
loaded collision model models/mapobjects/washroom/soap.ase
loaded collision model models/mapobjects/washroom/toilet.ase
loaded collision model models/mapobjects/washroom/tp.ase
loaded collision model models/mapobjects/arcade_machine/arcade_machine.lwo
loaded collision model models/mapobjects/mcity/deskcomp/deskcomp.lwo
loaded collision model models/mapobjects/skmachines/skoverhang.lwo
loaded collision model models/mapobjects/shipping_crates/shipping_crates.lwo
loaded collision model models/mapobjects/skmachines/skcube.lwo
loaded collision model models/mapobjects/doors/accesshatch/accesshatch.lwo
loaded collision model models/mapobjects/doors/accesshatch/accesshatchdoor.lwo
loaded collision model models/mapobjects/elevators/elevator.lwo
loaded collision model models/mapobjects/swinglights/swinglight1b.lwo
loaded collision model models/mapobjects/swinglights/swinglight_long_wbulbs_bulb_broken.ase
loaded collision model models/mapobjects/filler/keyboard1.ase
loaded collision model models/mapobjects/storagecab/gunrack/gunrackcomp.lwo
loaded collision model models/mapobjects/chairs/modchair/modcorner.lwo
loaded collision model models/mapobjects/shutter/shutter_small.lwo
loaded collision model models/mapobjects/mcity/outside/mc_outside.lwo
loaded collision model models/mapobjects/turrets/ceilingturret1b.lwo
loaded collision model models/mapobjects/mcity/outside/mc_outside2.lwo
loaded collision model models/mapobjects/kiosk/infokiosk2.lwo
loaded collision model models/mapobjects/lab/loadingplatform/loadingplatform.lwo
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
loaded collision model models/mapobjects/deltakiosk/deltakiosk.lwo
WARNING: marscity_cinematic_player_sarge has no AAS file
loaded collision model models/mapobjects/hangar/hangar1b.lwo
loaded collision model models/mapobjects/doors/jumbodoor/jumbodoorfrm.lwo
loaded collision model models/mapobjects/hangar/hangar1tower.lwo
loaded collision model models/mapobjects/hangar/rails3.lwo
loaded collision model models/mapobjects/hangar/rails2.lwo
loaded collision model models/mapobjects/hangar/rails1.lwo
loaded collision model models/mapobjects/hangar/rails4.lwo
loaded collision model models/mapobjects/hangar/rails5.lwo
loaded collision model models/mapobjects/hangar/pillar1.lwo
loaded collision model models/mapobjects/hangar/rails6.lwo
loaded collision model models/mapobjects/hangar/marquee.lwo
loaded collision model models/mapobjects/hangar/hangarlamp1.lwo
loaded collision model models/mapobjects/mcity/bioscanner/bioscannereye.lwo
loaded collision model models/mapobjects/tables/gendesk/gendesk1.lwo
loaded collision model models/mapobjects/hangar/hangar2tower.lwo
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
loaded collision model models/mapobjects/monitors/hangingmonitor.lwo
loaded collision model models/mapobjects/signs/ceilingsign/ceilingsign.lwo
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
loaded collision model models/mapobjects/elevators/elevator_door.lwo
loaded collision model models/mapobjects/com/platguistand/platguistand.lwo
loaded collision model models/mapobjects/guiobjects/flatmonitor/flatmonitor.lwo
loaded collision model models/mapobjects/mcity/bioscanner/bioscanbeam.lwo
loaded collision model models/mapobjects/mcity/bioscanner/bioscanner.lwo
loaded collision model models/mapobjects/doors/mcitydoor_glass.lwo
loaded collision model models/mapobjects/lab/fridge1/fridge1_delta2b.lwo
WARNING: Couldn't load sound 'guisounds.wav' using default
loaded collision model models/mapobjects/turrets/ceilingturret1a.lwo
...1969 entities spawned, 0 inhibited

==== Processing events ====
--------------------------------------
SpawnPlayer: 0
loaded collision model models/weapons/shell1/mshell_lo.lwo
loaded collision model models/weapons/shell1/sshell_bigger.lwo
----- idRenderModelManagerLocal::EndLevelLoad -----
    0 purged from previous
 1023 kept from previous
    0 new loaded
all models loaded in   0.0 seconds
---------------------------------------------------
----- idImageManager::EndLevelLoad -----
WARNING: Non-portable: path contains uppercase characters: base/dds/makeIntensity/lights
WARNING: Non-portable: path contains uppercase characters: base/dds/makeIntensity/lights
WARNING: Non-portable: path contains uppercase characters: base/dds/makeIntensity/lights
WARNING: Non-portable: path contains uppercase characters: base/dds/makeIntensity/lights
    0 purged from previous
    5 kept from previous
 2074 new loaded
all images loaded in  16.1 seconds
----------------------------------------
394 msec to draw all images
----- idSoundCache::EndLevelLoad -----
13517k referenced
    0k purged
----------------------------------------
-----------------------------------
 40147 msec to load game/mars_city1
idRenderWorld::GenerateAllInteractions, msec = 58, staticAllocCount = 0.
interactionTable size: 2822240 bytes
29910 interaction take 3349920 bytes
------------- Warnings ---------------
during game/mars_city1...
WARNING: Couldn't load sound 'guisounds.wav' using default
WARNING: Non-portable: path contains uppercase characters: base/dds/makeIntensity/lights
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
3 warnings
missed 9 sound updates
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
--------- Game Map Shutdown ----------
--------------------------------------
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
double fault Hangup, bailing out

```

EDIT: Oh yeah, I checked the md5sums of the pak-files and they are all good.

---

### Post by Ranime on 2005-11-14
What version of Doom3 are you using?

It seems to me you're using an outdated version with a much to light GPU... (Ati R200 IGP)...

Try updating to doom3 1302 and read this howto --> [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54)
:rolleyes: 

Worked for me (Ati 9600)

```
ranime@ishtar:~$ ./doom3.sh
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.0.8/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/ranime/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
execing DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "XFree86-DGA" missing on display ":0.0".
Failed to detect DGA DirectVideo Mouse
Free86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: RADEON 9600 Generic
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_element_array GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_map_object_buffer GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_ATI_vertex_array_object GL_ATI_vertex_attrib_array_object GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_blend_square GL_NV_occlusion_query GL_NV_texgen_reflection GL_SGI_color_matrix GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother./dev/dsp - bit rate: 16, channels: 2, frequency: 44100
allocated a mix buffer of 16384 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
...using GL_ATI_separate_stencil
...using GL_ATI_fragment_shader
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
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
---------- R_ARB2_Init ----------
Available.
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfp
glprogs/test.vfp
glprogs/interaction.vfp
glprogs/interaction.vfp
glprogs/bumpyEnvironment.vfp
glprogs/bumpyEnvironment.vfp
glprogs/ambientLight.vfp
glprogs/ambientLight.vfp
glprogs/shadow.vp
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
found DLL in pak file: /usr/local/games/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/ranime/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: May 10 2005
Initializing event system
...472 event definitions
Initializing class hierarchy
...142 classes, 381376 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 2205.14 MHz
Compiled 'removeInitialSplineAngles': 1812.5 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67866, 1357320 bytes
   Functions: 2108, 250452 bytes
   Variables: 147244 bytes
    Mem used: 2478772 bytes
 Static data: 2277552 bytes
   Allocated: 3284208 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
Opening IP socket: localhost:-1
--- Common Initialization Complete ---
------------- Warnings ---------------
during DOOM 3 initialization...
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
1 warnings
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 13216
512 MB System Memory
256 MB Video Memory
Async thread started
guid set to vtg0q2C1loI
--------- Game Map Shutdown ----------
--------------------------------------
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------
shutdown terminal support
ranime@ishtar:~$
```

If you're wondering what the content of my *doom3.sh* is:
```
esdctl off
sleep 2
doom3 +set sys_videoRam 256
esdctl on

```

---

### Post by Hellion DarkLord on 2007-04-27
I have lots of these errors:

"Non-portable: path contains uppercase characters...."

I noticed that in Ranime's post there are no such errors.

So that led me to believe that I could get rid of all the links I put in my system and just upgrade to doom3 1302.  Then I noticed that I'm running 1304.

now I'm lost again.  how do I get rid of

Non-portable: path contains uppercase characters

without having all these silly little links all over the place? I don't even know if my links really work correctly because I'm new to all this gaming stuff and only recently upgraded to a G6200

Thanks for any help

Hellion

---

