---
title: "I seem to have broken my 3D games"
date: 2009-11-14
forum: Gaming &amp; Leisure
---

### Post by samh785 on 2009-11-14
Edit: Here's a clue to the problem-
When I run the program as root, the game works fine


I'm running Ubuntu 9.10, and my computer specs are in my signature. I've been messing around with the nvidia-190 driver and in the process I seem to make all my games that are in 3D have issues. Take tremulous for example: I can start it, and I can load the levels but some of the walls are rendered in black, and I get a maximum of like 5 FPS...

Here is the result of loading tremulous in the terminal:
```
sam@system76-pc:~$ tremulous
tremulous 1.1.0 linux-x86_64 Sep  6 2008
----- FS_Startup -----
Current search path:
/home/sam/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
execing autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 7: 1152 864
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
Using 8/8/8 Color bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce G 105M/PCI/SSE2
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce G 105M/PCI/SSE2
GL_VERSION: 3.0.0 NVIDIA 185.18.36
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_framebuffer_object GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_vertex_array_object GL_ARB_vertex_program GL_ARB_window_pos GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_geometry_shader4 GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_packed_depth_stencil GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: 7, 1152 x 864 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/uncreation.shader'
...loading 'scripts/q3map2_tremor.shader'
...loading 'scripts/tremor.shader'
...loading 'scripts/transit.shader'
...loading 'scripts/niveus.shader'
...loading 'scripts/nexus6.shader'
...loading 'scripts/karith.shader'
...loading 'scripts/atcs.shader'
...loading 'scripts/arachnid2.shader'
...loading 'scripts/jetpack.shader'
...loading 'scripts/core.shader'
...loading 'scripts/flame.shader'
...loading 'scripts/misc.shader'
...loading 'scripts/common-trem.shader'
...loading 'scripts/titan.shader'
...loading 'scripts/water.shader'
...loading 'scripts/displays.shader'
...loading 'scripts/plant_life.shader'
...loading 'scripts/stasis.shader'
...loading 'scripts/booster.shader'
...loading 'scripts/eggpod.shader'
...loading 'scripts/medistat.shader'
...loading 'scripts/mgturret.shader'
...loading 'scripts/reactor.shader'
...loading 'scripts/telenode.shader'
...loading 'scripts/trapper.shader'
...loading 'scripts/overmind.shader'
...loading 'scripts/tesla.shader'
...loading 'scripts/dcc.shader'
...loading 'scripts/hive.shader'
...loading 'scripts/level2.shader'
...loading 'scripts/human.shader'
...loading 'scripts/null.shader'
...loading 'scripts/weapons.shader'
...loading 'scripts/conkit.shader'
...loading 'scripts/advckit.shader'
...loading 'scripts/psaw.shader'
...loading 'scripts/mdriver.shader'
...loading 'scripts/flamer.shader'
...loading 'scripts/crosshairs.shader'
...loading 'scripts/grenade.shader'
...loading 'scripts/splash.shader'
...loading 'scripts/marks.shader'
...loading 'scripts/sprites.shader'
...loading 'scripts/muzzleflashes.shader'
----- finished R_Init -----
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "alsa".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  512
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x2bcdb60 dma buffer
No background file.
----------------------
Sound intialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1075 jump table targets
compiling ui
running assembler < /tmp/ui.s_O0jOOF > /tmp/ui.o_behyb6
done
computing jump table
VM file ui compiled to 6261955 bytes of code (0x7f5fe3a33000 - 0x7f5fe402bcc3)
ui loaded in 4596672 bytes on the hunk
UI menu load time = 188 milli seconds
UI menu load time = 16 milli seconds
UI menu load time = 13 milli seconds
--- Common Initialization Complete ---
Opening IP socket: localhost:30720
Hostname: system76-pc
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Resolving master.tremulous.net
master.tremulous.net resolved to 67.222.136.108:30710
74.86.23.18:50000 resolved to 74.86.23.18:-15536
----- FS_Startup -----
Current search path:
/home/sam/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

handle 1: sound/ui/heartbeat.wav
----------------------
4160 files in pk3 files
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce G 105M/PCI/SSE2
GL_VERSION: 3.0.0 NVIDIA 185.18.36
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_framebuffer_object GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_vertex_array_object GL_ARB_vertex_program GL_ARB_window_pos GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_geometry_shader4 GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_packed_depth_stencil GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: 7, 1152 x 864 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/uncreation.shader'
...loading 'scripts/q3map2_tremor.shader'
...loading 'scripts/tremor.shader'
...loading 'scripts/transit.shader'
...loading 'scripts/niveus.shader'
...loading 'scripts/nexus6.shader'
...loading 'scripts/karith.shader'
...loading 'scripts/atcs.shader'
...loading 'scripts/arachnid2.shader'
...loading 'scripts/jetpack.shader'
...loading 'scripts/core.shader'
...loading 'scripts/flame.shader'
...loading 'scripts/misc.shader'
...loading 'scripts/common-trem.shader'
...loading 'scripts/titan.shader'
...loading 'scripts/water.shader'
...loading 'scripts/displays.shader'
...loading 'scripts/plant_life.shader'
...loading 'scripts/stasis.shader'
...loading 'scripts/booster.shader'
...loading 'scripts/eggpod.shader'
...loading 'scripts/medistat.shader'
...loading 'scripts/mgturret.shader'
...loading 'scripts/reactor.shader'
...loading 'scripts/telenode.shader'
...loading 'scripts/trapper.shader'
...loading 'scripts/overmind.shader'
...loading 'scripts/tesla.shader'
...loading 'scripts/dcc.shader'
...loading 'scripts/hive.shader'
...loading 'scripts/level2.shader'
...loading 'scripts/human.shader'
...loading 'scripts/null.shader'
...loading 'scripts/weapons.shader'
...loading 'scripts/conkit.shader'
...loading 'scripts/advckit.shader'
...loading 'scripts/psaw.shader'
...loading 'scripts/mdriver.shader'
...loading 'scripts/flamer.shader'
...loading 'scripts/crosshairs.shader'
...loading 'scripts/grenade.shader'
...loading 'scripts/splash.shader'
...loading 'scripts/marks.shader'
...loading 'scripts/sprites.shader'
...loading 'scripts/muzzleflashes.shader'
----- finished R_Init -----
Loading vm file vm/ui.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1075 jump table targets
compiling ui
running assembler < /tmp/ui.s_FkxWr3 > /tmp/ui.o_HfclI0
done
computing jump table
VM file ui compiled to 6261955 bytes of code (0x7f5fe3a33000 - 0x7f5fe402bcc3)
ui loaded in 4596672 bytes on the hunk
UI menu load time = 187 milli seconds
UI menu load time = 15 milli seconds
UI menu load time = 14 milli seconds
Loading vm file vm/cgame.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1284 jump table targets
compiling cgame
running assembler < /tmp/cgame.s_jei5v2 > /tmp/cgame.o_uSOPj4
done
computing jump table
VM file cgame compiled to 10577810 bytes of code (0x7f5fe29db000 - 0x7f5fe33f1792)
cgame loaded in 34239040 bytes on the hunk
UI menu load time = 47 milli seconds
...loading 'scripts/buildables.trail'
...loading 'scripts/weapons.trail'
...loading 'scripts/uncreation.particle'
...loading 'scripts/tremor.particle'
...loading 'scripts/niveus.particle'
...loading 'scripts/nexus6.particle'
...loading 'scripts/karith.particle'
...loading 'scripts/atcs.particle'
...loading 'scripts/arachnid2.particle'
...loading 'scripts/jetpack.particle'
...loading 'scripts/misc.particle'
...loading 'scripts/weapons.particle'
...loading 'scripts/buildables.particle'
stitched 0 LoD cracks
...loaded 3971 faces, 8 meshes, 0 trisurfs, 0 flares
CL_InitCGame:  4.38 seconds
9 msec to draw all images
Com_TouchMemory: 0 msec
Roflboom^7 entered the game
^1Your client is out of date. Updating your client will allow you to become an admin on servers and download maps much more quickly. Please replace your client executable with the one at ^2http://trem.tjw.org/backport/^1 and reconnect. rms^7 was bitten by ^tE^gu^tr^gi^td^gi^tc^7
^5.^7User#0^7 should leave !!!jirka tournamentkox!!!^7's buildings alone
!!!jirka tournamentkox!!!^7 was chaingunned by The Manix [FR]^7
^2NOM ^tNOM ^e^qNOM^7 was mauled by ^!W^7^#o^!l^#f^!<^#B^!r^#>^7's Tyrant
KNACH   ^7 disconnected
Polaco^7 was mauled by ^9(^4LS^9) ^3^2Korigen^7's Tyrant
sereale killer^7 was mauled by ^9(^4LS^9) ^3^2Korigen^7's Tyrant
^1code^7monkey^7 was gunned down by de man^7
de man^7 was mauled by ^9(^4LS^9) ^3^2Korigen^7's Tyrant
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
sam@system76-pc:~$ 

```Now I'm not very savvy about these things, but it seems to me that this part is the most relevant to my issue:
```
Initializing OpenGL display
...setting mode 7: 1152 864
[B]NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
Using 8/8/8 Color bits, 24 depth, 8 stencil display.[/B]
GL_RENDERER: GeForce G 105M/PCI/SSE2
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce G 105M/PCI/SSE2
GL_VERSION: 3.0.0 NVIDIA 185.18.36
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_framebuffer_object GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_vertex_array_object GL_ARB_vertex_program GL_ARB_window_pos GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_geometry_shader4 GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_packed_depth_stencil GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4
```Any help at all is appreciated! And as always- Thanks in advance! :D

