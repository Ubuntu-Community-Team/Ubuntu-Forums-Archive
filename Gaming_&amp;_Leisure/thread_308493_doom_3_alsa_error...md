---
title: "doom 3 alsa error.."
date: 2006-11-28
forum: Gaming &amp; Leisure
---

### Post by tedrampart on 2006-11-28
I got doom 3 to install and run, but ran into that robot sound error alot of people had.  but I can't seem to find a way to fix it.  all the methods I've found are for oss,  or esd.. and none worked.  here's the output..

also I read on the F.A.Q. about some module called snd_io32, and it needed to be loaded.  synaptic can't find it, and its not installed..

thanks..

DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface wlan0 - 192.168.1.110/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/manimal/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /home/manimal/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /home/manimal/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /home/manimal/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /home/manimal/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /home/manimal/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /home/manimal/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /home/manimal/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /home/manimal/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /home/manimal/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/manimal/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/manimal/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/manimal/.doom3/base
/home/manimal/doom3/base
/home/manimal/doom3/base/pak007.pk4 (38 files)
/home/manimal/doom3/base/pak006.pk4 (48 files)
/home/manimal/doom3/base/pak005.pk4 (63 files)
/home/manimal/doom3/base/pak004.pk4 (5137 files)
/home/manimal/doom3/base/pak003.pk4 (4676 files)
/home/manimal/doom3/base/pak002.pk4 (6120 files)
/home/manimal/doom3/base/pak001.pk4 (8972 files)
/home/manimal/doom3/base/pak000.pk4 (2698 files)
/home/manimal/doom3/base/game03.pk4 (2 files)
/home/manimal/doom3/base/game02.pk4 (2 files)
/home/manimal/doom3/base/game01.pk4 (2 files)
/home/manimal/doom3/base/game00.pk4 (2 files)
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
Free86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce Go 6150/PCI/SSE2
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_clear_tag GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.11
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
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
found DLL in pak file: /home/manimal/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/manimal/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: May 10 2005
Initializing event system
...472 event definitions
Initializing class hierarchy
...142 classes, 381376 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 1600 MHz
Compiled 'weapon_shotgun::Lower': 3115.6 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67866, 1357320 bytes
   Functions: 2108, 250452 bytes
   Variables: 147244 bytes
    Mem used: 2478772 bytes
 Static data: 2277552 bytes
   Allocated: 3284208 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
Opening IP socket: localhost:-1
--- Common Initialization Complete ---
terminal support disabled
pid: 15171
976 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
found XNVCtrl extension 1.12
256 MB Video Memory
Async thread started
[COLOR="Red"]snd_pcm_writei short write: 3760 out of 4096
snd_pcm_writei short write: 3760 out of 4096
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei failed: Resource temporarily unavailable[/COLOR]
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



here's my system:
AMD64 Edgy
amd X2 1.6
1gb ram
nVidia geforce go 6150
(not sure what the soundcard is in the laptop, but its an nvidia chipset)

---

### Post by lakersforce on 2006-11-28
I have exactly the same problem too
solution appreciated!!

---

### Post by tedrampart on 2006-11-28
good to know I'm not the only one with the error...

I guess I should state that I'm running AMD64 .. which I think is the issue.. but I can't find a solution yet.

---

### Post by XVampireX on 2006-11-29
What happens exactly? Does it even initialize the game window? or is that all you get in terminal and nothing happens, just the text is scrolling?

I don't believe this has anything to do with ALSA, it may be giving these errors but it's not a reason for it not to work. Try to disable sound and see if it loads up.

---

### Post by tedrampart on 2006-11-29
the game loads up just fine aside from sound.  I even get a decent fps in it.  just the sound (when set up as alsa) gets all garbled.. and sounds like some cheesey space synth instead of the normal sounds.  when sound is set to best it does the same thing.. and on oss it has no sound..

---

### Post by lakersforce on 2006-11-29
same thing here except i am running the 386 architecture.
I guess I should add I'm running on a:
AMD Athlon 3200+
nForce onboard soundcard
NVidia Gforce 4 MX 4200

---

### Post by tedrampart on 2006-11-29
nvidia onboard sound.. sounds like mine too.. yours isn't by chance an high definition MCP51 chip is it?

could be an issue with nvidia sound.  I've had issues with it recently, and a few people I know that have nvidia sound also experienced issues with switching to ubuntu.. mainly so far its the lack of headphone jack on our laptops.. 

its pretty annoying, I could just play doom3 on my windows computer (which is actually setup for serious gaming), but I was hoping to have a few games to play on my night shifts when work gets quiet..

I'm going to look up some stuff on alsa and nvidia..

---

### Post by David Corrales on 2006-11-30
I was having robotic sound because alsa was using the default driver instead of the card explicitly. Here's what worked for me:
Edit *./doom3/base/DoomConfig.cfg*, look for these variables and change them to the value posted:

seta s_numberOfSpeakers "2"
seta s_driver "oss"
seta s_alsa_pcm "plughw:0"

---

### Post by tedrampart on 2006-11-30
okay, I just tried that, and now I get no sound.. 

I set the multimedia selector thing to autodetect.. and I tried oss, and alsa.. but none make sound now..

---

### Post by kvonb on 2006-12-02
Just to throw the thread off topic for a sec, can anyone point me to the best howto for installing Doom3 (Windows version) on Ubuntu?

Thanks :)

---

### Post by juraj on 2006-12-02
I just start the game with +s_driver="oss" or something like that, and it works flawlessly...

---

### Post by tedrampart on 2006-12-02
> **juraj said:**
> I just start the game with +s_driver="oss" or something like that, and it works flawlessly...

I think I stated earlier that this didnt work,  I've tried everything except installing newer versions of ALSA.. which I tried to do to fix my headphone jack issue, but that screwed everything up. 

I've pretty much given up.. doom3 isn't worth that much hassle, considering I've already played through it 3 times on my windows machine (which plays it alot better, 27" widescreen, full settings, and surround sound.. compared to my laptop running linux...)

thanks for the help though everyone..it was a good effort..

---

