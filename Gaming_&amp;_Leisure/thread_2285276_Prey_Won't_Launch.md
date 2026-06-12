---
title: "Prey Won't Launch"
date: 2015-07-04
forum: Gaming &amp; Leisure
---

### Post by ricky-flammia on 2015-07-04
I successfully installed the Linux port of Prey using the DVD on my Ubuntu 15.04 x64 machine however, when I attempt to launch it, the screen turns black and then return to my desktop in a resolution of 640x480 (my normal desktop resolution is 1600x900). I checked the executables for unmet dependencies using the "lib" command in the terminal and made sure that all dependencies were met. Does anyone have any ideas as to how to remedy this issue? Thanks. P.S. I am running an AMD A10-7800 APU with 12 GB of 2133 MHZ DDR3 RAM.

---

### Post by MikeCyber on 2015-07-05
try in a terminal
cd /towhere/prey/is
ldd prey
if all libs are there
./prey
and paste the output here.

---

### Post by ricky-flammia on 2015-07-05
Thanks for the help. When I check for missing libraries I am told that prey isn't a dynamic executable so I individually checked each executable and filled in any holes that I found. Here is the output for "./prey". ```
richard@richard-Aspire-TC-120:~/prey$ ./prey
Prey 1.4.119 linux-x86 Nov 26 2008 00:03:20
found interface lo - loopback
found interface eth0 - 10.0.1.2/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/richard/prey/base/game00.pk4 with checksum 0xff851bf2
Loaded pk4 /home/richard/prey/base/game01.pk4 with checksum 0xa208af14
Loaded pk4 /home/richard/prey/base/game02.pk4 with checksum 0xaa46eb08
Loaded pk4 /home/richard/prey/base/game03.pk4 with checksum 0x39a5ed9c
Loaded pk4 /home/richard/prey/base/pak000.pk4 with checksum 0x7dc00ede
Loaded pk4 /home/richard/prey/base/pak001.pk4 with checksum 0xd06647b1
Loaded pk4 /home/richard/prey/base/pak002.pk4 with checksum 0x57dce443
Loaded pk4 /home/richard/prey/base/pak003.pk4 with checksum 0x263006fe
Loaded pk4 /home/richard/prey/base/pak004.pk4 with checksum 0xcc075380
Loaded pk4 /home/richard/prey/base/pak005.pk4 with checksum 0xead35190
Loaded pk4 /home/richard/prey/base/pak006.pk4 with checksum 0xed8ce397
Loaded pk4 /home/richard/prey/base/pak020.pk4 with checksum 0x39191193
Loaded pk4 /home/richard/prey/base/pak040.pk4 with checksum 0x40dd9bb5
Current search path:
/home/richard/.prey/base
/home/richard/prey/base
/home/richard/prey/base/pak040.pk4 (468 files)
/home/richard/prey/base/pak020.pk4 (23 files)
/home/richard/prey/base/pak006.pk4 (108 files)
/home/richard/prey/base/pak005.pk4 (10 files)
/home/richard/prey/base/pak004.pk4 (3739 files)
/home/richard/prey/base/pak003.pk4 (4111 files)
/home/richard/prey/base/pak002.pk4 (5337 files)
/home/richard/prey/base/pak001.pk4 (6270 files)
/home/richard/prey/base/pak000.pk4 (3318 files)
/home/richard/prey/base/game03.pk4 (2 files)
/home/richard/prey/base/game02.pk4 (10 files)
/home/richard/prey/base/game01.pk4 (2 files)
/home/richard/prey/base/game00.pk4 (2 files)
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
2661 strings read from strings/english001.lang
Couldn't open journal files
couldn't exec editor.cfg
execing default.cfg
execing preyconfig.cfg
couldn't exec autoexec.cfg
2661 strings read from strings/english001.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup SDL display connection
Initializing OpenGL display
Loading GL driver '(default)' through SDL
GL_RENDERER: AMD Radeon(TM) R7 Graphics  
GL_VENDOR: ATI Technologies Inc.
GL_VERSION: 2.1 (4.4.13374 Compatibility Profile Context 15.20.1013)
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_ARB_shader_objects GL_ARB_vertex_shader GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_geometry_shader4 GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_histogram GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_geometry_shader4 GL_EXT_gpu_shader4 GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays GL_ARB_texture_float 

