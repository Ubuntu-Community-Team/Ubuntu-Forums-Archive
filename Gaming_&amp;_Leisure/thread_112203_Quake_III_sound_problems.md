---
title: "Quake III sound problems"
date: 2006-01-03
forum: Gaming &amp; Leisure
---

### Post by duemler on 2006-01-03
Well, I found Quake III on my computer lol. No sound worked what so ever. I used a thing called   addsound.bat  and it fixed almost every sound. I can hear eveything except machinegun fire and steps. Instead of normal sounds, I hear an "error sound". It is an annoying sound. And eveytime i fire the mahcinegun or walk it makes that sound, but all other sounds work. 


Anyone know?   :confused:

---

### Post by Patriot1776 on 2007-12-09
Where'd you get the addsound.bat?

---

### Post by Patriot1776 on 2008-01-21
> **duemler said:**
> Well, I found Quake III on my computer lol. No sound worked what so ever. I used a thing called   addsound.bat  and it fixed almost every sound. I can hear eveything except machinegun fire and steps. Instead of normal sounds, I hear an "error sound". It is an annoying sound. And eveytime i fire the mahcinegun or walk it makes that sound, but all other sounds work. 


Anyone know?   :confused:

Hey, are you using the idSoftware-produced Quake III engine?  That's probably one reason why.

I came up with an alternative solution.  Get ioquake3 and install it using the .pk3 files off the Quake III Arena CD.  ioquake3 is the open source Quake III engine that games like OpenArena are built off of, but ioquake3 can use the proprietary id Software Q3A datafiles (.pk3's) to give you vanilla Quake III Arena.  It's what I did to finally fix my sound problems once and for all, as ioquake3 is built from the ground up with Linux in mind instead of being a Windows binary that's been re-engineered to work in Linux like idSoftware's Linux-version of Quake III Arena is.

Check out the website: [http://ioquake3.org/](http://ioquake3.org/)

---

### Post by disturbedite on 2008-01-21
i was gonna recommend ioquake3 also, but Patriot1776 beat me to it.  :)

---

### Post by Sockerdrickan on 2008-01-21
i was gonna recommend ioquake3 also, but Patriot1776 beat me to it. :)

---

### Post by Selim873 on 2010-11-27
I've had no sound... no matter what, I ended up having to use Wine but the gameplay was NO where as good as the Linux port, ioquake3 has no sound either... here's what I get.

EDIT: I know I'm running off sudo, I have to or else my settings won't save...

     Using Ubuntu 10.10 Maverick Meerkat.

```

ty@ty-laptop:~$ sudo /home/ty/ioquake3/ioquake3
[sudo] password for ty: 
ioq3 1.36 linux-i386 Apr 12 2009
----- FS_Startup -----
Current search path:
/home/ty/.q3a/baseq3
./baseq3/pak8.pk3 (9 files)
./baseq3/pak7.pk3 (4 files)
./baseq3/pak6.pk3 (64 files)
./baseq3/pak5.pk3 (7 files)
./baseq3/pak4.pk3 (272 files)
./baseq3/pak3.pk3 (4 files)
./baseq3/pak2.pk3 (148 files)
./baseq3/pak1.pk3 (26 files)
./baseq3/pak0.pk3 (3539 files)
./baseq3

----------------------
4073 files in pk3 files
execing default.cfg
execing q3config.cfg
com_zoneMegs will be changed upon restarting.
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.333
...setting mode 3: 640 480
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
Available modes: '1280x1024 640x480 800x600 832x624 1024x768 1152x864 720x400'
GL_RENDERER: Mesa DRI Intel(R) 945GME GEM 20100330 DEVELOPMENT x86/MMX/SSE2
Initializing OpenGL extensions
...GL_EXT_texture_compression_s3tc not found
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 945GME GEM 20100330 DEVELOPMENT x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 7.9-devel
GL_EXTENSIONS: GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_fragment_program GL_ARB_half_float_pixel GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_APPLE_object_purgeable GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays GL_OES_EGL_image
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_TEXTURE_UNITS_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
HACK: using vertex lightmap approximation
Initializing Shaders
----- finished R_Init -----
------ Initializing Sound ------
SDL_Init( SDL_INIT_AUDIO )... OK
SDL audio driver is "(UNKNOWN)".
SDL_OpenAudio() failed: No available audio device
Sound initialization failed.
--------------------------------
Loading vm file vm/ui.qvm...
VM file ui compiled to 594408 bytes of code
ui loaded in 1368576 bytes on the hunk
35 arenas parsed
32 bots parsed
--- Common Initialization Complete ---
IP: 127.0.0.1
IP: 192.168.2.3
IP6: ::1
IP6: fe80::eee:e6ff:fea0:728a%wlan0
Opening IP6 socket: [::]:27960
Opening IP socket: 0.0.0.0:27960
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
ty@ty-laptop:~$ 

```

---