Edit: Here is the terminal version of running the game as root in which the game runs fine:
```
sam@system76-pc:~$ sudo su
root@system76-pc:/home/sam# tremulous
tremulous 1.1.0 linux-x86_64 Sep  6 2008
----- FS_Startup -----
Current search path:
/root/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
execing autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
Using 8/8/8 Color bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce G 105M/PCI/SSE2
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce G 105M/PCI/SSE2
GL_VERSION: 3.0.0 NVIDIA 185.18.36
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_instanced GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_framebuffer_object GL_ARB_geometry_shader4 GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NV_vertex_buffer_unified_memory GL_NV_shader_buffer_load GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/uncreation.shader'
...loading 'scripts/q3map2_tremor.shader'
...loading 'scripts/tremor.shader'
...loading 'scripts/transit.shader'
...loading 'scripts/niveus.shader'
...loading 'scripts/nexus6.shader'
...loading 'scripts/karith.shader'
...loading 'scripts/atcs.shader'
...loading 'scripts/arachnid2.shader'
...loading 'scripts/jetpack.shader'
...loading 'scripts/core.shader'
...loading 'scripts/flame.shader'
...loading 'scripts/misc.shader'
...loading 'scripts/common-trem.shader'
...loading 'scripts/titan.shader'
...loading 'scripts/water.shader'
...loading 'scripts/displays.shader'
...loading 'scripts/plant_life.shader'
...loading 'scripts/stasis.shader'
...loading 'scripts/booster.shader'
...loading 'scripts/eggpod.shader'
...loading 'scripts/medistat.shader'
...loading 'scripts/mgturret.shader'
...loading 'scripts/reactor.shader'
...loading 'scripts/telenode.shader'
...loading 'scripts/trapper.shader'
...loading 'scripts/overmind.shader'
...loading 'scripts/tesla.shader'
...loading 'scripts/dcc.shader'
...loading 'scripts/hive.shader'
...loading 'scripts/level2.shader'
...loading 'scripts/human.shader'
...loading 'scripts/null.shader'
...loading 'scripts/weapons.shader'
...loading 'scripts/conkit.shader'
...loading 'scripts/advckit.shader'
...loading 'scripts/psaw.shader'
...loading 'scripts/mdriver.shader'
...loading 'scripts/flamer.shader'
...loading 'scripts/crosshairs.shader'
...loading 'scripts/grenade.shader'
...loading 'scripts/splash.shader'
...loading 'scripts/marks.shader'
...loading 'scripts/sprites.shader'
...loading 'scripts/muzzleflashes.shader'
----- finished R_Init -----
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "alsa".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  512
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x1c751e0 dma buffer
No background file.
----------------------
Sound intialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1075 jump table targets
compiling ui
running assembler < /tmp/ui.s_5UIoc5 > /tmp/ui.o_XevdJd
done
computing jump table
VM file ui compiled to 6261955 bytes of code (0x7fa6a2690000 - 0x7fa6a2c88cc3)
ui loaded in 4596672 bytes on the hunk
UI menu load time = 210 milli seconds
UI menu load time = 15 milli seconds
UI menu load time = 11 milli seconds
--- Common Initialization Complete ---
Opening IP socket: localhost:30720
Hostname: system76-pc
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
177 servers listed in browser with 445 players.
30 servers not listed due to packet loss or pings higher than 800
Resolving master.tremulous.net
master.tremulous.net resolved to 67.222.136.108:30710
74.86.23.18:50000 resolved to 74.86.23.18:-15536
----- FS_Startup -----
Current search path:
/root/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

handle 1: sound/ui/heartbeat.wav
----------------------
4160 files in pk3 files
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce G 105M/PCI/SSE2
GL_VERSION: 3.0.0 NVIDIA 185.18.36
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_instanced GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_framebuffer_object GL_ARB_geometry_shader4 GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NV_vertex_buffer_unified_memory GL_NV_shader_buffer_load GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/uncreation.shader'
...loading 'scripts/q3map2_tremor.shader'
...loading 'scripts/tremor.shader'
...loading 'scripts/transit.shader'
...loading 'scripts/niveus.shader'
...loading 'scripts/nexus6.shader'
...loading 'scripts/karith.shader'
...loading 'scripts/atcs.shader'
...loading 'scripts/arachnid2.shader'
...loading 'scripts/jetpack.shader'
...loading 'scripts/core.shader'
...loading 'scripts/flame.shader'
...loading 'scripts/misc.shader'
...loading 'scripts/common-trem.shader'
...loading 'scripts/titan.shader'
...loading 'scripts/water.shader'
...loading 'scripts/displays.shader'
...loading 'scripts/plant_life.shader'
...loading 'scripts/stasis.shader'
...loading 'scripts/booster.shader'
...loading 'scripts/eggpod.shader'
...loading 'scripts/medistat.shader'
...loading 'scripts/mgturret.shader'
...loading 'scripts/reactor.shader'
...loading 'scripts/telenode.shader'
...loading 'scripts/trapper.shader'
...loading 'scripts/overmind.shader'
...loading 'scripts/tesla.shader'
...loading 'scripts/dcc.shader'
...loading 'scripts/hive.shader'
...loading 'scripts/level2.shader'
...loading 'scripts/human.shader'
...loading 'scripts/null.shader'
...loading 'scripts/weapons.shader'
...loading 'scripts/conkit.shader'
...loading 'scripts/advckit.shader'
...loading 'scripts/psaw.shader'
...loading 'scripts/mdriver.shader'
...loading 'scripts/flamer.shader'
...loading 'scripts/crosshairs.shader'
...loading 'scripts/grenade.shader'
...loading 'scripts/splash.shader'
...loading 'scripts/marks.shader'
...loading 'scripts/sprites.shader'
...loading 'scripts/muzzleflashes.shader'
----- finished R_Init -----
Loading vm file vm/ui.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1075 jump table targets
compiling ui
running assembler < /tmp/ui.s_OsILgQ > /tmp/ui.o_oUkkOs
done
computing jump table
VM file ui compiled to 6261955 bytes of code (0x7fa6a2690000 - 0x7fa6a2c88cc3)
ui loaded in 4596672 bytes on the hunk
UI menu load time = 170 milli seconds
UI menu load time = 15 milli seconds
UI menu load time = 11 milli seconds
Loading vm file vm/cgame.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1284 jump table targets
compiling cgame
running assembler < /tmp/cgame.s_y9WCV9 > /tmp/cgame.o_oLYV2Q
done
computing jump table
VM file cgame compiled to 10577810 bytes of code (0x7fa6a0451000 - 0x7fa6a0e67792)
cgame loaded in 34239040 bytes on the hunk
UI menu load time = 38 milli seconds
...loading 'scripts/buildables.trail'
...loading 'scripts/weapons.trail'
...loading 'scripts/uncreation.particle'
...loading 'scripts/tremor.particle'
...loading 'scripts/niveus.particle'
...loading 'scripts/nexus6.particle'
...loading 'scripts/karith.particle'
...loading 'scripts/atcs.particle'
...loading 'scripts/arachnid2.particle'
...loading 'scripts/jetpack.particle'
...loading 'scripts/misc.particle'
...loading 'scripts/weapons.particle'
...loading 'scripts/buildables.particle'
stitched 0 LoD cracks
...loaded 3971 faces, 8 meshes, 0 trisurfs, 0 flares
CL_InitCGame:  5.00 seconds
7 msec to draw all images
Com_TouchMemory: 0 msec
root^7 entered the game
^1Your client is out of date. Updating your client will allow you to become an admin on servers and download maps much more quickly. Please replace your client executable with the one at ^2http://trem.tjw.org/backport/^1 and reconnect. ^5.^7User#1^7 disconnected
^tE^gu^tr^gi^td^gi^tc^7 was zapped by a tesla generator.
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
root@system76-pc:/home/sam# 

```

