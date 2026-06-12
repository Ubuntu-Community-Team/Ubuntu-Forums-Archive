---
title: "wolf et blank screen!"
date: 2006-09-02
forum: Gaming &amp; Leisure
---

### Post by p0pnfresh on 2006-09-02
Hi i've installed wolfet v.2.56 successfully and are able to run it as the common user. When I run /usr/local/bin/et the game runs with sound but it shows a blank screen. This is the output I get after running et. The error must be video related any clues?

:/usr/local/bin$ et
ET 2.56 linux-i386 Sep 10 2003
----- FS_Startup -----
Current search path:
/home/p0pnfresh/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
3739 files in pk3 files
execing default.cfg
couldn't exec language.cfg
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
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225
GL_VERSION: 1.3 Mesa 6.4.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0xace94000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/p0pnfresh/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/p0pnfresh/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/p0pnfresh/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab324bfc
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: juiseb0x
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
execing preset_high.cfg
r_colorbits will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_picmip will be changed upon restarting.
r_mode will be changed upon restarting.
r_texturebits will be changed upon restarting.
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20050225
GL_VERSION: 1.3 Mesa 6.4.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/p0pnfresh/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/p0pnfresh/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/p0pnfresh/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab324bfc
Sys_LoadDll(ui) succeeded!

---

### Post by p0pnfresh on 2006-09-05
I updated Wolfet to 2.60 and still have the same problem.

---

### Post by Dark Elitist on 2006-09-05
Hey!

What kind of videocard do you have? ATI or nVidia? Do you have the latest drivers installed for your card?

Please provide system information!

---

### Post by p0pnfresh on 2006-09-06
Thanks for the reply.

I have a dell inspiron 700m. Mi video card is an Intel 82852/855GM Integrated Graphics Device. I have no idea about drivers. I can see videos in VLC player though. :-k

---

### Post by Dark Elitist on 2006-09-06
Hey. Sorry it took so long to reply...

You won't easily be doing any gaming, if at all, unless you buy a nVidia or ATI card, preferably nVidia.  Installing drivers is easy with tseliot's envy script and nVidia support is best on *nix.

Shop by brand on [http://www.newegg.com/]("http://www.newegg.com") for XFX and buy a nVidia card that will fit in your computer.  Depending on the motherboard used, you may need a PCI, but that's fine.  My friend was in the same boat as you and he got a 256 meg FX 5200 PCI and he plays Doom 3 and Quake 4 fine, which says a lot.

Good luck!

---

### Post by gosam on 2006-09-14
Did you run the game when you were asked at the end of the install, if yes, it means that some important files are now property of root, what I did is delete et and /home/user/.etwolf, then reinstall.

---

