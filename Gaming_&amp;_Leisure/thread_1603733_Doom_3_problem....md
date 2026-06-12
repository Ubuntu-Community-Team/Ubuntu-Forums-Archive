---
title: "Doom 3 problem..."
date: 2010-10-23
forum: Gaming &amp; Leisure
---

### Post by NeptuneNavigator2001 on 2010-10-23
Greetings, fellow Ubuntu users.  I've been using computers for many years now, but up until mid-2006, I was strictly a DOS/Windows user.  For personal and performance reasons, I made the decision a few days ago, to move over to Ubuntu Linux.  With that said, I expect that the move will not be easy at first, and I am willing to do whatever it takes to get things up and running smoothly.  Which brings me to my problem:

I've managed to install Doom 3 under Ubuntu - after learning about several things I needed to do first - and the game does start up.  However, when I attempt to load a new game, it loads the actual data, shows the Doom 3 logo, and the plot text just before the main intro - then the game crashes, most of the time leaving my desktop in 640x480 mode, forcing me to reboot to get the default resolution back.  Despite this however, I have learned how to copy output text from the Terminal to a file using the "tee" command, but I was not able to do so from the approximate moment the error occurred.  So for that, I had to manually copy and paste it to the end of the same file.  Here is the output text - be forewarned, it is QUITE long:

