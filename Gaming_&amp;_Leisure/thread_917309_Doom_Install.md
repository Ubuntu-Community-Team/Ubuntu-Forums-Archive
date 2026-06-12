---
title: "Doom Install"
date: 2008-09-11
forum: Gaming &amp; Leisure
---

### Post by LaidbackBill on 2008-09-11
Recently installed Doom 3 on 8.04 with less than stellar results.  I previously had it installed on Gutsy but on a different board and gpu.  This time I used the alternative installer with the sudo command and it installed in the root location.  Unfortuately it has no sound and the video stops at various points.  Two questions: can I reinstall over the old install or can I remove it?  Need permissions which I know nothing about. Below is a printout of the loading process with the problems.bill@bill-desktop:~$ doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface ppp0 - 66.81.243.48/255.255.255.255
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/bill/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
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
Free86-VidModeExtension Activated at 1152x864
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: Radeon X1950 Series
GL_EXTENSIONS: GL_AMD_performance_monitor GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_KTX_buffer_region GL_NV_blend_square GL_NV_texgen_reflection GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_WIN_swap_hint WGL_EXT_swap_control 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.15
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
...using GL_ATI_separate_stencil
...using GL_ATI_fragment_shader
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
GL_NUM_FRAGMENT_REGISTERS_ATI: 6
GL_NUM_FRAGMENT_CONSTANTS_ATI: 8
GL_NUM_PASSES_ATI: 2
GL_NUM_INSTRUCTIONS_PER_PASS_ATI: 8
GL_NUM_INSTRUCTIONS_TOTAL_ATI: 16
GL_COLOR_ALPHA_PAIRING_ATI: 1
GL_NUM_LOOPBACK_COMPONENTS_ATI: 3
GL_NUM_INPUT_INTERPOLATOR_COMPONENTS_ATI: 3
FPROG_FAST_PATH
---------------------
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
found DLL in pak file: /usr/local/games/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/bill/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Jan 16 2007
Initializing event system
...473 event definitions
Initializing class hierarchy
...142 classes, 382184 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 2000 MHz
Compiled 'removeInitialSplineAngles': 1367.6 ms
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
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 6563
2032 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
guess failed, return default low-end VRAM setting ( 64MB VRAM )
64 MB Video Memory
Async thread started
snd_pcm_writei 4096 frames failed: Broken pipe
guid set to 5FiUHMO7AZ4
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
--------- Game Map Shutdown ----------
--------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------
shutdown terminal support
bill@bill-desktop:~

---

