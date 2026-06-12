---
title: "Doom3 sound"
date: 2008-10-25
forum: Gaming &amp; Leisure
---

### Post by Gezzy on 2008-10-25
Hi, im having troube getting sound to work in doom3.
The game it self runs fine, but without sound obviously :)

Sound seems to work in most games i've tried so far.

My soundcard is X-Fi and I belive im using something calles OSS.

Here is the output for when I start doom:

```
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.1.66/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/gez/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /home/gez/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /home/gez/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /home/gez/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /home/gez/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /home/gez/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /home/gez/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /home/gez/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /home/gez/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /home/gez/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/gez/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/gez/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /home/gez/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/gez/.doom3/base
/home/gez/doom3/base
/home/gez/doom3/base/pak008.pk4 (3 files)
/home/gez/doom3/base/pak007.pk4 (38 files)
/home/gez/doom3/base/pak006.pk4 (48 files)
/home/gez/doom3/base/pak005.pk4 (63 files)
/home/gez/doom3/base/pak004.pk4 (5137 files)
/home/gez/doom3/base/pak003.pk4 (4676 files)
/home/gez/doom3/base/pak002.pk4 (6120 files)
/home/gez/doom3/base/pak001.pk4 (8972 files)
/home/gez/doom3/base/pak000.pk4 (2698 files)
/home/gez/doom3/base/game03.pk4 (2 files)
/home/gez/doom3/base/game02.pk4 (2 files)
/home/gez/doom3/base/game01.pk4 (2 files)
/home/gez/doom3/base/game00.pk4 (2 files)
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
Free86-VidModeExtension Activated at 1280x1024
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce 8800 GTS/PCI/SSE2
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother.WARNING: ioctl SNDCTL_DSP_SPEED failed to get the requested frequency 44100, got 96000
close sound device
WARNING: sound subsystem disabled
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
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
...using GL_NV_register_combiners
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using EXT_depth_bounds_test
---------- R_NV20_Init ----------
---------------------------------
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Available.
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
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
found DLL in pak file: /home/gez/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/gez/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Jan 16 2007
Initializing event system
...473 event definitions
Initializing class hierarchy
...142 classes, 382184 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 1600 MHz
Compiled 'weapon_handgrenade::Lower': 1299.4 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67875, 1357500 bytes
   Functions: 2109, 250532 bytes
   Variables: 147376 bytes
    Mem used: 2479288 bytes
 Static data: 2277552 bytes
   Allocated: 3284544 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
Opening IP socket: localhost:-1
--- Common Initialization Complete ---
------------- Warnings ---------------
during DOOM 3 initialization...
WARNING: ioctl SNDCTL_DSP_SPEED failed to get the requested frequency 44100, got 96000
WARNING: sound subsystem disabled
2 warnings
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 7816
2032 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
found XNVCtrl extension 1.14
320 MB Video Memory
Async thread started
guid set to MyVhohH9ezc
--------- Game Map Shutdown ----------
--------------------------------------
idRenderSystem::Shutdown()
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------
shutdown terminal support

```

_any_ held is welcome :)
Im clueless :)

---

### Post by crazyfuturamanoob on 2008-10-25
Yeah. Doom 3 can't scare a sh*t without sounds. :(

---

### Post by Azure.Rise on 2008-10-25
Hm, I have sounds but it lags behind the game a little.

---

### Post by crazyfuturamanoob on 2008-10-26
Doom3 sound didn't work for me if I had another application running that might use alsa. In my case, it was gstreamer in firefox, so I had to close firefox.

---

