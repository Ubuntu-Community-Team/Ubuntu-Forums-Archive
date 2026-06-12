---
title: "Freedoom Crashes in OpenGL graphics mode"
date: 2018-09-02
forum: Gaming &amp; Leisure
---

### Post by emilward on 2018-09-02
I just installed Xubuntu 16.04 32-bit on a Toshiba Satellite A215-S7437 and Freedoom crashes and then closes out when I change the graphics to OpenGL mode. If I run it in lower settings such as 32-bit, 16-bit, 8-bit, etc the game runs just fine. Does anyone know what this is happening? The laptop has an AMD Turion 64 X2 CPU, 4GB of RAM, and an ATI RS690 GPU. I tried figuring out what version of OpenGL this card supports (thinking that may be the issue) and this is what I got in terminal:

```

eric@Toshiba-A215:~$ glxinfo | grep "OpenGL version"
OpenGL version string: 2.1 Mesa 18.0.5
eric@Toshiba-A215:~$ glxinfo | grep 'version'
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
    Max core profile version: 0.0
    Max compat profile version: 2.1
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 2.0
OpenGL version string: 2.1 Mesa 18.0.5
OpenGL shading language version string: 1.20
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 18.0.5
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
eric@Toshiba-A215:~$
```

I also tried launching Freedoom from terminal (then changing graphics to OpenGL) to see what happens and this is what I got:

