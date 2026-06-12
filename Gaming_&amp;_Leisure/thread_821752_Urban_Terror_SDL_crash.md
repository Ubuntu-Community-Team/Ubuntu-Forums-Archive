---
title: "Urban Terror SDL crash"
date: 2008-06-07
forum: Gaming &amp; Leisure
---

### Post by spadewarrior on 2008-06-07
Hello,

Urban Terror has worked fine for ages, but suddenly I keep keep getting crashes to the desktop, sometimes even back to the login screen.

If run in the terminal, I get:
```

CL_Shutdown
SDL audio device shutdown
RE_Shutdown( 1 )
Segmentation fault

```

Any ideas? :confused:

---

### Post by spadewarrior on 2008-06-07
It's doing it in Quake Wars as well. :(

---

### Post by Phenax on 2008-06-07
Paste the whole output, not just the error spot.

---

### Post by spadewarrior on 2008-06-07
Hi.

I decided to reinstall the drivers. I used EnvyNG instead of the regular driver manager and it seems to have stopped.

If it happens again I shall paste the whole output in this thread.

Thanks. :)

---

### Post by jnorth on 2008-08-16
Odd - mine is doing this now out of the blue as well... still researching but this was the first thread I found.

Full log is below - I just used a local server with a bot to test, I got about 2 minutes of gameplay out of this particular example, but it varies from a few seconds to a few minutes.  Does it on any map, and whether I run a local server or connect to an online game.

Any ideas?

```
jnorth@nb01:~/ut$ ./ioUrbanTerror.i386 
ioQ3 1.35urt linux-i386 Dec 20 2007
----- FS_Startup -----
Going through search path...

----------------------
9359 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 4: 800 600
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce Go 7400/PCI/SSE2
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce Go 7400/PCI/SSE2
GL_VERSION: 2.1.2 NVIDIA 169.12
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "alsa".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  470
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x8b7f560 dma buffer
No background file.
----------------------
Sound initialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 375 milli seconds
UI menu load time = 260 milli seconds
16 bots parsed
13 crosshairs parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: nb01
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
38 arenas parsed
------ Server Initialization ------
Server: ut_apartment
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- FS_Startup -----
Going through search path...

----------------------
18718 files in pk3 files
Loading vm file vm/qagame.qvm...
VM file qagame compiled to 1870844 bytes of code
qagame loaded in 34524832 bytes on the hunk
------- Game Initialization -------
gamename: q3ut4
gamedate: Dec 21 2007
7 teams with 418 entities
-----------------------------------
Opened log botlib.log
------- BotLib Initialization -------
loaded weapons.c
loaded items.c
loaded syn.c
loaded rnd.c
loaded match.c
^3Warning: file rchat.c, line 635: variables from the match template(s) could be invalid when outputting one of the chat messages
^3Warning: file rchat.c, line 1242: variables from the match template(s) could be invalid when outputting one of the chat messages
loaded rchat.c
------------ Map Loading ------------
trying to load maps/ut_apartment.aas
loaded maps/ut_apartment.aas
found 2 level items
-------------------------------------
16 UT bots parsed
38 arenas parsed
AAS initialized.
-----------------------------------
RE_Shutdown( 0 )
----- R_Init -----

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce Go 7400/PCI/SSE2
GL_VERSION: 2.1.2 NVIDIA 169.12
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 378 milli seconds
UI menu load time = 271 milli seconds
16 bots parsed
13 crosshairs parsed
Loading vm file vm/cgame.qvm...
VM file cgame compiled to 1617707 bytes of code
cgame loaded in 34383680 bytes on the hunk
^1ERROR: Could not open "sound/ut_202/202_drums.wav"
^3WARNING: could not find sound/ut_202/202_drums.wav - using default
^3WARNING: R_FindImageFile could not find 'textures/base_floor/clangdark.tga' in shader 'textures/base_floor/clangdark'
^3Shader textures/base_floor/clangdark has a stage with no image
^3WARNING: R_FindImageFile could not find 'textures/docks/cow_vents3.tga' in shader 'textures/cow/cow_metal4'
^3Shader textures/cow/cow_metal4 has a stage with no image
^3WARNING: 'textures/common/mirror1.tga' TGA file header declares top-down image, ignoring
stitched 126 LoD cracks
...loaded 16538 faces, 598 meshes, 909 trisurfs, 0 flares
^3WARNING: R_FindImageFile could not find 'sprites/foe2.tga' in shader 'sprites/foe'
^3Shader sprites/foe has a stage with no image
UI menu load time = 21 milli seconds
13 crosshairs parsed
CL_InitCGame: 12.46 seconds
4 msec to draw all images
Com_TouchMemory: 0 msec
Welcome...
sQu1b joined the blue team.
sQu1b entered the game
Welcome...
]/exec bots
execing bots
Com_sprintf: overflow of 2 in 2
loaded skill 1 from bots/default_c.c
loaded skill 1 from bots/ut_cheetah_c.c
loaded bots/ut_cheetah_i.c
loaded bots/ut_cheetah_w.c
loaded cheetah from bots/ut_cheetah_t.c
Spawning bot
Cheetah connected
Cougar joined the red team.
Cougar entered the game
2 teams with 418 entities
Received signal 11, exiting...
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
----- Server Shutdown (Signal caught) -----
==== ShutdownGame ====
AAS shutdown.
Closed log botlib.log
---------------------------
Shutdown tty console
jnorth@nb01:~/ut$ 
```