------- Input Initialization -------
------------------------------------
...initializing OpenAL
...calling LoadLibrary( 'openal32.dll' ): dlopen 'openal32.dll' failed: openal32.dll: cannot open shared object file: No such file or directory
failed
...initializing OpenAL
...calling LoadLibrary( 'openal32.dll' ): dlopen 'openal32.dll' failed: openal32.dll: cannot open shared object file: No such file or directory
failed
------ SDL Sound Initialization ------
signal caught: Segmentation fault
si_code 1
double fault Segmentation fault, bailing out

```

Thanks again.

---

### Post by MikeCyber on 2015-07-06
ldd prey should work.
Anyway the output says to not find OpenAL. Hence install with synaptic openal. I guess the package is libopenal1

---

### Post by ricky-flammia on 2015-07-06
I reinstalled openal1 as well as installing the openal dev package and the openal dbg package because I wasn't sure if those might solve the problem but they didn't. Is there any further information that I can provide that may give you further insight in regards to solving this issue. Thanks.

---

### Post by Frogs Hair on 2015-07-06
I installed the appropriate Prey Ubuntu .deb using the following link and was not aware of any installation disk. You may want to remove Prey and try the .deb package. [https://preyproject.com/download](https://preyproject.com/download)

Excuse me if this a different Prey program.

---

### Post by ricky-flammia on 2015-07-06
Sorry. I should have further specified. I am referring to the video game Prey which is installed from a DVD and is a native Linux game after installing it using a patch.

---

### Post by MikeCyber on 2015-07-07
No idea what you two are using but this:
[http://icculus.org/prey/](http://icculus.org/prey/)
works flawlessly on my 15.04 64bit.

---

### Post by ricky-flammia on 2015-07-07
Thanks. That link is how I got the installer to install the DVD on Linux. The issue now is that when I click on the Prey Icon to launch the game, It launches as a black screen and then shuts down immediately after.

---

### Post by MikeCyber on 2015-07-08
The demo works? Maybe you messed up something with adding the retail files.
Install openal (libopenal1 and -data) and sdl (libsdl1.2debian also maybe libsdl-image1.2) with synaptic and paste the terminal output of the demo.

---

### Post by ricky-flammia on 2015-07-12
I think the issue is that I'm missing "libstdc++.so.5" and from what I have found it is obsolete so I'm now attempting to find a way to download it. If anyone has any suggestions, feel free to voice them. I would also like to mention that I have already downloaded multiple GNU Standard C++ Library v3 packages in both 32 and 64 bit forms.  Thanks. P.S. The demo reacts in the same as the full game when attempting to launch it in the sense that it also starts as a black screen followed by it crashing.

---

### Post by MikeCyber on 2015-07-12
Are you sure you're firing up the launch script and not the executable itself? That's what I get with the exe and the script:

michael@michael-ubuntu:/$ cd /m*/m*/DATA/pre*
michael@michael-ubuntu:/media/michael/DATA/prey-demo$ ./p*6
./prey-demo.x86: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
michael@michael-ubuntu:/media/michael/DATA/prey-demo$ ./prey-demo
Prey 1.4.119 linux-x86 Nov 25 2008 23:53:42
found interface lo - loopback
found interface eth0 - 192.168.0.11/255.255.255.0
found interface lxcbr0 - 10.0.3.1/255.255.255.0
------ Initializing File System ------
Loaded pk4 /media/michael/DATA/prey-demo/base/demo00.pk4 with checksum 0x86294060
...
loading fine

---

### Post by ricky-flammia on 2015-07-12
Here is the result that I get when attempting to launch the Prey demo. ```
richard@richard-Aspire-TC-120:~/prey-demo$ ./prey-demo
Prey 1.4.119 linux-x86 Nov 25 2008 23:53:42
found interface lo - loopback
found interface eth0 - 10.0.1.17/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/richard/prey-demo/base/demo00.pk4 with checksum 0x86294060
Current search path:
/home/richard/.prey-demo/base
/home/richard/prey-demo/base
/home/richard/prey-demo/base/demo00.pk4 (11273 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------

Running in restricted demo mode.

----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
2647 strings read from strings/english001.lang
Couldn't open journal files
couldn't exec editor.cfg
execing default.cfg
couldn't exec preyconfig.cfg
couldn't exec autoexec.cfg
2647 strings read from strings/english001.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup SDL display connection
Initializing OpenGL display
Loading GL driver '(default)' through SDL
GL_RENDERER: AMD Radeon(TM) R7 Graphics  
GL_VENDOR: ATI Technologies Inc.
GL_VERSION: 2.1 (4.4.13374 Compatibility Profile Context 15.20.1013)
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_ARB_shader_objects GL_ARB_vertex_shader GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_geometry_shader4 GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_histogram GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_geometry_shader4 GL_EXT_gpu_shader4 GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays GL_ARB_texture_float 

------- Input Initialization -------
------------------------------------
...initializing OpenAL
...calling LoadLibrary( './openal.so' ): dlopen './openal.so' failed: ./openal.so: cannot open shared object file: No such file or directory
failed
...initializing OpenAL
...calling LoadLibrary( './openal.so' ): dlopen './openal.so' failed: ./openal.so: cannot open shared object file: No such file or directory
failed
------ SDL Sound Initialization ------
signal caught: Segmentation fault
si_code 1
double fault Segmentation fault, bailing out

```
The reason why I think that libstdc++.so.5 is the issue is because the full game of Prey says that it is "not found" when I check for missing packages.

---

### Post by MikeCyber on 2015-07-13
I rather think that it's sound related. You have sound on your PC? If you look through mine, also 15.04, you see that it uses pulse. I would rather install that first. 
ldd on the exe returns: libstdc++.so.5 => not found
Hence that's not the showstopper. Here's my output:


```
michael@michael-ubuntu:/$ cd /m*/m*/DATA/pr*
michael@michael-ubuntu:/media/michael/DATA/prey-demo$ ls
base           libNvidiaVidMemTest.so  libstdc++.so.5  prey-demo      prey.png                xdg-open
libgcc_s.so.1  libSDL-1.2.so.0         openurl.sh      prey-demo.x86  uninstall-prey-demo.sh
michael@michael-ubuntu:/media/michael/DATA/prey-demo$ ldd pre*6
    linux-gate.so.1 =>  (0xf76ef000)
    ./libSDL-1.2.so.0 (0xf763b000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf75e9000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf75e3000)
    libstdc++.so.5 => not found
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7596000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf7579000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf73be000)
    /lib/ld-linux.so.2 (0xf76f0000)
