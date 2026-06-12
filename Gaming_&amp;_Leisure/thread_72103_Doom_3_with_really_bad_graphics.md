---
title: "Doom 3 with really bad graphics"
date: 2005-10-05
forum: Gaming &amp; Leisure
---

### Post by frank_b on 2005-10-05
I've just installed Doom 3 and the game is running with really bad graphics, a very dark image and in slow motion.
Is this a 3D acceleration problem?
I have an ATI Radeon 9250 graphic card.
I've checked the Doom 3 GNU/Linux guide at [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/) and it talks about installing an ATI driver called "fglrx". I've tried installing a package in the ubuntu repositories called "xorg-driver-fglrx" but when I do that, the game doesn't even start.
Anyone knows what's happening?

---

### Post by Perfect Storm on 2005-10-05
Perhaps this will help you: [http://ubuntuforums.org/showthread.php?t=32495](http://ubuntuforums.org/showthread.php?t=32495)

---

### Post by frank_b on 2005-10-05
I followed the steps in the link's tutorial and didn't see any error messages.
I rebooted my computer, tried to run Doom 3 and it didn't work. 
[B]
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface ppp0 - 85.240.134.156/255.255.255.255
------ Initializing File System ------
Loaded pk4 /usr/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/renato/.doom3/base
/usr/games/doom3/base
/usr/games/doom3/base/pak007.pk4 (38 files)
/usr/games/doom3/base/pak006.pk4 (48 files)
/usr/games/doom3/base/pak005.pk4 (63 files)
/usr/games/doom3/base/pak004.pk4 (5137 files)
/usr/games/doom3/base/pak003.pk4 (4676 files)
/usr/games/doom3/base/pak002.pk4 (6120 files)
/usr/games/doom3/base/pak001.pk4 (8972 files)
/usr/games/doom3/base/pak000.pk4 (2698 files)
/usr/games/doom3/base/game03.pk4 (2 files)
/usr/games/doom3/base/game02.pk4 (2 files)
/usr/games/doom3/base/game01.pk4 (2 files)
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
Using 8/8/8 Color bits, 8 Alpha bits, 16 depth, 8 stencil display.
GL_RENDERER: Mesa GLX Indirect
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias
Fatal X Error:
Major opcode of failed request: 137
Minor opcode of failed request: 2
Serial number of failed request: 55
XF86DGANoDirectVideoMode
------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.8
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
X..GL_ARB_texture_compression not found
X..GL_EXT_texture_filter_anisotropic not found
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
X..GL_EXT_texture3D not found
X..GL_EXT_stencil_wrap not found
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
X..GL_ARB_vertex_buffer_object not found
X..GL_ARB_vertex_program not found
X..GL_ARB_fragment_program not found
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Not available.
----- R_ReloadARBPrograms -----
glprogs/test.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/test.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/shadow.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/R200_interaction.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_bumpAndLight.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_specularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseAndSpecularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Fatal X Error:
Major opcode of failed request: 137
Minor opcode of failed request: 2
Serial number of failed request: 66
XF86DGANoDirectVideoMode
[/B]
I've tried running Wolfenstein Enemy Territory (which was running fine prior to this) to check for any changes and now this one also doesn't run.
[B]ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/renato/.etwolf/etmain/zazForplay.pk3 (24 files)
/home/renato/.etwolf/etmain/zazForplay.e1f2b6d4.pk3 (24 files)
/home/renato/.etwolf/etmain/UrbanTerritory2.pk3 (178 files)
/home/renato/.etwolf/etmain/te_valhalla.pk3 (56 files)
/home/renato/.etwolf/etmain/temple_final.pk3 (57 files)
/home/renato/.etwolf/etmain/tc_base.pk3 (63 files)
/home/renato/.etwolf/etmain/SuperGoldrush_Final.pk3 (170 files)
/home/renato/.etwolf/etmain/subway.pk3 (174 files)
/home/renato/.etwolf/etmain/soa_20map.pk3 (4 files)
/home/renato/.etwolf/etmain/sixpack.pk3 (2 files)
/home/renato/.etwolf/etmain/schoko60.pk3 (4 files)
/home/renato/.etwolf/etmain/rtcc2.pk3 (41 files)
/home/renato/.etwolf/etmain/pakpanza.pk3 (21 files)
/home/renato/.etwolf/etmain/pakpanza.38176a8f.pk3 (21 files)
/home/renato/.etwolf/etmain/paknw15.pk3 (2 files)
/home/renato/.etwolf/etmain/pak4300.pk3 (2 files)
/home/renato/.etwolf/etmain/oilraid_b1.pk3 (106 files)
/home/renato/.etwolf/etmain/nw6map.pk3 (1 files)
/home/renato/.etwolf/etmain/nw10.pk3 (1 files)
/home/renato/.etwolf/etmain/mlb_d_day.pk3 (121 files)
/home/renato/.etwolf/etmain/LOL_FUNPARK.pk3 (115 files)
/home/renato/.etwolf/etmain/LNATrickjump.pk3 (16 files)
/home/renato/.etwolf/etmain/KoB_Trickjump-Final-1.0.pk3 (64 files)
/home/renato/.etwolf/etmain/JVserver.pk3 (56 files)
/home/renato/.etwolf/etmain/jvparkb4.pk3 (15 files)
/home/renato/.etwolf/etmain/icewind210.pk3 (1 files)
/home/renato/.etwolf/etmain/icewind110.pk3 (1 files)
/home/renato/.etwolf/etmain/et_beach.pk3 (177 files)
/home/renato/.etwolf/etmain/ds_bunkers_b2.pk3 (137 files)
/home/renato/.etwolf/etmain/crazy.pk3 (2 files)
/home/renato/.etwolf/etmain/cortexbeta.pk3 (358 files)
/home/renato/.etwolf/etmain/caen.pk3 (82 files)
/home/renato/.etwolf/etmain/baserace_b3.pk3 (131 files)
/home/renato/.etwolf/etmain/am_hydro_dam_b1.pk3 (52 files)
/home/renato/.etwolf/etmain
/usr/games/enemy-territory/etmain/venice.pk3 (330 files)
/usr/games/enemy-territory/etmain/supplydepot2.pk3 (46 files)
/usr/games/enemy-territory/etmain/saberpeak_final.pk3 (243 files)
/usr/games/enemy-territory/etmain/saberpeak_etpro.pk3 (3 files)
/usr/games/enemy-territory/etmain/resurrection.pk3 (305 files)
/usr/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/games/enemy-territory/etmain/mp_tram.pk3 (83 files)
/usr/games/enemy-territory/etmain/mp_pak10map3.pk3 (2 files)
/usr/games/enemy-territory/etmain/mp_pak10map2.pk3 (565 files)
/usr/games/enemy-territory/etmain/mp_pak10map.pk3 (239 files)
/usr/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/games/enemy-territory/etmain/mp_assault_rc1.pk3 (177 files)
/usr/games/enemy-territory/etmain/mml_helmsdeep_a3.pk3 (125 files)
/usr/games/enemy-territory/etmain/marketgarden_et.pk3 (275 files)
/usr/games/enemy-territory/etmain/et_tank_beta3.pk3 (186 files)
/usr/games/enemy-territory/etmain/byzantine.pk3 (216 files)
/usr/games/enemy-territory/etmain
----------------------
8837 files in pk3 files
^3WARNING: profile.pid found for profile 'Kamizake' - system settings will revert to defaults
execing default.cfg
couldn't exec language.cfg
execing profiles/Kamizake/etconfig.cfg
r_smp is unsafe. Check com_crashed.
r_mode is unsafe. Check com_crashed.
r_depthbits is unsafe. Check com_crashed.
r_stencilbits is unsafe. Check com_crashed.
r_stereo is unsafe. Check com_crashed.
r_colorbits is unsafe. Check com_crashed.
r_texturebits is unsafe. Check com_crashed.
r_clampToEdge is unsafe. Check com_crashed.
r_ext_texture_env_add is unsafe. Check com_crashed.
r_nv_fogdist_mode is unsafe. Check com_crashed.
r_ext_NV_fog_dist is unsafe. Check com_crashed.
r_ext_texture_filter_anisotropic is unsafe. Check com_crashed.
r_ati_fsaa_samples is unsafe. Check com_crashed.
r_ati_truform_pointmode is unsafe. Check com_crashed.
r_ati_truform_normalmode is unsafe. Check com_crashed.
r_ati_truform_tess is unsafe. Check com_crashed.
r_ext_ATI_pntriangles is unsafe. Check com_crashed.
r_glIgnoreWicked3D is unsafe. Check com_crashed.
r_ext_compiled_vertex_array is unsafe. Check com_crashed.
r_ext_multitexture is unsafe. Check com_crashed.
r_ext_gamma_control is unsafe. Check com_crashed.
r_ext_compressed_textures is unsafe. Check com_crashed.
r_allowExtensions is unsafe. Check com_crashed.
r_glDriver is unsafe. Check com_crashed.
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect
***********************************************************
You are using software Mesa (no hardware acceleration)!
Driver DLL used: libGL.so.1
If this is intentional, add
"+set r_allowSoftwareGL 1"
to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...
[/B]
I've check the messages following the tutorial and in page 7 ([http://ubuntuforums.org/showthread.php?t=32495&page=7](http://ubuntuforums.org/showthread.php?t=32495&page=7)) I saw someone refering to a link ([http://ubuntulinux.org/wiki/BinaryDriverHowto](http://ubuntulinux.org/wiki/BinaryDriverHowto)) I checked and then remembered seeing in another tutorial saying that my graphic card doesn't need 3D acceleration drivers.
Is the driver I installed a 3D one?
Also, in the tutorial it talks about having "linux kernel headers" installed. I've checked synaptic and I have a packaged called "linux-kernel-headers" installed but  there are others called just "linux-headers-[version]" that say "linux kernel headers" in the description and none of them are installed. Do I have what the person who wrote the tutorial wants? Does this make any difference?

---

### Post by seethru on 2005-10-05
what happens when you run glxgears?

---

### Post by Curlydave on 2005-10-05
I wouldn't bother with Doom3 on a 9250 in Linux. In Windows it's more than pushing it, but in Linux it will probably be awful; ATI cards do not run well in Linux. Notable problems include poor perfomance and lack of AA, AF, Vsync and TB.

---

### Post by frank_b on 2005-10-06
I'm sorry to hear that Doom 3 won't probably run well on my graphic card... :( (Thanks for the tip anyway) :???: 
This is what I get when I execute the command "glxgears -info":
[B]
GL_MAX_VIEWPORT_DIMS=4096/4096
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (1.5 Mesa 6.2.1)
GL_VENDOR     = Mesa project: [www.mesa3d.org](www.mesa3d.org)
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias
1473 frames in 5.0 seconds = 294.600 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1582 frames in 5.0 seconds = 316.400 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
1695 frames in 5.0 seconds = 339.000 FPS
X connection to :0.0 broken (explicit kill or server shutdown).[/B]
By the way, since it is not a package, is it possibly to undo/uninstall whatever the ATI driver installation script I run did/installed and just put it back as it was before?

---

### Post by seethru on 2005-10-06
yikes....339fps, I know it's not a benchmark but that isn't great in comparison...I don't know much about ATI...but why is it using Mesa GLX to render it...

---

### Post by frank_b on 2005-10-06
OK, so my 3D card is not that good... (Didn't know that, it's my first one...)

(It has 128 MB to be more precise.)

But, once again, to make sure someone sees this, how do I put things back as they were? How do I uninstall the driver?

---

### Post by Yagisan on 2005-10-06
[QUOTE=frank_b]GL_RENDERER   = Mesa GLX Indirect[/QUOTE] The problem you are having can be traced back to this. Currently your system is using a software video driver as indicated by the mesa glx indirect for your gl renderer (think software mode directx). Have you tried this 
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) ? that should get you set up and ready to go.

---

### Post by seethru on 2005-10-06
[QUOTE=Yagisan]The problem you are having can be traced back to this. Currently your system is using a software video driver as indicated by the mesa glx indirect for your gl renderer (think software mode directx). Have you tried this 
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) ? that should get you set up and ready to go.[/QUOTE]
yes, thats what I thought was going on, like Yagisan has said, follow those directions and you should see a performance improvement.

