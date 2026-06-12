---
title: "No sound on Return to Castle Wolfenstein using Ubuntu 8.10 amd 64"
date: 2009-03-12
forum: Gaming &amp; Leisure
---

### Post by gdbutcher on 2009-03-12
Anyone know of a solution to fix the sound in Return to castle wolfenstein? 
I'm getting no sound at all. 

I'm running a Fujitsu-siemens Amilo PA2548 laptop, The audio drivers are all ALSA. I managed to clear the signal 11 fault by changing this line: ```
./wolfsp.x86 +set s_initsound 0 
``` in wolfsp. Could this be responsible?

I tried a variation of the ET fix, but without any luck:

```
sudo sh -c "echo 'wolf.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss"
sudo sh -c "echo 'wolf.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss"
```

Can anyone suggest anything?

---

### Post by gdbutcher on 2009-03-13
Below is the output from the terminal, notes the lines:
```

------- sound initialization -------
not initializing.
------------------------------------

```

It looks like the problem to me, anyone know how to fix it? ](*,)

The full output from the terminal: 

```
gareth@gareth-laptop:~$ ./wolfsp
Wolf 1.41 linux-i386 Dec  4 2002
----- FS_Startup -----
Current search path:
/home/gareth/.wolf/main
/home/gareth/wolfenstein/main/sp_pak4.pk3 (21 files)
/home/gareth/wolfenstein/main/sp_pak3.pk3 (14 files)
/home/gareth/wolfenstein/main/sp_pak2.pk3 (232 files)
/home/gareth/wolfenstein/main/sp_pak1.pk3 (1342 files)
/home/gareth/wolfenstein/main/pak0.pk3 (4775 files)
/home/gareth/wolfenstein/main

----------------------
6384 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing wolfconfig.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
Bypassing CD checks
----- Client Initialization -----
Cmd_AddCommand: map_restart already defined
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 8400M G/PCI/SSE2
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...using GL_NV_fog_distance
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 8400M G/PCI/SSE2
GL_VERSION: 2.1.2 NVIDIA 177.82
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
picmip2: 2
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
ATI truform: disabled
NV distance fog: enabled
Fog Mode: GL_EYE_RADIAL_NV
Initializing Shaders
...loading 'scripts/ai.shader'
...loading 'scripts/alpha.shader'
...loading 'scripts/blacksmokeanim.shader'
...loading 'scripts/blacksmokeanimb.shader'
...loading 'scripts/characters.shader'
...loading 'scripts/clipboard.shader'
...loading 'scripts/common.shader'
...loading 'scripts/cursorhints.shader'
...loading 'scripts/decals.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/expblue.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/fijets.shader'
...loading 'scripts/firest.shader'
...loading 'scripts/flamethrower.shader'
...loading 'scripts/funnel.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/heat.shader'
...loading 'scripts/lights.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/maxx.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/metal.shader'
...loading 'scripts/models.shader'
...loading 'scripts/netest.shader'
...loading 'scripts/oldwolf.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/particle.shader'
...loading 'scripts/q3view.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/signs.shader'
...loading 'scripts/skin.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/solo.shader'
...loading 'scripts/surfaces.shader'
...loading 'scripts/terrain.shader'
...loading 'scripts/test.shader'
...loading 'scripts/twiltb.shader'
...loading 'scripts/twiltb2.shader'
...loading 'scripts/ui.shader'
...loading 'scripts/ui_hud.shader'
...loading 'scripts/ui_notebook.shader'
...loading 'scripts/ui_wolf.shader'
...loading 'scripts/viewflames.shader'
...loading 'scripts/walls.shader'
...loading 'scripts/z_light.shader'
----- finished R_Init -----

------- sound initialization -------
not initializing.
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/gareth/wolfenstein/main/uii386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xf0439778  
Sys_LoadDll(ui) succeeded!
Parsing menu file:ui/main.menu
r_rmse of 0.000000 has saved 12kb
Parsing menu file:ui/setup.menu
Parsing menu file:ui/controls.menu
Parsing menu file:ui/cdkey.menu
Parsing menu file:ui/system.menu
Parsing menu file:ui/options.menu
Parsing menu file:ui/credit.menu
r_rmse of 0.000000 has saved 204kb
r_rmse of 0.000000 has saved 252kb
r_rmse of 0.000000 has saved 264kb
Parsing menu file:ui/connect.menu
Parsing menu file:ui/quit.menu
Parsing menu file:ui/vid_restart.menu
Parsing menu file:ui/snd_restart.menu
Parsing menu file:ui/rec_restart.menu
Parsing menu file:ui/default.menu
Parsing menu file:ui/error.menu
Parsing menu file:ui/serverinfo.menu
Parsing menu file:ui/quitcredit.menu
Parsing menu file:ui/resetscore.menu
Parsing menu file:ui/buy_pop.menu
Parsing menu file:ui/multiplayer_pop.menu
Parsing menu file:ui/play.menu
Parsing menu file:ui/load.menu
Parsing menu file:ui/mods.menu
Parsing menu file:ui/briefing.menu
UI menu load time = 599 milli seconds
Parsing menu file:ui/ingame.menu
Parsing menu file:ui/ingame_controls.menu
Parsing menu file:ui/ingame_options.menu
Parsing menu file:ui/ingame_system.menu
Parsing menu file:ui/ingame_leave.menu
Parsing menu file:ui/ingame_player.menu
Parsing menu file:ui/ingame_load.menu
Parsing menu file:ui/ingame_save.menu
Parsing menu file:ui/in_vid_restart.menu
Parsing menu file:ui/in_snd_restart.menu
Parsing menu file:ui/in_rec_restart.menu
Parsing menu file:ui/notebook.menu
Parsing menu file:ui/clipboard.menu
Parsing menu file:ui/bookz.menu
Parsing menu file:ui/bookv.menu
Parsing menu file:ui/bookp.menu
Parsing menu file:ui/pregame.menu
Parsing menu file:ui/test.menu
Parsing menu file:ui/ingame_help.menu
UI menu load time = 457 milli seconds
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: gareth-laptop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

```

---

### Post by gdbutcher on 2009-03-13
Heres how I fixed it if anyone is interested:

Open a terminal, input:

```
sudo gedit /etc/rc.local
```

Entered this line above the Exit 0 bit at the bottom:

```
echo "wolfsp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```

Saved the file, then:

```
sudo reboot
```

On reboot it worked, and everytime since.:D

---

