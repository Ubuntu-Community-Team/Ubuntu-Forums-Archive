---
title: "idRenderSystem::Shutdown()"
date: 2013-12-21
forum: Gaming &amp; Leisure
---

### Post by starving030 on 2013-12-21
I'm trying to run Doom3. It starts to load, then I get a black screen for a few seconds and then back to terminal. I don't know enough about linux yet to understand what to check/fix. It took me like 3 hours to fumble through getting it installed.haha Any ideas?

This is what I get in terminal once I try to run Doom3.
```
doom3
DOOM 1.1.1286 linux-x86 Nov 24 2004 17:56:04
Hostname: bryler-Aspire
local IP: 127.0.1.1
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
/home/bryler/.doom3/base
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
couldn't exec DoomConfig.cfg
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
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
libGL error: failed to load driver: i965
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: Mesa DRI Intel(R) Ivybridge Desktop 
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_s3tc GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_packed_pixels GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_depth_clamp GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.25
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
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
X..GL_ARB_vertex_buffer_object not found
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Available.
Cg not available.
---------------------------------
---------- R_Exp_Init -----------
Disabled at compile time.
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
bryler@bryler-Aspire:~$ 

```

---

### Post by Bucky Ball on 2013-12-21
Where to start? I can't help with any of your issues but can point out some clues for your to start researching. The title of your thread is a bit misleading because it really just tells us the app has shutdown due to a rendering issue, not really why or much else, but there seems to be other things going on. So here goes.

Your problems start here I'd say:

```
5151 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
```

Followed by this:

```
---------- R_ARB2_Init ----------
Available.
Cg not available.
---------------------------------
---------- R_Exp_Init -----------
Disabled at compile time.
```

Then this:

```
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
```

Then comes total shutdown, the title of your thread. Seems to be okay to start with, as shown with the render system here:

```
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
```

So you need to track down what's killing it and why further in the read out. Maybe ARB is wrong render system. Obviously, and as I mention, not really across it, but hopefully have raised a point or two to ponder ...

---

