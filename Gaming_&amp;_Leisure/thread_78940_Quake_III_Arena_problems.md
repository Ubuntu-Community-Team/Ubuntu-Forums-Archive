---
title: "Quake III Arena problems"
date: 2005-10-19
forum: Gaming &amp; Leisure
---

### Post by var on 2005-10-19
hi all,

I installed Q3A under Ubuntu Breezy, and it starts.
But, mouse and sounds don't work.

here's the output:

[size=1]
Q3 1.32 linux-i386 Oct  7 2002
----- FS_Startup -----
Current search path:
/home/var/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: MOBILITY RADEON 9600 Generic
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: MOBILITY RADEON 9600 Generic
GL_VERSION: 1.3.5272 (X4.3.0-8.16.20)
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_element_array GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_map_object_buffer GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_ATI_vertex_array_object GL_ATI_vertex_attrib_array_object GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_blend_square GL_NV_occlusion_query GL_NV_texgen_reflection GL_SGI_color_matrix GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/lightningnew.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/tim.shader'
...loading 'scripts/base.shader'
...loading 'scripts/base_button.shader'
...loading 'scripts/base_floor.shader'
...loading 'scripts/base_light.shader'
...loading 'scripts/base_object.shader'
...loading 'scripts/base_support.shader'
...loading 'scripts/base_trim.shader'
...loading 'scripts/base_wall.shader'
...loading 'scripts/common.shader'
...loading 'scripts/ctf.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/gothic_block.shader'
...loading 'scripts/gothic_floor.shader'
...loading 'scripts/gothic_light.shader'
...loading 'scripts/gothic_trim.shader'
...loading 'scripts/gothic_wall.shader'
...loading 'scripts/hell.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/models.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/shrine.shader'
...loading 'scripts/skin.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/test.shader'
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
0xadbe2000 dma buffer
No background file.
----------------------
Sound memory manager started
Loading vm file vm/ui.qvm.
VM file ui compiled to 594408 bytes of code
ui loaded in 1963008 bytes on the hunk
35 arenas parsed
32 bots parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: HAL9000
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
[/size]

the game worked greatly under Hoary.
can anyone help me?

thank you. :)

---

### Post by var on 2005-10-19
I fixed the audio problem, but the mouse doesn't work yet. :(

---

### Post by var on 2005-10-19
exactly, my mouse fires and jumps, but doesn't move. :(

---

### Post by GIBson3 on 2005-10-19
Just out of curiosity, what did you do to fix your Mouse? (getting ready to install q3a on my "work" box for lunch time activities :)

---

### Post by var on 2005-10-21
[QUOTE=GIBson3]Just out of curiosity, what did you do to fix your Mouse? (getting ready to install q3a on my "work" box for lunch time activities :)[/QUOTE]

ahem... I don't fix my mouse yet... it doesn't move inside the game. :(

---

### Post by var on 2005-10-21
I fixed my problem by using the version 1.32b of the pointrelease. :)

---

### Post by GIBson3 on 2005-10-21
[QUOTE=GIBson3]Just out of curiosity, what did you do to fix your Mouse? (getting ready to install q3a on my "work" box for lunch time activities :)[/QUOTE]

Sorry that should have been....
[COLOR="Red"]Just out of curiosity, what did you do to fix your **sound**? (getting ready to install q3a on my "work" box for lunch time activities :)[/COLOR]

I've got it all working except Sound. I know my issue is relating to the fact that /dev/dsp is not accessable to the app atm (unless I sudo ./quake3, which I'd rather not do) so working on that now.

---

