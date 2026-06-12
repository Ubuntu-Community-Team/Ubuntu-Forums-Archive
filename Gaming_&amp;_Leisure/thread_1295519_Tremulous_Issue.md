---
title: "Tremulous Issue"
date: 2009-10-19
forum: Gaming &amp; Leisure
---

### Post by samh785 on 2009-10-19
I am having an intermittent problem with Tremulous. I have recently upgraded my computer to karmic, and that may have something to do with the issue.

This issue doesn't occur every time I start tremulous, but it does at least every 3 or 4 times. 

I started tremulous in a terminal, and this is the output I got:
(I believe the issue is near the end)
```
sam@sam-desktop:~$ tremulous
tremulous 1.1.0 linux-x86 Sep  6 2008
----- FS_Startup -----
Current search path:
/home/sam/.tremulous/base/wth.pk3 (8 files)
/home/sam/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2088 files in pk3 files
execing default.cfg
execing autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 8: 1280 1024
Using 8/8/8 Color bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce 8600 GT/PCI/SSE2
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 8600 GT/PCI/SSE2
GL_VERSION: 3.0.0 NVIDIA 185.18.36
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_instanced GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_framebuffer_object GL_ARB_geometry_shader4 GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NV_vertex_buffer_unified_memory GL_NV_shader_buffer_load GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 8192
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: 8, 1280 x 1024 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/uncreation.shader'
...loading 'scripts/q3map2_tremor.shader'
...loading 'scripts/tremor.shader'
...loading 'scripts/transit.shader'
...loading 'scripts/niveus.shader'
...loading 'scripts/nexus6.shader'
...loading 'scripts/karith.shader'
...loading 'scripts/atcs.shader'
...loading 'scripts/arachnid2.shader'
...loading 'scripts/jetpack.shader'
...loading 'scripts/core.shader'
...loading 'scripts/flame.shader'
...loading 'scripts/misc.shader'
...loading 'scripts/common-trem.shader'
...loading 'scripts/titan.shader'
...loading 'scripts/water.shader'
...loading 'scripts/displays.shader'
...loading 'scripts/plant_life.shader'
...loading 'scripts/stasis.shader'
...loading 'scripts/booster.shader'
...loading 'scripts/eggpod.shader'
...loading 'scripts/medistat.shader'
...loading 'scripts/mgturret.shader'
...loading 'scripts/reactor.shader'
...loading 'scripts/telenode.shader'
...loading 'scripts/trapper.shader'
...loading 'scripts/overmind.shader'
...loading 'scripts/tesla.shader'
...loading 'scripts/dcc.shader'
...loading 'scripts/hive.shader'
...loading 'scripts/level2.shader'
...loading 'scripts/human.shader'
...loading 'scripts/null.shader'
...loading 'scripts/weapons.shader'
...loading 'scripts/conkit.shader'
...loading 'scripts/advckit.shader'
...loading 'scripts/psaw.shader'
...loading 'scripts/mdriver.shader'
...loading 'scripts/flamer.shader'
...loading 'scripts/crosshairs.shader'
...loading 'scripts/grenade.shader'
...loading 'scripts/splash.shader'
...loading 'scripts/marks.shader'
...loading 'scripts/sprites.shader'
...loading 'scripts/muzzleflashes.shader'
----- finished R_Init -----
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "alsa".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  512
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x8d0ea50 dma buffer
No background file.
----------------------
Sound intialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1075 jump table targets
VM file ui compiled to 786313 bytes of code
ui loaded in 4596672 bytes on the hunk
UI menu load time = 321 milli seconds
UI menu load time = 18 milli seconds
UI menu load time = 16 milli seconds
--- Common Initialization Complete ---
Opening IP socket: localhost:30720
Hostname: sam-desktop
IP: 127.0.1.1
Received signal 11, exiting...
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------

```

I start it, and then it just shuts down for no reason that is apparent to me.
If anyone could help me with this it would be nice. :)

---

