---
title: "Doom 3 display problems"
date: 2008-09-08
forum: Gaming &amp; Leisure
---

### Post by chungy on 2008-09-08
I'm trying to play Doom 3, however the display doesn't look so great: [http://img209.imageshack.us/my.php?image=doom3xd7.png](http://img209.imageshack.us/my.php?image=doom3xd7.png)

I'm running Xubuntu 8.04 on a Gateway ML6720 laptop... it has an Intel Mobile GM965/GL960 Integrated Graphics Controller.  I know it's not a particularly good card in the first place to run Doom 3, but it should be fine on low settings at least...

---

### Post by grossaffe on 2008-09-08
> **chungy said:**
> I'm trying to play Doom 3, however the display doesn't look so great: [http://img209.imageshack.us/my.php?image=doom3xd7.png](http://img209.imageshack.us/my.php?image=doom3xd7.png)

I'm running Xubuntu 8.04 on a Gateway ML6720 laptop... it has an Intel Mobile GM965/GL960 Integrated Graphics Controller.  I know it's not a particularly good card in the first place to run Doom 3, but it should be fine on low settings at least...

I think its dark because you're missing textures.  I installed Doom3 but didn't put in one of the pk4 files so I had some missing textures which made everything overly dark.  Open up the console and see if there are any errors being output.

---

### Post by chungy on 2008-09-08
I copied all the pk4 files the README instructed me to do, and there aren't any errors shown in the console aside from "WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video"

---

### Post by grossaffe on 2008-09-08
> **chungy said:**
> I copied all the pk4 files the README instructed me to do, and there aren't any errors shown in the console aside from "WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video"
The instructions I followed left out one of the pk4 files which is why I had the problems I did.  Check to see that you have them all from pak000.pk4 through pak008.pk4

---

### Post by DoktorSeven on 2008-09-08
> **chungy said:**
> I copied all the pk4 files the README instructed me to do, and there aren't any errors shown in the console aside from "WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video"

That's just a developer warning (to themselves, not us) from the engine that's exactly what it sounds like: the path has uppercase characters and therefore might cause problems on case-sensitive non-Windows systems in the future (if they make revisions to not do a case-insensitive search).

Doom 3 is dark, period.  Check out the brightness slider in preferences plus you might want to fiddle with r_gamma from the Doom3 terminal (hit ~ to bring it down).  

Plus any modern, graphics-intensive game can have issues in Linux with non-Nvidia/ATI graphics cards, which might be your problem as well.

---

### Post by grossaffe on 2008-09-08
> **DoktorSeven said:**
> That's just a developer warning (to themselves, not us) from the engine that's exactly what it sounds like: the path has uppercase characters and therefore might cause problems on case-sensitive non-Windows systems in the future (if they make revisions to not do a case-insensitive search).

Doom 3 is dark, period.  Check out the brightness slider in preferences plus you might want to fiddle with r_gamma from the Doom3 terminal (hit ~ to bring it down).  

Plus any modern, graphics-intensive game can have issues in Linux with non-Nvidia/ATI graphics cards, which might be your problem as well.

In that picture, it looks like everything that does not produce its own light is black.

---

### Post by chungy on 2008-09-08
> **grossaffe said:**
> The instructions I followed left out one of the pk4 files which is why I had the problems I did.  Check to see that you have them all from pak000.pk4 through pak008.pk4

The instructions from the (Linux native) installer say just to copy pak00{0,1,2,3,4}.pk4; the rest of the pk4 files (which are included already) are update packs which replace old game resources in the earlier files.  The copy I'm using comes from Steam specifically, but this shouldn't really matter (I also had the game running fine on my brother's computer which has normal Ubuntu 8.04, though different hardware (lower model Intel graphics, at that)).  I also copied the pk4 from Doom 3: Resurrection of Evil, though the screenshot is from the base game...

Interestingly, I ran the game through Wine and the exact same problem manifests.  I don't know whether it's a Doom 3 bug, driver bug, or just bad hardware; I don't have any issues in other 3D accelerated games (though Doom 3 is the most advanced one I've tried, the next best game would be Return to Castle Wolfenstein and Sauerbraten).  I also deleted the preinstalled Windows operating system that came on my computer (the same day I got it), so I can't even test whether the game would look fine in Windows itself (well I have both the Windows disc and recovery disc still, if I really cared so much)...

If this can't be resolved, oh well I suppose.  I was looking forward to actually playing the full version of Doom 3, but I can wait until I get a better computer I suppose.

---

### Post by grossaffe on 2008-09-08
It is a wierd problem.  I still say it looks like you're missing textures, though.  How are they missing?  I don't know.

anyways, Why don't you copy your entire console readout so people can look through it?  I may not be able to find anything since I'm relatively new to linux (under a year), but someone else may see a problem.

---

### Post by chungy on 2008-09-08
I suppose, but I didn't see anything of much importance... this is going to be a massive post, heh
```
$ doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface wlan0 - 192.168.1.2/255.255.255.0
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
/home/mike/.doom3/base
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
XFree86-VidModeExtension: not fullscreen, ignored
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.15
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 67728 bytes )
allocated a mix buffer of 49152 bytes
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
   maxTextureAnisotropy: 2.000000
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
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
copy gamex86.so to /home/mike/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Jan 16 2007
Initializing event system
...473 event definitions
Initializing class hierarchy
...142 classes, 382184 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 1467 MHz
Compiled 'removeInitialSplineAngles': 1938.5 ms
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
pid: 18548
1008 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
guess failed, return default low-end VRAM setting ( 64MB VRAM )
64 MB Video Memory
Async thread started
guid set to uJSpaZhZKm8
idUsercmdGenLocal::MouseMove: Ignoring ridiculous mouse delta.
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
425 msec to load collision data.
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
all images loaded in  18.6 seconds
----------------------------------------
----- idSoundCache::EndLevelLoad -----
13517k referenced
  939k purged
----------------------------------------
sound: found efxs/mars_city1.efx
-----------------------------------
 35084 msec to load game/mars_city1
idRenderWorld::GenerateAllInteractions, msec = 37, staticAllocCount = 0.
interactionTable size: 2822240 bytes
29910 interaction take 3349920 bytes
------------- Warnings ---------------
during game/mars_city1...
WARNING: Couldn't load sound 'guisounds.wav' using default
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
2 warnings
idUsercmdGenLocal::MouseMove: Ignoring ridiculous mouse delta.
idUsercmdGenLocal::MouseMove: Ignoring ridiculous mouse delta.
idUsercmdGenLocal::MouseMove: Ignoring ridiculous mouse delta.
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
```

---

### Post by grossaffe on 2008-09-09
```
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
**X..GL_EXT_texture_compression_s3tc not found**
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 2.000000
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
**X..GL_EXT_shared_texture_palette not found**
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
[b]X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found[/b]
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
**X..EXT_depth_bounds_test not found**

```
These lines in your console look suspicious, and they happen to involve textures...

---

### Post by Sockerdrickan on 2008-09-09
It's your so called gpu's fault I'm afraid :P Intel Mobile GM965/GL960 Integrated Graphics Controller

---

### Post by grossaffe on 2008-09-09
> **Tux0r said:**
> It's your so called gpu's fault I'm afraid :P Intel Mobile GM965/GL960 Integrated Graphics Controller

can't be any worse than an nVidia Geforce 2, can it?

---

### Post by Sockerdrickan on 2008-09-10
either way the linux driver isn't good enough for your game.

---

### Post by Perfect Storm on 2008-09-10
> **grossaffe said:**
> can't be any worse than an nVidia Geforce 2, can it?

I tend to say yes (we talking about gaming) - but they properly in the same category.

---

### Post by Dan_Dranath999 on 2008-09-23
Mmmh. I used to play Doom 3 **on Gutsy**, the game and 3 or 4 MODS, all without issues.

Now, **on Hardy**, i can't play at FULLSCREEN, (the image is not complete) **and can't play the mods at all!**  

(when i get home, i'll try to post the errors showing up in Terminal)

---

### Post by swoody on 2008-09-23
Hey, how do you guys like DOOM 3? I played the originals, and I had meant to take a look at 3, but never got around to it.

---

### Post by swoody on 2008-09-23
Oh, and I had the same problem trying to get WoW to play on my laptop with a similar GPU, and it was horrible compared to playing it on Windoze (1/2 the frames-per-second) :(

---

### Post by Dan_Dranath999 on 2008-09-25
gotta try it. I love gunning down zombies. (is that an accurate expression? English is not my primary language)

---

### Post by realzippy on 2008-09-25
I had the same issue,1 year ago,black textures in Doom 3.
Missing dependencies?Suggest to install blender (3D modeller),
googleearth.Even I do not know why,my Doom3 worked after this...

You can also install ubuntustudio with all that 3D stuff,doom3 will work
correctly out of the box..

---

### Post by chungy on 2008-09-25
That sounds very strange, I'm guessing that they have some dependency Doom 3 also requires.  It's worth a shot I suppose, the worst that can happen is that Doom 3 still doesn't run correctly :)

---

### Post by chungy on 2008-09-25
Neither of them had any dependencies I didn't already have, and it didn't help Doom 3.

---

### Post by Crafty Kisses on 2008-09-25
How about the results of this command:
```
glxinfo
```

---

### Post by chungy on 2008-09-25
```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