```

eric@Toshiba-A215:~$ freedoom1
M_LoadDefaults: Load system defaults.
 default file: /home/eric/.prboom-plus/prboom-plus.cfg
 found /usr/share/games/doom/prboom-plus.wad

PrBoom-Plus v2.5.1.5 (http://prboom-plus.sourceforge.net/)
 found /usr/share/games/doom/freedoom1.wad
IWAD found: /usr/share/games/doom/freedoom1.wad
PrBoom-Plus, playing: The Ultimate DOOM
PrBoom-Plus is released under the GNU General Public license v2.0.
You are welcome to redistribute it under certain conditions.
It comes with ABSOLUTELY NO WARRANTY. See the file COPYING for details.
V_Init: allocate screens.
V_InitMode: using 32 bit video mode
I_CalculateRes: trying to optimize screen pitch
 test case for pitch=5120 is processed 970 times for 100 msec
 test case for pitch=5152 is processed 2055 times for 100 msec
 optimized screen pitch is 5152
I_InitScreenResolution: Using resolution 1280x800
 found /usr/share/games/doom/prboom-plus.wad
D_InitNetGame: Checking for network game.
W_Init: Init WADfiles.
 adding /usr/share/games/doom/freedoom1.wad
 adding /usr/share/games/doom/prboom-plus.wad
W_InitCache

Loading DEH lump from /usr/share/games/doom/freedoom1.wad
M_Init: Init miscellaneous info.
SetRatio: width/height parameters 1280x800
SetRatio: storage aspect ratio 8:5
SetRatio: assuming square pixels
SetRatio: display aspect ratio 8:5
SetRatio: gl_ratio 1.920000
SetRatio: multiplier 5/6
R_Init: Init DOOM refresh daemon - 
R_LoadTrigTables: Endianness...ok.
R_InitData: Textures Flats Sprites 
R_Init: R_InitPlanes R_InitLightTables R_InitSkyMap R_InitTranslationsTables R_InitPatches 
P_Init: Init Playloop state.
I_Init: Setting up machine state.
I_InitSound:  configured audio device with 512 samples/slice
Fluidplayer: Fluidsynth version 1.1.6

** (process:5783): CRITICAL **: fluid_synth_sfload: assertion 'filename != NULL' failed
fl_init: error loading soundfont /usr/share/sounds/sf2/TimGM6mb.sf2
portmidiplayer device list:
  ALSA:Midi Through Port-0
portmidiplayer: Opening device ALSA:Midi Through Port-0 for output
I_InitSound: sound module ready
S_Init: Setting up sound.
S_Init: default sfx volume 8
HU_Init: Setting up heads up display.
I_InitGraphics: 1280x800
I_UpdateVideoMode: 0xe0000000, SDL buffer, direct access
SetRatio: width/height parameters 1280x800
SetRatio: storage aspect ratio 8:5
SetRatio: assuming square pixels
SetRatio: display aspect ratio 8:5
SetRatio: gl_ratio 1.920000
SetRatio: multiplier 5/6
ST_Init: Init status bar.
vorb_registersong: failed
mad_registersong failed: input buffer too small (or EOF)
db_registersong: couldn't load as tracker
Exp_RegisterSongEx: Using player opl2 synth player
G_DoPlayDemo: playing demo with Ultimate Doom/Doom95 compatibility
vorb_registersong: failed
mad_registersong failed: input buffer too small (or EOF)
db_registersong: couldn't load as tracker
Exp_RegisterSongEx: Using player opl2 synth player
P_GetNodesVersion: using normal BSP nodes
V_InitMode: using OpenGL video mode
I_InitScreenResolution: Using resolution 1280x800
I_UpdateVideoMode: 0x80000002, own buffer, direct access
SetRatio: width/height parameters 1280x800
SetRatio: storage aspect ratio 8:5
SetRatio: assuming square pixels
SetRatio: display aspect ratio 8:5
SetRatio: gl_ratio 1.920000
SetRatio: multiplier 5/6
SDL OpenGL PixelFormat:
    SDL_GL_RED_SIZE: 8
    SDL_GL_GREEN_SIZE: 8
    SDL_GL_BLUE_SIZE: 8
    SDL_GL_STENCIL_SIZE: 8
    SDL_GL_ACCUM_RED_SIZE: 0
    SDL_GL_ACCUM_GREEN_SIZE: 0
    SDL_GL_ACCUM_BLUE_SIZE: 0
    SDL_GL_ACCUM_ALPHA_SIZE: 0
    SDL_GL_DOUBLEBUFFER: 1
    SDL_GL_BUFFER_SIZE: 24
    SDL_GL_DEPTH_SIZE: 24
    SDL_GL_MULTISAMPLESAMPLES: 0
    SDL_GL_MULTISAMPLEBUFFERS: 0
    SDL_GL_STENCIL_SIZE: 8
GL_VENDOR: X.Org R300 Project
GL_RENDERER: ATI RS690
GL_VERSION: 2.1 Mesa 18.0.5
GL_EXTENSIONS:
    GL_AMD_shader_trinary_minmax
    GL_ANGLE_texture_compression_dxt3
    GL_ANGLE_texture_compression_dxt5
    GL_APPLE_packed_pixels
    GL_ARB_ES2_compatibility
    GL_ARB_buffer_storage
    GL_ARB_clear_buffer_object
    GL_ARB_clip_control
    GL_ARB_compressed_texture_pixel_storage
    GL_ARB_copy_buffer
    GL_ARB_debug_output
    GL_ARB_depth_texture
    GL_ARB_draw_buffers
    GL_ARB_draw_elements_base_vertex
    GL_ARB_explicit_attrib_location
    GL_ARB_explicit_uniform_location
    GL_ARB_fragment_coord_conventions
    GL_ARB_fragment_program
    GL_ARB_fragment_program_shadow
    GL_ARB_fragment_shader
    GL_ARB_framebuffer_object
    GL_ARB_get_program_binary
    GL_ARB_get_texture_sub_image
    GL_ARB_half_float_pixel
    GL_ARB_half_float_vertex
    GL_ARB_instanced_arrays
    GL_ARB_internalformat_query
    GL_ARB_internalformat_query2
    GL_ARB_invalidate_subdata
    GL_ARB_map_buffer_alignment
    GL_ARB_map_buffer_range
    GL_ARB_multi_bind
    GL_ARB_multisample
    GL_ARB_multitexture
    GL_ARB_occlusion_query
    GL_ARB_occlusion_query2
    GL_ARB_pixel_buffer_object
    GL_ARB_point_parameters
    GL_ARB_point_sprite
    GL_ARB_program_interface_query
    GL_ARB_provoking_vertex
    GL_ARB_robustness
    GL_ARB_sampler_objects
    GL_ARB_separate_shader_objects
    GL_ARB_shader_objects
    GL_ARB_shading_language_100
    GL_ARB_shadow
    GL_ARB_sync
    GL_ARB_texture_barrier
    GL_ARB_texture_border_clamp
    GL_ARB_texture_compression
    GL_ARB_texture_cube_map
    GL_ARB_texture_env_add
    GL_ARB_texture_env_combine
    GL_ARB_texture_env_crossbar
    GL_ARB_texture_env_dot3
    GL_ARB_texture_filter_anisotropic
    GL_ARB_texture_float
    GL_ARB_texture_mirror_clamp_to_edge
    GL_ARB_texture_mirrored_repeat
    GL_ARB_texture_non_power_of_two
    GL_ARB_texture_rectangle
    GL_ARB_texture_rg
    GL_ARB_texture_storage
    GL_ARB_texture_swizzle
    GL_ARB_transpose_matrix
    GL_ARB_vertex_array_bgra
    GL_ARB_vertex_array_object
    GL_ARB_vertex_attrib_binding
    GL_ARB_vertex_buffer_object
    GL_ARB_vertex_program
    GL_ARB_vertex_shader
    GL_ARB_vertex_type_10f_11f_11f_rev
    GL_ARB_vertex_type_2_10_10_10_rev
    GL_ARB_window_pos
    GL_ATI_blend_equation_separate
    GL_ATI_draw_buffers
    GL_ATI_fragment_shader
    GL_ATI_separate_stencil
    GL_ATI_texture_compression_3dc
    GL_ATI_texture_env_combine3
    GL_ATI_texture_float
    GL_ATI_texture_mirror_once
    GL_EXT_abgr
    GL_EXT_bgra
    GL_EXT_blend_color
    GL_EXT_blend_equation_separate
    GL_EXT_blend_func_separate
    GL_EXT_blend_minmax
    GL_EXT_blend_subtract
    GL_EXT_compiled_vertex_array
    GL_EXT_copy_texture
    GL_EXT_draw_range_elements
    GL_EXT_fog_coord
    GL_EXT_framebuffer_blit
    GL_EXT_framebuffer_multisample
    GL_EXT_framebuffer_multisample_blit_scaled
    GL_EXT_framebuffer_object
    GL_EXT_gpu_program_parameters
    GL_EXT_multi_draw_arrays
    GL_EXT_packed_depth_stencil
    GL_EXT_packed_pixels
    GL_EXT_pixel_buffer_object
    GL_EXT_point_parameters
    GL_EXT_polygon_offset
    GL_EXT_provoking_vertex
    GL_EXT_rescale_normal
    GL_EXT_secondary_color
    GL_EXT_separate_specular_color
    GL_EXT_shadow_funcs
    GL_EXT_stencil_two_side
    GL_EXT_stencil_wrap
    GL_EXT_subtexture
    GL_EXT_texture
    GL_EXT_texture3D
    GL_EXT_texture_compression_dxt1
    GL_EXT_texture_compression_s3tc
    GL_EXT_texture_cube_map
    GL_EXT_texture_edge_clamp
    GL_EXT_texture_env_add
    GL_EXT_texture_env_combine
    GL_EXT_texture_env_dot3
    GL_EXT_texture_filter_anisotropic
    GL_EXT_texture_lod_bias
    GL_EXT_texture_mirror_clamp
    GL_EXT_texture_object
    GL_EXT_texture_rectangle
    GL_EXT_texture_sRGB
    GL_EXT_texture_sRGB_decode
    GL_EXT_texture_snorm
    GL_EXT_texture_swizzle
    GL_EXT_vertex_array
    GL_EXT_vertex_array_bgra
    GL_IBM_multimode_draw_arrays
    GL_IBM_rasterpos_clip
    GL_IBM_texture_mirrored_repeat
    GL_INGR_blend_func_separate
    GL_KHR_context_flush_control
    GL_KHR_debug
    GL_KHR_no_error
    GL_MESA_pack_invert
    GL_MESA_texture_signed_rgba
    GL_MESA_window_pos
    GL_MESA_ycbcr_texture
    GL_NV_blend_square
    GL_NV_conditional_render
    GL_NV_fog_distance
    GL_NV_light_max_exponent
    GL_NV_packed_depth_stencil
    GL_NV_primitive_restart
    GL_NV_texgen_reflection
    GL_NV_texture_barrier
    GL_NV_texture_env_combine4
    GL_NV_texture_rectangle
    GL_OES_EGL_image
    GL_OES_read_format
    GL_S3_s3tc
    GL_SGIS_generate_mipmap
    GL_SGIS_texture_border_clamp
    GL_SGIS_texture_edge_clamp
    GL_SGIS_texture_lod
    GL_SUN_multi_draw_arrays
using GL_EXT_texture_filter_anisotropic
using GL_ARB_texture_non_power_of_two
using GL_ARB_multitexture
using GL_ARB_texture_compression
using GL_EXT_framebuffer_object
using GL_EXT_packed_depth_stencil
using GL_EXT_blend_color
using GL_ARB_pixel_buffer_object
GL_MAX_TEXTURE_SIZE=2048
Using texture format GL_RGBA.
SetRatio: width/height parameters 1280x800
SetRatio: storage aspect ratio 8:5
SetRatio: assuming square pixels
SetRatio: display aspect ratio 8:5
SetRatio: gl_ratio 1.920000
SetRatio: multiplier 5/6
gld_Precache: E1M7 done in 486 ms
I_SignalHandler: Exiting on signal: Segmentation fault
I_ShutdownSound: 
eric@Toshiba-A215:~$ 


```


Anyone know what's going on?

---

### Post by emmaparker on 2018-09-03
I'm facing the same issue

---

### Post by wildmanne39 on 2018-09-03
Hello emmaparker, if you need help with an issue please start your own thread instead of posting in someone else's.

Thanks

---

