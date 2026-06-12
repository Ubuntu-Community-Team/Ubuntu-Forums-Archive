---
title: "Problems with running Enemy Territory"
date: 2005-11-19
forum: Gaming &amp; Leisure
---

### Post by Rast on 2005-11-19
Hello out there :) first post here, so Hi to all...

   - I have installed Enemy Territory, and solved some drivers problems (loading some wrong modules) and now when I run ET from application, I get a big black window doing nothing on top of my desktop (actually, all of my four desktops).
   - This is the message I get when running through ET the terminal, I udnerstand it could be something with the sounds initialiaztion. Howver, sounds works fine on the rest of my box..

 > ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/dan/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
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
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce4 Ti 4200 with AGP8X/AGP/SSE/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 Ti 4200 with AGP8X/AGP/SSE/3DNOW!
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multisample GL_ARB_mul titexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_bord er_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_a dd GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_re peat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_objec t GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT _texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_ range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL _EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_ rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shad ow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture3D GL_E XT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL _EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotrop ic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_verte x_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repea t GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_ clamp GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_multisample_ filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_ra nge GL_NV_point_sprite GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_ texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV _texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shad er3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_N V_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture _lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_ SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_ARB _get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
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
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------


   Hope someone can help. Thanks in advance..

---

### Post by C_nemo on 2005-12-02
Try killing esd before starting ET. Its probably hugging your soundcard. 
Start ET på typing

run-program (alt-f2)
killall esd

run-program (alt-f2)
et

run-program (alt-f2)
esd

quite cumbersome, but someone has boundto have made a script which automates it. It should get you up and running though

---

### Post by yetanothersteve on 2005-12-02
This worked for me and has been much discussed elsewhere. I created a bash script to allow ET direct access to OSS.

```
#!/bin/bash
cd /proc/asound/card0/pcm0p
chmod 666  oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```

You have to run the bash script as superuser or sudo, in my case: 
```
sudo sh etsound.sh
```

Reference link:
[http://alsa.opensrc.org/index.php?page=FAQ023]("http://alsa.opensrc.org/index.php?page=FAQ023")

---

### Post by Copter on 2005-12-06
[QUOTE=C_nemo]Try killing esd before starting ET. Its probably hugging your soundcard. 
Start ET på typing

run-program (alt-f2)
killall esd

run-program (alt-f2)
et

run-program (alt-f2)
esd

quite cumbersome, but someone has boundto have made a script which automates it. It should get you up and running though[/QUOTE]
hi!

had the same problem. just killed osd and ran the game again. it worked :) thnx!

copter :]

---