---

### Post by samh785 on 2009-11-15
Bump

---

### Post by Sindwiller on 2009-11-16
That's a common thing to be triggered by nvidia driver updates in Karmic it seems - in the past it used to **** up the modules config, now it somehow ***** up the permissions for the nvidia device file.

Since the nvidia device file is usually accessible for root and the video group, the usual fix is adding your user to the video group.

So

```
sudo usermod -aG video $your_username 
```

---

### Post by samh785 on 2009-11-16
> **Sindwiller said:**
> That's a common thing to be triggered by nvidia driver updates in Karmic it seems - in the past it used to **** up the modules config, now it somehow ***** up the permissions for the nvidia device file.

Since the nvidia device file is usually accessible for root and the video group, the usual fix is adding your user to the video group.

So

```
sudo usermod -aG video $your_username 
```
Thank you!

---

### Post by samh785 on 2009-11-27
I have now figured out how to change the permissions of the two files needed to allow me to play 3d games at a decent frame rate, but how do I SAVE these permissions? the files are:

/dev/nvidia0
/dev/nvidiactl

---

### Post by samh785 on 2009-12-18
> **samh785 said:**
> but how do I SAVE these permissions? the files are:

/dev/nvidia0
/dev/nvidiactl

bump

---

### Post by Ferrat on 2009-12-21
it's not very good or nice but you could use 

sudo nautilus 

go to /dev

select the files and right-click, go to properties>>permissions and make access for others read-only, that might work

---