---

### Post by frank_b on 2005-10-06
Al'right!!!

It worked! :)

This is what I get now when I run the "glxgears -info" command:


[B]GL_MAX_VIEWPORT_DIMS=2048/2048
GL_RENDERER   = RADEON 8500 Prototype DDR Pentium 4 (SSE2) (FireGL) (GNU_ICD)
GL_VERSION    = 1.3.4769 (X4.3.0-8.8.25)
GL_VENDOR     = ATI Technologies Inc.
GL_EXTENSIONS = GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_ATI_element_array GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_map_object_buffer GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_vertex_array_object GL_ATI_vertex_attrib_array_object GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_texgen_reflection GL_NV_blend_square GL_NV_occlusion_query GL_SGI_color_matrix GL_SGIS_texture_edge_clamp GL_SGIS_texture_border_clamp GL_SGIS_texture_lod GL_SGIS_generate_mipmap GL_SUN_multi_draw_arrays
2390 frames in 5.0 seconds = 478.000 FPS
2828 frames in 5.0 seconds = 565.600 FPS
2829 frames in 5.0 seconds = 565.800 FPS
2828 frames in 5.0 seconds = 565.600 FPS
2829 frames in 5.0 seconds = 565.800 FPS
2829 frames in 5.0 seconds = 565.800 FPS[/B]


The frame rate has really improved.

I can run Doom 3 (faster) now, although yet slowly and with a strange sound, but as it was said to me, it's a problem of my graphic card beeing too slow for the game...

But the rest has improved a lot!

I can now run Enemy Territory a lot faster (I was begining to suspect that my LCD monitor was responsible for the game beeing a little slow...) and I can see, when I switch between windows, that the refresh rate of my monitor in general has improved also! :) yeah!

Thanks a lot Yagisan and seethru! :)

I guess that the post at [https://wiki.ubuntu.com//BinaryDriverHowto](https://wiki.ubuntu.com//BinaryDriverHowto) is not correct or at least not very clear, since that, in my case, it really is better to install the driver... (I'll e-mail the responsible).

But (sorry for refering this once again) what about the driver I downloaded from the ATI site and installed ([http://ubuntuforums.org/showthread.php?t=32495)](http://ubuntuforums.org/showthread.php?t=32495))... is it possible to uninstall it? (I've tried uninstalling the one I got from the ubuntu repositories but this seems to be the one I'm using right now...)

---