---

### Post by Crafty Kisses on 2008-08-16
You might want to try turning desktop effects off, post the following output:
```
glxinfo
```

---

### Post by jnorth on 2008-08-17
> **Codename said:**
> You might want to try turning desktop effects off, post the following output:
```
glxinfo
```

Hmm, didn't think of that -- I'll try that later on tonight and post back.  I did kill the screensaver and all power management apps to make sure they weren't interfering.  In the meantime, here is the requested output.

```
jnorth@nb01:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 7400/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x71 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x82 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x83 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x84 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x85 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x86 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x87 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x89 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8b 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x8c 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x8d 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8e 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x90 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x91 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x92 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x93 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x94 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x95 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x96 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x97 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x98 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
jnorth@nb01:~$ 
```

---

### Post by jnorth on 2008-08-17
> **Codename said:**
> You might want to try turning desktop effects off, post the following output:
```
glxinfo
```

Got around to trying with all desktop effects off - still crashing...  and with the exception of the lines stemming from me using a different map on this test, every single line is identical on the terminal output.

Terminal output:
```
jnorth@nb01:~$ ut
ioQ3 1.35urt linux-i386 Dec 20 2007
----- FS_Startup -----
Going through search path...

----------------------
9359 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 4: 800 600
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce Go 7400/PCI/SSE2
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce Go 7400/PCI/SSE2
GL_VERSION: 2.1.2 NVIDIA 169.12
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "alsa".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  470
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x8b7f3d0 dma buffer
No background file.
----------------------
Sound initialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 369 milli seconds
UI menu load time = 252 milli seconds
16 bots parsed
13 crosshairs parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: nb01
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
38 arenas parsed
------ Server Initialization ------
Server: ut4_dressingroom
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- FS_Startup -----
Going through search path...

----------------------
18718 files in pk3 files
Loading vm file vm/qagame.qvm...
VM file qagame compiled to 1870844 bytes of code
qagame loaded in 34524832 bytes on the hunk
------- Game Initialization -------
gamename: q3ut4
gamedate: Dec 21 2007
2 teams with 16 entities
-----------------------------------
Opened log botlib.log
------- BotLib Initialization -------
loaded weapons.c
loaded items.c
loaded syn.c
loaded rnd.c
loaded match.c
^3Warning: file rchat.c, line 635: variables from the match template(s) could be invalid when outputting one of the chat messages
^3Warning: file rchat.c, line 1242: variables from the match template(s) could be invalid when outputting one of the chat messages
loaded rchat.c
------------ Map Loading ------------
trying to load maps/ut4_dressingroom.aas
loaded maps/ut4_dressingroom.aas
found 2 level items
-------------------------------------
16 UT bots parsed
38 arenas parsed
AAS initialized.
-----------------------------------
RE_Shutdown( 0 )
----- R_Init -----

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce Go 7400/PCI/SSE2
GL_VERSION: 2.1.2 NVIDIA 169.12
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
Loading vm file vm/ui.qvm...
VM file ui compiled to 737597 bytes of code
ui loaded in 33931488 bytes on the hunk
UI menu load time = 379 milli seconds
UI menu load time = 263 milli seconds
16 bots parsed
13 crosshairs parsed
Loading vm file vm/cgame.qvm...
VM file cgame compiled to 1617707 bytes of code
cgame loaded in 34383680 bytes on the hunk
^3WARNING: 'textures/common/mirror1.tga' TGA file header declares top-down image, ignoring
stitched 0 LoD cracks
...loaded 513 faces, 0 meshes, 40 trisurfs, 0 flares
^3WARNING: R_FindImageFile could not find 'sprites/foe2.tga' in shader 'sprites/foe'
^3Shader sprites/foe has a stage with no image
UI menu load time = 21 milli seconds
13 crosshairs parsed
CL_InitCGame:  6.81 seconds
5 msec to draw all images
Com_TouchMemory: 1 msec
Welcome...
]/exec bots
execing bots
Com_sprintf: overflow of 2 in 2
loaded skill 1 from bots/default_c.c
loaded skill 1 from bots/ut_cheetah_c.c
loaded bots/ut_cheetah_i.c
loaded bots/ut_cheetah_w.c
loaded cheetah from bots/ut_cheetah_t.c
Spawning bot
Cheetah connected
Cheetah joined the blue team.
Cheetah entered the game
sQu1b joined the red team.
sQu1b entered the game

(((( gameplay removed for briefness ))))

Cheetah was torn asunder by sQu1b's crass AK103.
Received signal 11, exiting...
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
----- Server Shutdown (Signal caught) -----
==== ShutdownGame ====
AAS shutdown.
Closed log botlib.log
---------------------------
Shutdown tty console
jnorth@nb01:~$ 
```