michael@michael-ubuntu:/media/michael/DATA/prey-demo$ cd base
michael@michael-ubuntu:/media/michael/DATA/prey-demo/base$ ls
config.spec  default.cfg  demo00.pk4  gamex86.so  guis  preykey
michael@michael-ubuntu:/media/michael/DATA/prey-demo/base$ cd ..
michael@michael-ubuntu:/media/michael/DATA/prey-demo$ grep -r open*
.mojosetup/manifest/prey-demo.xml:            <file sha1="A0875D4A75BDC0E8D973123A3BAB6F331527543" crc32="BD13A6C6" md5="9214FDA3E89EED30111AB3F87BE2F370" mode="0644">openurl.sh</file>
.mojosetup/manifest/prey-demo.txt:openurl.sh
.mojosetup/manifest/prey-demo.lua:        ["openurl.sh"] = {
Binary file prey-demo.x86 matches
michael@michael-ubuntu:/media/michael/DATA/prey-demo$ ./prey-demo
Prey 1.4.119 linux-x86 Nov 25 2008 23:53:42
found interface lo - loopback
found interface eth0 - 192.168.0.11/255.255.255.0
found interface lxcbr0 - 10.0.3.1/255.255.255.0
------ Initializing File System ------
Loaded pk4 /media/michael/DATA/prey-demo/base/demo00.pk4 with checksum 0x86294060
Current search path:
/home/michael/.prey-demo/base
/media/michael/DATA/prey-demo/base
/media/michael/DATA/prey-demo/base/demo00.pk4 (11273 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------

Running in restricted demo mode.

----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
2647 strings read from strings/english001.lang
Couldn't open journal files
couldn't exec editor.cfg
execing default.cfg
execing preyconfig.cfg
couldn't exec autoexec.cfg
2647 strings read from strings/english001.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup SDL display connection
Initializing OpenGL display
Loading GL driver '(default)' through SDL
GL_RENDERER: GeForce GTX 770/PCIe/SSE2
GL_VENDOR: NVIDIA Corporation
GL_VERSION: 4.5.0 NVIDIA 346.59
idCommon::VPrintf: truncated to 4094 characters
GL_EXTENSIONS: GL_AMD_multi_draw_indirect GL_AMD_seamless_cubemap_per_texture GL_ARB_arrays_of_arrays GL_ARB_base_instance GL_ARB_bindless_texture GL_ARB_blend_func_extended GL_ARB_buffer_storage GL_ARB_clear_buffer_object GL_ARB_clear_texture GL_ARB_clip_control GL_ARB_color_buffer_float GL_ARB_compatibility GL_ARB_compressed_texture_pixel_storage GL_ARB_conservative_depth GL_ARB_compute_shader GL_ARB_compute_variable_group_size GL_ARB_conditional_render_inverted GL_ARB_copy_buffer GL_ARB_copy_image GL_ARB_cull_distance GL_ARB_debug_output GL_ARB_depth_buffer_float GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_derivative_control GL_ARB_direct_state_access GL_ARB_draw_buffers GL_ARB_draw_buffers_blend GL_ARB_draw_indirect GL_ARB_draw_elements_base_vertex GL_ARB_draw_instanced GL_ARB_enhanced_layouts GL_ARB_ES2_compatibility GL_ARB_ES3_compatibility GL_ARB_ES3_1_compatibility GL_ARB_explicit_attrib_location GL_ARB_explicit_uniform_location GL_ARB_fragment_coord_conventions GL_ARB_fragment_layer_viewport GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_no_attachments GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_geometry_shader4 GL_ARB_get_program_binary GL_ARB_get_texture_sub_image GL_ARB_gpu_shader5 GL_ARB_gpu_shader_fp64 GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_indirect_parameters GL_ARB_instanced_arrays GL_ARB_internalformat_query GL_ARB_internalformat_query2 GL_NV_internalformat_sample_query GL_ARB_invalidate_subdata GL_ARB_map_buffer_alignment GL_ARB_map_buffer_range GL_ARB_multi_bind GL_ARB_multi_draw_indirect GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pipeline_statistics_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_program_interface_query GL_ARB_provoking_vertex GL_ARB_robust_buffer_access_behavior GL_ARB_robustness GL_ARB_sample_shading GL_ARB_sampler_objects GL_ARB_seamless_cube_map GL_ARB_seamless_cubemap_per_texture GL_ARB_separate_shader_objects GL_ARB_shader_atomic_counters GL_ARB_shader_bit_encoding GL_ARB_shader_draw_parameters GL_ARB_shader_group_vote GL_ARB_shader_image_load_store GL_ARB_shader_image_size GL_ARB_shader_objects GL_ARB_shader_precision GL_ARB_query_buffer_object GL_ARB_shader_storage_buffer_object GL_ARB_shader_subroutine GL_ARB_shader_texture_image_samples GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shading_language_420pack GL_ARB_shading_language_include GL_ARB_shading_language_packing GL_ARB_shadow GL_ARB_sparse_buffer GL_ARB_sparse_texture GL_ARB_stencil_texturing GL_ARB_sync GL_ARB_tessellation_shader GL_ARB_texture_barrier GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_buffer_object_rgb32 GL_ARB_texture_buffer_range GL_ARB_texture_compression GL_ARB_texture_compression_bptc GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_cube_map_array GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_gather GL_ARB_texture_mirror_clamp_to_edge GL_ARB_texture_mirrored_repeat GL_ARB_texture_multisample GL_ARB_texture_non_power_of_two GL_ARB_texture_query_levels GL_ARB_texture_query_lod GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_rgb10_a2ui GL_ARB_texture_stencil8 GL_ARB_texture_storage GL_ARB_texture_storage_multisample GL_ARB_texture_swizzle GL_ARB_texture_view GL_ARB_timer_query GL_ARB_transform_feedback2 GL_ARB_transform_feedback3 GL_ARB_transform_feedback_instanced GL_ARB_transform_feedback_overflow_query GL_ARB_transpose_matrix GL_ARB_uniform_buffer_object GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_attrib_64bit GL_ARB_vertex_attrib_binding GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_vertex_type_10f_11f_11f_rev GL_ARB_vertex_type_2_10_10_10_rev GL_ARB_viewport_array GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT

------- Input Initialization -------
------------------------------------
...initializing OpenAL
...calling LoadLibrary( './openal.so' ): dlopen './openal.so' failed: ./openal.so: cannot open shared object file: No such file or directory
failed
...initializing OpenAL
...calling LoadLibrary( './openal.so' ): dlopen './openal.so' failed: ./openal.so: cannot open shared object file: No such file or directory
failed
------ SDL Sound Initialization ------
SDL is using audio backend 'pulse'.
allocated a mix buffer of 32768 bytes
SDL_AudioSpec: 44100 freq, S16LSB, 2 channels, 512 samples.
Opening audio device...
Audio device is ready.
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
glprogs/interactionUpdate.vfp
glprogs/interactionUpdate.vfp
glprogs/interactionCubeMaps.vfp
glprogs/interactionCubeMaps.vfp
glprogs/interactionNormBump.vfp
glprogs/interactionNormBump.vfp
glprogs/interactionNormBumpH.vfp
glprogs/interactionNormBumpH.vfp
glprogs/interactionAll.vfp
glprogs/interactionAll.vfp
-------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
--------- Initializing Game ----------
gamename: basePrey-1
gamedate: Feb 15 2008
Initializing event system
...1025 event definitions
Initializing class hierarchy
...357 classes, 2050000 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 4270.96 MHz
Compiled 'removeInitialSplineAngles': 1044.6 ms
---------- Compile stats ----------

Memory usage:
     Strings: 58, 9168 bytes
  Statements: 92650, 1853000 bytes
   Functions: 2987, 352692 bytes
   Variables: 411160 bytes
    Mem used: 3784416 bytes
 Static data: 3617736 bytes
   Allocated: 5132044 bytes
 Thread size: 7080 bytes

...11 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
--- Common Initialization Complete ---
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 2800
15984 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
Trying XNVCTRL approach...
Loaded './libNvidiaVidMemTest.so'
NVidia test says 2048
2048 MB Video Memory
Async thread started
--------- Game Map Shutdown ----------
--------------------------------------
Shutting down sound hardware
------ SDL Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
Shutting down SDL subsystem
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------
shutdown terminal support
Segmentation fault (core dumped)
michael@michael-ubuntu:/media/michael/DATA/prey-demo$
```

---

### Post by ricky-flammia on 2015-07-14
I do have sound on my PC. I now agree that it's due to a sound issue but I already have the packages that you suggested installed so I'm not really sure where to go from here.

---

### Post by MikeCyber on 2015-07-14
I haven't had sound issues since I've left Suse some 6 years ago for that reason.
Google should help like for ex this page:
[URL="https://wiki.ubuntu.com/PulseAudio"]https://wiki.ubuntu.com/PulseAudio
[/URL]
If you haven't done so, install libsdl-mixer1.2 as prey uses sound through sdl.

---

### Post by ricky-flammia on 2015-07-14
Thanks.

---

### Post by MikeCyber on 2015-07-15
It works now?

---

### Post by MikeCyber on 2015-07-22
Maybe playing around with pavucontrol helps like for me:

[http://ubuntuforums.org/showthread.php?t=2287680](http://ubuntuforums.org/showthread.php?t=2287680)

---

### Post by ricky-flammia on 2015-08-11
I just wanted to update everyone who helped me in this thread by letting you know that I recently switched to Ubuntu 12.04 for a unrelated reason and once again attempted to install Prey to find that not only does it contain a GUI based installer which I discovered can be used by removing .bin at the end of the application name and then clicking on it but furthermore the game now runs.

---