### Post by Sandlst on 2009-10-20
Signal 11 is apparently related to segmentation faults, you can read up a bit about it on wikipedia: [http://en.wikipedia.org/wiki/SIGSEGV]("http://en.wikipedia.org/wiki/SIGSEGV").

How did you install Tremulous?

I haven't seen a segfault in a long time, but when they used to happen to me I would try to solve it by installing the program using different method, ie. installing from source verses installing a deb; for some wacky reason this seemed to work, so that is where I would start.  I would prefer debs to anything else while running ubuntu of course, but if that is how you installed it already you can use this link to the .run file to install tremulous [here]("http://sourceforge.net/projects/tremulous/files/tremulous/1.1/tremulous-1.1.0-installer.x86.run/download"), which can be run via ```
./tremulous-1.1.0-installer.x86.run
```

---

### Post by samh785 on 2009-10-20
I installed it using the repositories in karmic :P

---

### Post by Sandlst on 2009-10-20
Do you happen to be running the 64-bit version of ubuntu?

You can try to install the game following the UGA guide, although if you are running 32-bit you can skip the first part about installing ia32-libs: [http://gwos.org/doku.php/guides:64bit:tremulous]("http://gwos.org/doku.php/guides:64bit:tremulous").

Also make sure you have the following packages installed:```
sudo apt-get install libc6 libopenal1 libsdl1.2debian
```Although it is highly unlikely that these are not already installed.

---

### Post by samh785 on 2009-10-21
yes I'm running the 32 bit version, and I also have all of those packages installed.

---

### Post by Sandlst on 2009-10-22
Unfortunately I'm all out of ideas, hopefully someone will reply with more knowledge.  As a last question did you have any luck with installing the game using other methods (rather than installing from the repository)?

---

### Post by samh785 on 2009-10-22
Actually yes, I installed it using the alternative method you supplied above, and I don't seem to have the issues anymore. It makes me wonder what the problem was with the repository version.

---

### Post by Sandlst on 2009-10-22
Yeah, I don't really understand segfault errors at all, but I've read they usually are the result of bugs, so it might be a good idea to make bug report about this.  I was actually planning on trying out Karmic myself this weekend, so I think I'll see if I can reproduce this issue.  I'm using an nvidia card also, hopefully we can sort this out.

---

### Post by samh785 on 2009-10-22
well, it just happened again... though it does seem to be happening less frequently. I'm going to turn on the openAL audio in tremulous and see if that helps. I don't profess to know wtf openAL is, but at this point I'm willing to try it. :P

Edit: I've been stopping and starting it at various times since I switched the audio to openAL, and I haven't had one problem since.

---

### Post by sefs on 2009-11-01
I am having the same exact problem, and have filed a bug report on it here...

[https://bugs.launchpad.net/ubuntu/+source/tremulous/+bug/461265](https://bugs.launchpad.net/ubuntu/+source/tremulous/+bug/461265)

How do you turn on the openAL audio in trem?

---

### Post by sefs on 2009-11-01
I switched to OpenAL within the trem client but the sound is grainy, scratchy, choppy, and indecipherable.  Might I have to change other sound settings in the trem client?

---

### Post by Mr_Miyagi on 2009-11-01
Try installing libsdl1.2debian-pulseaudio

---

### Post by DavidSev on 2009-11-01
Or try completely removing pulse audio.  It's a useless pile of buggy crap.

For openAL audio open the console (~ or `) and type "/s_useOpenAL 1" (without the quotes).

Try installing using the official installer ([http://tremulous.net/files/](http://tremulous.net/files/)) and also try switching out the client from that installer with a more up-to-date one, such as from [http://projects.mercenariesguild.net/projects/mgclient/files](http://projects.mercenariesguild.net/projects/mgclient/files) (unofficial build released by two of the devs).

---

### Post by sefs on 2009-11-01
> **Mr_Miyagi said:**
> Try installing libsdl1.2debian-pulseaudio

This was the first thing I installed after installing Karmic.

---

### Post by sefs on 2009-11-01
> **DavidSev said:**
> Or try completely removing pulse audio.  It's a useless pile of buggy crap.

For openAL audio open the console (~ or `) and type "/s_useOpenAL 1" (without the quotes).

Try installing using the official installer ([http://tremulous.net/files/](http://tremulous.net/files/)) and also try switching out the client from that installer with a more up-to-date one, such as from [http://projects.mercenariesguild.net/projects/mgclient/files](http://projects.mercenariesguild.net/projects/mgclient/files) (unofficial build released by two of the devs).

I'm timid about removing pulse audio since I may just go from frying pan into fire.  I will try your other suggestions.

---

### Post by samh785 on 2009-11-02
> **sefs said:**
> I'm timid about removing pulse audio since I may just go from frying pan into fire.  I will try your other suggestions.

Don't hold me to this, but I've heard that removing pulse audio in karmic removes some vital gnome libraries. Once again this is entirely hearsay, and you should definitely do some research on this for yourself about this.

---

