---
title: "Lots of problems with Frets on Fire"
date: 2007-10-27
forum: Gaming &amp; Leisure
---

### Post by seanf on 2007-10-27
I've installed Frets On Fire from the repositories on gutsy. When I run it, it is unplayable because it is so slow.

My video is a Radeon 9600 with the open source drivers... acceleration works, compiz fusion works, armagetron works, google earth works, stellarium works... so I think my video setup is ok.

If I start FoF with the verbose option, this is the output:

```
sean@bigwig:~$ fretsonfire -v
(W) PyOGG not found. OGG files will be fully decoded prior to playing; expect absurd memory usage.
(W) PyAmanith not found, SVG support disabled.
(D) Initializing audio.
(D) Audio configuration: (44100, -16, 1)
(D) Initializing video.
(W) Video setup failed. Trying without antialiasing.
(D) Enabling high priority timer.
(D) 0 joysticks found.
(N) Loading Data.star1 synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/mods/LightGraphics/star1.png' instead of '/usr/share/games/fretsonfire/data/mods/LightGraphics/star1.svg'.
(N) Loaded Data.star1 in 0.016 seconds
(N) Loading Data.star2 synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/mods/LightGraphics/star2.png' instead of '/usr/share/games/fretsonfire/data/mods/LightGraphics/star2.svg'.
(N) Loaded Data.star2 in 0.005 seconds
(N) Loading Data.left synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/mods/LightGraphics/left.png' instead of '/usr/share/games/fretsonfire/data/mods/LightGraphics/left.svg'.
(N) Loaded Data.left in 0.003 seconds
(N) Loading Data.right synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/mods/LightGraphics/right.png' instead of '/usr/share/games/fretsonfire/data/mods/LightGraphics/right.svg'.
(N) Loaded Data.right in 0.003 seconds
(N) Loading Data.ball1 synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/mods/LightGraphics/ball1.png' instead of '/usr/share/games/fretsonfire/data/mods/LightGraphics/ball1.svg'.
(N) Loaded Data.ball1 in 0.004 seconds
(N) Loading Data.ball2 synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/mods/LightGraphics/ball2.png' instead of '/usr/share/games/fretsonfire/data/mods/LightGraphics/ball2.svg'.
(N) Loaded Data.ball2 in 0.005 seconds
(N) Loading Data.loadingImage synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/mods/LightGraphics/loading.png' instead of '/usr/share/games/fretsonfire/data/mods/LightGraphics/loading.svg'.
(N) Loaded Data.loadingImage in 0.016 seconds
(N) Loading Data.font asynchronously
(N) Loading Data.bigFont asynchronously
(N) Loading Data.screwUpSounds asynchronously
(N) Loading Data.acceptSound asynchronously
(N) Loading Data.cancelSound asynchronously
(N) Loading Data.selectSound1 asynchronously
(N) Loading Data.selectSound2 asynchronously
(N) Loading Data.selectSound3 asynchronously
(N) Loading Data.startSound asynchronously
(D) Ready.
(N) Loading MainMenu.background synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/mods/LightGraphics/keyboard.png' instead of '/usr/share/games/fretsonfire/data/mods/LightGraphics/keyboard.svg'.
(N) Loaded MainMenu.background in 0.077 seconds
(N) Loading MainMenu.guy synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/mods/LightGraphics/pose.png' instead of '/usr/share/games/fretsonfire/data/mods/LightGraphics/pose.svg'.
(N) Loaded MainMenu.guy in 0.047 seconds
(N) Loading MainMenu.logo synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/mods/LightGraphics/logo.png' instead of '/usr/share/games/fretsonfire/data/mods/LightGraphics/logo.svg'.
(N) Loaded MainMenu.logo in 0.035 seconds
(W) Unable to enable psyco.
(N) Loaded Data.font in 0.001 seconds
(N) Loaded Data.bigFont in 0.000 seconds
(N) Loaded Data.screwUpSounds in 0.222 seconds
(N) Loaded Data.acceptSound in 0.031 seconds
(N) Loaded Data.cancelSound in 0.024 seconds
(N) Loaded Data.selectSound1 in 0.009 seconds
(N) Loaded Data.selectSound2 in 0.009 seconds
(N) Loaded Data.selectSound3 in 0.009 seconds
(N) Loaded Data.startSound in 0.020 seconds
(D) View: Push: MainMenu
(D) View: Push: Menu
```

So, I've got "PyOGG not found", although python-pyogg is installed.

"PyAmanith not found", but this isn't even in the repositories... makes me wonder why FoF is in the repo if its dependencies are not!

And "Video setup failed"... I've tried turning antialiasing off, but there was no noticeable improvement.

If I download FoF from [http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/) and run it verbosely from that, I do not get the errors regarding PyOGG and PyAmanith, but I do get the following:

```
(D) Initializing video.
(E) Couldn't find matching GLX visual
(W) Video setup failed. Trying without antialiasing.
```

So.... any ideas?

---

### Post by MadeR on 2008-02-12
for the audio part: the package you need is:
python-pyvorbis

---

### Post by FrozenFox on 2008-02-12
Hmmm. No glx visual.. you are probably right indeed that your video setup is fine, but just to be sure and see some things going on with glx, please give us the first 10 lines or so output of glxinfo.

---

### Post by MadeR on 2008-02-12
in my case the game starts, but the screen (windowed or fullscreen is the same) but the screen remains black, even though the program works, I can hear the audio and press esc to quit the game.

glxinfo 
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7276 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers,
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects,
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_float,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod,
    GL_WIN_swap_hint, WGL_EXT_swap_control

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7276 Release

```

from xorg.conf
```

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Option      "VideoOverlay" "off"
        Option      "OpenGLOverlay" "on"
#       Option      "DynamicClocks" "false"
        Option      "TexturedVideo" "on"
EndSection

```

---