***---Begin Output Log---***
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface wlan0 - 192.168.1.6/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/aaron/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
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
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: Mesa DRI R300 (RS400 5955) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL DRI2
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_provoking_vertex GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_MESAX_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_bgra GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_blit GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_vertex_program GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.23
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device plughw:0 for playback
device buffer size: 5461 frames ( 21844 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
X..GL_EXT_texture_compression_s3tc not found
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
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
copy gamex86.so to /home/aaron/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Jan 16 2007
Initializing event system
...473 event definitions
Initializing class hierarchy
...142 classes, 382184 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 1600 MHz
Compiled 'removeInitialSplineAngles': 1808.3 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67875, 1357500 bytes
   Functions: 2109, 250532 bytes
   Variables: 147376 bytes
    Mem used: 2479288 bytes
 Static data: 2277552 bytes
   Allocated: 3284544 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
Opening IP socket: localhost:-1
--- Common Initialization Complete ---
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 2565
1888 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
guess failed, return default low-end VRAM setting ( 64MB VRAM )
64 MB Video Memory
Async thread started
guid set to Hs5jojVPAlI
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
--------- Game Map Shutdown ----------
--------------------------------------
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
reloading guis/mainmenu.gui.
reloading guis/restart.gui.
reloading guis/gameover.gui.
reloading guis/msg.gui.
reloading guis/takeNotes.gui.
reloading guis/intro.gui.
reloading guis/netmenu.gui.
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
--------- Map Initialization ---------
Map: game/mars_city1
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
glprogs/heatHaze.vfp
glprogs/heatHaze.vfp
preparing audio device for output
preparing audio device for output
glprogs/heatHazeWithMask.vfp
glprogs/heatHazeWithMask.vfp
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
----------- Game Map Init ------------
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
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
444 msec to load collision data.
map bounds are (19640.0, 22168.0, 29496.0)
max clip sector is (1227.5, 1385.5, 1843.5)
    2 KB passage memory used to build PVS
    3 msec to calculate PVS
   56 areas
  110 portals
    9 areas visible on average
  448 bytes PVS data
[Load AAS]
loading maps/game/mars_city1.aas48
preparing audio device for output
done.
preparing audio device for output
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
preparing audio device for output
loaded collision model models/mapobjects/com/platguistand/mc_platguistand.lwo
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
WARNING: marscity_cinematic_sarge_1 has no AAS file
preparing audio device for output
preparing audio device for output
WARNING: marscity_cinematic_sarge2_1 has no AAS file
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
loaded collision model models/mapobjects/filler/burgerboxopen.lwo
preparing audio device for output
preparing audio device for output
glprogs/heatHazeWithMaskAndVertex.vfppreparing audio device for output

glprogs/heatHazeWithMaskAndVertex.vfp
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
loaded collision model models/mapobjects/lab/diamondbox/diamondbox_sm.lwo
preparing audio device for output
loaded collision model models/mapobjects/com/modconsole1.lwo
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
loaded collision model models/mapobjects/filler/burgereat.lwo
loaded collision model models/mapobjects/filler/burgerboxclose.lwo
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
loaded collision model models/mapobjects/filler/mkeyboard.lwo
preparing audio device for output
loaded collision model models/mapobjects/lights/florescent_bulbflare.ASE
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
loaded collision model models/mapobjects/base/misc/emerlight.ase
loaded collision model models/mapobjects/monitors/controlmonitor.lwo
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
loaded collision model models/mapobjects/doors/mcitydoor2l.lwo
loaded collision model models/mapobjects/doors/mcitydoor2r.lwo
loaded collision model models/mapobjects/doors/mcdoor2frame.lwo
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
preparing audio device for output
loaded collision model models/mapobjects/tables/conf_table/conf_table.lwo
preparing audio device for output
loaded collision model models/mapobjects/filler/cola1.lwo
loaded collision model models/mapobjects/filler/foamcup.lwo
loaded collision model models/mapobjects/signs/marquee/marquee.lwo
preparing audio device for output
loaded collision model models/mapobjects/doors/mcitydoorframe.lwo
preparing audio device for output
loaded collision model models/mapobjects/doors/mcitydoorframegui.lwo
loaded collision model models/items/keycard/keycard3.lwo
preparing audio device for output
loaded collision model models/mapobjects/doors/mcitydoor.lwo
loaded collision model models/mapobjects/cpu/pullhandle.lwo
preparing audio device for output
loaded collision model models/mapobjects/doors/delelev/delelevlf.lwo
loaded collision model models/mapobjects/guiobjects/techdrpanel1/techdrpanel1.lwo
loaded collision model models/mapobjects/doors/delelev/delelevrt.lwo
loaded collision model models/mapobjects/filler/ktable.lwo
loaded collision model models/mapobjects/cpu/heater.lwo
loaded collision model models/mapobjects/cpu/heater2.lwo
preparing audio device for output
loaded collision model models/mapobjects/cpu/comrack2.lwo
loaded collision model models/mapobjects/lab/sink2/sink2.lwo
loaded collision model models/mapobjects/filler/sodamachine.lwo
loaded collision model models/mapobjects/filler/binder1.ase
preparing audio device for output
loaded collision model models/mapobjects/lab/bubbler2/bubbler2.lwo
loaded collision model models/mapobjects/filler/tbox7.ase
loaded collision model models/mapobjects/filler/binder3.ase
loaded collision model models/mapobjects/chairs/modchair/modtable.lwo
loaded collision model models/mapobjects/chairs/modchair/modseat.lwo
loaded collision model models/mapobjects/chairs/modchair/modarm.lwo
preparing audio device for output
removed 2 degenerate triangles
loaded collision model models/mapobjects/lab/newfridge/newfridge.lwo
loaded collision model models/mapobjects/filler/paper1.ase
loaded collision model models/mapobjects/filler/tbox6.ase
loaded collision model models/mapobjects/filler/tbox_open.ase
loaded collision model models/mapobjects/filler/toolchest.lwo
preparing audio device for output
loaded collision model models/mapobjects/doors/deldoor1/deldoor1frm.lwo
loaded collision model models/mapobjects/doors/deldoor1/deldoor1.lwo
loaded collision model models/mapobjects/com/modconsole2.lwo
loaded collision model models/mapobjects/com/modconsole5.lwo
preparing audio device for output
loaded collision model models/mapobjects/cpu/cpumaze1.lwo
loaded collision model models/mapobjects/doors/deldoor1/deldoor1win.lwo
preparing audio device for output
loaded collision model models/mapobjects/com/modconsole4.lwo
loaded collision model models/mapobjects/lab/gizmo2/gizmo2.lwo
preparing audio device for output
loaded collision model models/mapobjects/lab/autable/autable.lwo
loaded collision model models/mapobjects/lab/roboarm1/roboarm1.lwo
loaded collision model models/mapobjects/utility/tecknob2/tecknob2.lwo
preparing audio device for output
preparing audio device for output
loaded collision model models/mapobjects/cpu/comrack.lwo
preparing audio device for output
loaded collision model models/mapobjects/tables/gendesk/gendesk2.lwo
loaded collision model models/mapobjects/filler/tbox2.ase
loaded collision model models/mapobjects/cpu/serverplate.lwo
preparing audio device for output
loaded collision model models/mapobjects/filler/snackmachine.lwo
loaded collision model models/mapobjects/filler/tbox1.ase
preparing audio device for output
loaded collision model models/mapobjects/washroom/clamp.ase
loaded collision model models/mapobjects/washroom/urinal2.ase
loaded collision model models/mapobjects/washroom/dryer.ase
loaded collision model models/mapobjects/washroom/bsink.ase
loaded collision model models/mapobjects/washroom/soap.ase
loaded collision model models/mapobjects/washroom/toilet.ase
preparing audio device for output
loaded collision model models/mapobjects/washroom/tp.ase
preparing audio device for output
preparing audio device for output
loaded collision model models/mapobjects/arcade_machine/arcade_machine.lwo
preparing audio device for output
loaded collision model models/mapobjects/mcity/deskcomp/deskcomp.lwo
preparing audio device for output
loaded collision model models/mapobjects/skmachines/skoverhang.lwo
preparing audio device for output
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
    1 models purged from previous level,  1022 models kept.
---------------------------------------------------
----- idImageManager::EndLevelLoad -----
    0 purged from previous
  154 kept from previous
 2073 new loaded
all images loaded in  30.5 seconds
----------------------------------------
----- idSoundCache::EndLevelLoad -----
13517k referenced
  939k purged
----------------------------------------
sound: found efxs/mars_city1.efx
-----------------------------------
 54022 msec to load game/mars_city1
idRenderWorld::GenerateAllInteractions, msec = 61, staticAllocCount = 0.
interactionTable size: 2822240 bytes
29910 interaction take 3349920 bytes
------------- Warnings ---------------
during game/mars_city1...
WARNING: Couldn't load sound 'guisounds.wav' using default
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
2 warnings
signal caught: Aborted
si_code -6
Trying to exit gracefully..
--------- Game Map Shutdown ----------
--------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------
shutdown terminal support
Failed to allocate :
   size      : 20832 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 6784 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 2240 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 19776 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 1152 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 9184 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 5824 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 3424 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 4352 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 3680 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 1920 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 240 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 128 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 10620 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 1200 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 7980 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 7680 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 5220 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 9660 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 15960 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 7500 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 600 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 11400 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 2760 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 12480 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 1440 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 1200 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 3420 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 4800 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 2880 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 4800 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 4320 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 1800 bytes
   alignment : 32 bytes
   domains   : 2
Failed to allocate :
   size      : 1440 bytes
   alignment : 32 bytes
   domains   : 2
doom.x86: tnl/t_draw.c:248: bind_inputs: Assertion `inputs[i]->BufferObj->Pointer' failed.
***---End Output Log---***

At this point, I would like to mention that I am running the amd64 build of Ubuntu 10.10, and therefore I had to install the ia32-libs package to make the Doom 3 installer work.  (That was a fortunate find from another forum that helped me determine that I had to do that.)  I also installed the mesa-utils package, and ran:

glxinfo | grep direct

which informed me that Direct rendering was set to Yes.  (I should also mention that I'm downloading these packages from the Ubuntu packages site, and installing them myself - I do this so that I might have a backup of them in case any Ubuntu servers should go down for any length of time, and I should have to do a complete reinstall.)

I am running a Compaq Presario V2000 laptop (the V2321US, to be exact), and am using all default Ubuntu drivers, except on my wireless card, which is irrelevant to this problem.  I'm also running Doom 3 with Stereo speakers, and selected the "Best" sound backend (neither Alsa nor OSS give me sound, yet they still crash).  I am using the default Low Quality settings.  Is there anything else I should post here, in order to give clarity?  I patiently await the response of anyone who is able to help with this matter.

Thank you for your time.

-NeptuneNavigator2001

---

### Post by prshah on 2010-10-23
> **NeptuneNavigator2001 said:**
> 
si_code -6
Trying to exit gracefully..

Looks like a sound system error; try the suggestions from [http://www.linuxquestions.org/questions/linux-games-33/doom-3-wont-load-on-fedora-8-a-603990/](http://www.linuxquestions.org/questions/linux-games-33/doom-3-wont-load-on-fedora-8-a-603990/) (Specifically, the end of post 4).

---

### Post by NeptuneNavigator2001 on 2010-10-23
> **prshah said:**
> Looks like a sound system error; try the suggestions from [http://www.linuxquestions.org/questions/linux-games-33/doom-3-wont-load-on-fedora-8-a-603990/](http://www.linuxquestions.org/questions/linux-games-33/doom-3-wont-load-on-fedora-8-a-603990/) (Specifically, the end of post 4).

Thanks prshah, I will try that.

> **sniper420 said:**
> Doom 3 Classic game! Your drivers aint right. Did you try to update the sound and video card drivers?

I love Doom3 except that you have to use that stupid torch when it is goddman 25+ century

sniper420 - I'm using the default drivers that Ubuntu installed, and as far as I know, there wasn't an update for them yet, and I've installed about 95 MB worth of updates already.  I was wondering about sound and video - what else could it be, of course?  Looks like this will require a lot of work, but I'll start with what prshah suggested, and report back here.  Thank you.

---

### Post by perspectoff on 2010-10-23
Yeah, I couldn't do anything on my nVidia computer until I installed the proprietary nVidia drivers (using the Hardware Drivers utility).

---

### Post by NeptuneNavigator2001 on 2010-10-23
> **perspectoff said:**
> Yeah, I couldn't do anything on my nVidia computer until I installed the proprietary nVidia drivers (using the Hardware Drivers utility).

perspectoff - There is no option in my Additional Drivers utility to install proprietary ATi drivers or Connectix drivers.  The only proprietary driver it lists is the one for the old dial-up modem, which I personally will never use.

prshah - I tried the option at the end of post 4, putting +set s_driver oss at the end, and it gives me absolutely no sound whatsoever, and still crashes.  Same thing happens if I go into the Doom 3 System options before starting a new game, and set it to either Alsa or OSS.  No sound, but still a crash.  I await further help on this issue.  Thank you.

---

### Post by perspectoff on 2010-10-23
> **NeptuneNavigator2001 said:**
> There is no option in my Additional Drivers utility to install proprietary ATi drivers or Connectix drivers.  


A commonly heard problem in regards to other games, too (like Urban Terror).

My hunch is that until you solve the ATI driver problem, you won't be able to run your games. I would focus on that.

---

### Post by NeptuneNavigator2001 on 2010-10-23
> **perspectoff said:**
> A commonly heard problem in regards to other games, too (like Urban Terror).

My hunch is that until you solve the ATI driver problem, you won't be able to run your games. I would focus on that.

Okay, perspectoff.  So what should I do next?  Any ideas or recommendations?  I'm pretty new to the deeper aspects of Linux, so I'm certainly going to need some help.

EDIT: Okay, so I'm running the System Testing utility, and when it came to the audio part of the testing, it gives me the following information:

Detecting your sound device(s):

0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with Cx20468-31 at 0xc0003400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 2 at 0xc0003800, irq 17

I'm pretty sure that's incorrect.  Actually, I got the name of my sound card wrong, according to the Compaq website - it's by Conexant.  LOL, I confused it with Connectix - that's totally unrelated.  It's a Conexant CX 20468-31 AC97 sound card.  My video card is an ATI Radeon Xpress 200M.  Sorry about that confusion

EDIT 2: I found an additional repository by doing some research on fglrx.  I will report back if this helps.

EDIT 3: I guess I can't install fglrx, because the ATi Radeon Xpress 200M is now considered a legacy chip (of course - it's 5 years old at least), and therefore fglrx wouldn't work.  However, I have found out how to install some open source Edge drivers, thanks to the following link:

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)

Running glxinfo | grep direct used to reveal some information about OpenGL where it didn't before, but it's gone now, for some odd reason.  And now, Doom 3 crashes before loading the two intro videos, generating a whole new error.  Unfortunately, due to the extreme length of this new error, it overfills the capacity of the Terminal, preventing me from showing it here.  So I'll show what I can, what I was able to save using the tee command with doom3:

DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface wlan0 - 192.168.1.6/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/aaron/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
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
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: Gallium 0.4 on RS480
GL_EXTENSIONS: GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_fragment_coord_conventions GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_transpose_matrix GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_conditional_render GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays GL_OES_EGL_image GL_OES_draw_texture

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.23
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
...using GL_ARB_texture_compression
X..GL_EXT_texture_compression_s3tc not found
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
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
copy gamex86.so to /home/aaron/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Jan 16 2007
Initializing event system
...473 event definitions
Initializing class hierarchy
...142 classes, 382184 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 1600 MHz
Compiled 'removeInitialSplineAngles': 1828.9 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67875, 1357500 bytes
   Functions: 2109, 250532 bytes
   Variables: 147376 bytes
    Mem used: 2479288 bytes
 Static data: 2277552 bytes
   Allocated: 3284544 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
Opening IP socket: localhost:-1
--- Common Initialization Complete ---
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 1784
1888 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
guess failed, return default low-end VRAM setting ( 64MB VRAM )
64 MB Video Memory
Async thread started
guid set to Hs5jojVPAlI
--------- Game Map Shutdown ----------
--------------------------------------
reloading guis/mainmenu.gui.
reloading guis/restart.gui.
reloading guis/gameover.gui.
reloading guis/msg.gui.
reloading guis/takeNotes.gui.
reloading guis/intro.gui.
reloading guis/netmenu.gui.
--------- Map Initialization ---------
Map: game/mars_city1
glprogs/heatHaze.vfp
glprogs/heatHaze.vfp
glprogs/heatHazeWithMask.vfp
glprogs/heatHazeWithMask.vfp
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
462 msec to load collision data.
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
glprogs/heatHazeWithMaskAndVertex.vfp
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
    1 models purged from previous level,  1022 models kept.
---------------------------------------------------
----- idImageManager::EndLevelLoad -----
    0 purged from previous
  154 kept from previous
 2073 new loaded
all images loaded in  30.7 seconds
----------------------------------------
----- idSoundCache::EndLevelLoad -----
13517k referenced
  939k purged
----------------------------------------
sound: found efxs/mars_city1.efx
-----------------------------------
 54207 msec to load game/mars_city1
idRenderWorld::GenerateAllInteractions, msec = 37, staticAllocCount = 0.
interactionTable size: 2822240 bytes
29910 interaction take 3349920 bytes
------------- Warnings ---------------
during game/mars_city1...
WARNING: Couldn't load sound 'guisounds.wav' using default
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
2 warnings
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
--------- Game Map Shutdown ----------
--------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------
shutdown terminal support


Then at the very end, it has the following:

r300: Failed to create a transfer object, praise.
Failed to allocate :
   size      : 1048576 bytes
   alignment : 16 bytes
   domains   : 2

I have no idea what any of this means. *discouraged*

---

### Post by NeptuneNavigator2001 on 2010-10-29
Sorry for the double post, but I have an update.  There have been a few times where I've been able to get the game to the actual intro, particularly it seems to go that far if I select the main game from the Mods option - I've also noticed it in the expansion pack.  However, all attempts to get past that point result in a crash.  I tried the next-to-newest version, and that couldn't even load, stating some kind of OpenGL error.  So the game _is_ loading, but not getting very far.  Assuming the game makes it to the actual intro, the timing of the crash is random.  Could there be a bug in the rendering, as relates to my hardware and drivers?  I wonder...

---

### Post by NeptuneNavigator2001 on 2010-11-07
Alright.  After much thought, I've made a decision.  Since there is no foreseeable way for me to fix this problem in the near future, and there are still a number of other Windows-only programs that I need, I have decided to move to Ubuntu anyway, but to dual-boot to Windows whenever I want to play a game that won't work natively under Ubuntu, or use a Windows-only tool that I need, sometimes in relation to a game.  This was not an easy decision for me to make, but there is just no way around this.  Wine is still very buggy, and I'm currently stuck with a card that's not fully supported.  This is the only computer I've got for now, so it's all I can do.  If it weren't Doom 3 causing these problems, it would be something else that I'd still need, tying me down to Windows.  Not sure if I should consider this thread &quot;solved&quot; or not.  Mods can do what they wish with it.  Sorry for wasting time.

---