---

### Post by typek_pb on 2009-02-07
Hi, 

same issue at my side. I have following console output (game history croped):
```
ioQ3 1.35urt linux-i386 Aug 10 2008
----- FS_Startup -----             
Going through search path...       

----------------------
8313 files in pk3 files
execing default.cfg    
execing q3config.cfg   
execing autoexec.cfg   
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.         
----- Initializing Renderer ---- 
-------------------------------  
QKEY found.                      
----- Client Initialization Complete -----
----- R_Init -----                        
...loading libGL.so.1:                    
Calling SDL_Init(SDL_INIT_VIDEO)...       
SDL_Init(SDL_INIT_VIDEO) passed.          
Initializing OpenGL display               
...setting mode 4: 800 600                
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce4 MX 440/AGP/SSE/3DNOW!         
Initializing OpenGL extensions                      
...ignoring GL_S3_s3tc                              
...ignoring GL_EXT_texture_env_add                  
...using GL_ARB_multitexture                        
...using GL_EXT_compiled_vertex_array               
...ignoring GL_EXT_texture_filter_anisotropic       

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX 440/AGP/SSE/3DNOW!
GL_VERSION: 1.5.8 NVIDIA 96.43.09          
GL_MAX_TEXTURE_SIZE: 2048                  
GL_MAX_ACTIVE_TEXTURES_ARB: 2              

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A                 
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
----- finished R_Init -----                          
------ Initializing Sound ------                     
Initializing SDL audio driver...                     
SDL audio driver is "alsa".                          
SDL_AudioSpec:                                       
  Format:   AUDIO_S16LSB                             
  Freq:     22050                                    
  Samples:  470                                      
  Channels: 2                                        
Starting SDL audio callback...                       
SDL audio initialized.                               
----- Sound Info -----                               
    1 stereo                                         
16384 samples                                        
   16 samplebits                                     
    1 submission_chunk                               
22050 speed                                          
0x95cfb58 dma buffer                                 
No background file.                                  
----------------------                               
Sound initialization successful.                     
--------------------------------                     
Sound memory manager started                         
Loading vm file vm/ui.qvm...                         
VM file ui compiled to 737597 bytes of code          
ui loaded in 33931488 bytes on the hunk              
UI menu load time = 562 milli seconds                
UI menu load time = 402 milli seconds                
16 bots parsed                                       
13 crosshairs parsed                                 
--- Common Initialization Complete ---               
Opening IP socket: localhost:27960                   
Hostname: pb-desktop                                 
IP: 127.0.1.1                                        
Started tty console (use +set ttycon 0 to disable)   
85.131.185.19:27960 resolved to 85.131.185.19:27960  
----- FS_Startup -----                               
Going through search path...                         

handle 1: music/mainmenu.wav
----------------------      
16626 files in pk3 files    
Need paks: @q3ut4/ut_forrest.pk3@q3ut4/ut_forrest.pk3@q3ut4/ut4_subterra.pk3@q3ut4/ut4_subterra.pk3@q3ut4/ut4_sliema.pk3@q3ut4/ut4_sliema.pk3@q3ut4/ut4_paradise.pk3@q3ut4/ut4_paradise.pk3@q3ut4/ut4_oildepot.pk3@q3ut4/ut4_oildepot.pk3@q3ut4/ut4_kingdom.pk3@q3ut4/ut4_kingdom.pk3@q3ut4/ut4_baeza.pk3@q3ut4/ut4_baeza.pk3   
RE_Shutdown( 0 )                                                                
Hunk_Clear: reset the hunk ok                                                   
----- R_Init -----                                                              

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX 440/AGP/SSE/3DNOW!
GL_VERSION: 1.5.8 NVIDIA 96.43.09          
GL_MAX_TEXTURE_SIZE: 2048                  
GL_MAX_ACTIVE_TEXTURES_ARB: 2              

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A                 
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
----- finished R_Init -----                          
Loading vm file vm/ui.qvm...                         
VM file ui compiled to 737597 bytes of code          
ui loaded in 33931488 bytes on the hunk              
UI menu load time = 492 milli seconds                
UI menu load time = 356 milli seconds                
16 bots parsed                                       
13 crosshairs parsed                                 
Loading vm file vm/cgame.qvm...                      
VM file cgame compiled to 1617707 bytes of code      
cgame loaded in 34383680 bytes on the hunk           
stitched 4 LoD cracks                                
...loaded 7979 faces, 64 meshes, 149 trisurfs, 0 flares
^3WARNING: R_FindImageFile could not find 'sprites/foe2.tga' in shader 'sprites/foe'                                                                            
^3Shader sprites/foe has a stage with no image                                  
UI menu load time = 26 milli seconds                                            
13 crosshairs parsed                                                            
CL_InitCGame: 29.98 seconds                                                     
2250 msec to draw all images                                                    
Com_TouchMemory: 0 msec                                                         
Rastmannis connected                                                            
Addicted connected                                                              
Rastmannis joined the blue team.                                                
Rastmannis entered the game                                                     
Willkommen auf den Urban Terror Server von den Crusaders                        
Dr_Tran got a lead enema from BaRt!!!'s retro M4.                               
Bafti_The_King played 'catch the shiny bullet' with <<C>>Siggi's LR-300 rounds. 
tesa got a lead enema from bounty-hunter's retro M4.                            
pb-ubuntu.sk joined the blue team.                                              
pb-ubuntu.sk entered the game                                                   
Willkommen auf den Urban Terror Server von den Crusaders                        
<<C>>NightlyNeo got a whole lot of hole from PixelBorg[ro]'s DE round.          
<<C>>Cyborg was on the wrong end of [PLS]Scourer's G36.                         
<<C>>Siggi played 'catch the shiny bullet' with amuse's LR-300 rounds.          
amuse got a lead enema from s!mon's retro M4.                                   
deadstar got a lead enema from s!mon's retro M4.                                
kumefight got a lead enema from piercing_huber's retro M4.                      
Addicted joined the red team.                                                   
Addicted entered the game                                                       
^4Spectator@mp3[PL]^7 (train station front): ^3Requesting medic. Status: near death                                                                             
^4[PLS]Scourer^7 (back parking lot): ^3sry                                      
rastafari[pt] was on the wrong end of <<C>>NightlyNeo's G36.                    
Rastmannis played 'catch the shiny bullet' with tesa's LR-300 rounds.           
PixelBorg[ro] got a lead enema from s!mon's retro M4.                           
Bafti_The_King got a lead enema from s!mon's retro M4.                          
.........
<game history only in fact>
.........
.........
.........
^4Etasoeur^3: ^3c'est vraiment un gros mouleux utko :o
^4[SPG]kiwi@ubuntu.com^3: ^3frag drain wie gut ich eig.bin
You were hit in the Kevlar by >-((*>-.-WinZ-.- for 100% damage.
pb-ubuntu managed to slow down >-((*>-.-WinZ-.-'s SR-8 round just a little.
>-((*>-.-WinZ-.- had 100% Health.
TheOnlyOne{PL} was torn asunder by utkO's crass AK103.
Etasoeur hit |SpaM|- in the Head for 100% damage.
|SpaM|- played 'catch the shiny bullet' with Etasoeur's LR-300 rounds.
Etasoeur was hit in the Legs by >-((*>-.-WinZ-.- for 17% damage.
>-((*>-.-WinZ-.- played 'catch the shiny bullet' with [SPG]last-pain's LR-300 rounds.
|SpaM |- disconnected
YOUNES was torn asunder by vorsprung's crass AK103.
^1(DEAD) >-((*>-.-WinZ-.-^3: ^3Oooo
framo managed to slow down Frinuc's SR-8 round just a little.
vorsprung played 'catch the shiny bullet' with babillone's LR-300 rounds.
Received signal 11, exiting...
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
Shutdown tty console

```
this is output of my glxinfo:
```
name of display: :0.0                                                           
display: :0  screen: 0                                                          
direct rendering: Yes                                                           
server glx vendor string: NVIDIA Corporation                                    
server glx version string: 1.4                                                  
server glx extensions:                                                          
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,              
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,                 
    GLX_EXT_texture_from_pixmap                                                 
client glx vendor string: NVIDIA Corporation                                    
client glx version string: 1.4                                                  
client glx extensions:                                                          
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,         
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,          
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,   
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,          
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap                  
GLX version: 1.3                                                                
GLX extensions:                                                                 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,              
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,                 
    GLX_EXT_texture_from_pixmap, GLX_ARB_get_proc_address                       
OpenGL vendor string: NVIDIA Corporation                                        
OpenGL renderer string: GeForce4 MX 440/AGP/SSE/3DNOW!                          
OpenGL version string: 1.5.8 NVIDIA 96.43.09                                    
OpenGL extensions:                                                              
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_pixel_buffer_object,            
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects,        
    GL_ARB_shading_language_100, GL_ARB_texture_compression,                    
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,                            
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,                        
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,                   
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,                       
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,             
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra,               
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,             
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,    
    GL_EXT_draw_range_elements, GL_EXT_fog_coord,                               
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays,                    
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,  
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,     
    GL_EXT_separate_specular_color, GL_EXT_shared_texture_palette,              
    GL_EXT_stencil_wrap, GL_EXT_texture_compression_s3tc,                       
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,                         
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,                        
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,                      
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,        
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,                      
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fence,                      
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil,   
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_register_combiners,       
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,                        
    GL_NV_texture_rectangle, GL_NV_vertex_array_range,                          
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1,   
    GL_SGIS_generate_mipmap, GL_SGIS_multitexture, GL_SGIS_texture_lod,         
    GL_SUN_slice_accum                                                          

48 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x39 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x3a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x42 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x43 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x44 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x45 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x46 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x47 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x48 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x49 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x4a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x4b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x4c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x4d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x4e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x50 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None

55 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x51  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x52  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x53  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x54  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x55  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x56  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x57  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x58  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x59  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5a  0 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5b  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5c  0 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5d  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5e  0 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5f  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x60  0 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x61  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x62  0 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x63  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x64  0 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x65  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x66  0 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x67  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x68  0 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x69  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x6a  0 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x6b  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x6c  0 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x6d  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x6e  0 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x6f  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x70  0 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x71  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75  0 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76  0 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77  0 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78  0 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79  0 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a  0 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b  0 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c  0 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d  0 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e  0 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f  0 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80  0 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81  0 sg  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x82  0 sg  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x83  0 sg  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x84  0 sg  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x85  0 sg  0  0  0 r  .  .  0  0  0  0  4 16  0 16 16 16 16  0 0 None
0x86  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  0 16 16 16 16  0 0 None
0x87  0 sg  0  0  0 r  .  .  0  0  0  0  4 24  8 16 16 16 16  0 0 None
```

---

