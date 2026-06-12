---
title: "Doom 3 crashes"
date: 2010-05-19
forum: Gaming &amp; Leisure
---

### Post by static_void on 2010-05-19
I just purchased a copy of doom 3 and have copied over all the correct .pk4 files to the doom3/base folder. I've also entered the cd key and I can see the main menu and all sub-menus. The problem is when I click 'new game' the screen just fades out and then crashes. I can't even press ctrl-alt-f1 to try and terminate the process. Any ideas on why this could be?. I've got a ati radeon x1300/1550 which is above the minimum spec and I'm running ubuntu 9.10. Also, other games play fine like openarena etc.?

---

### Post by ankit singh on 2010-05-19
close compiz-fusion and then try.Right click on ur desktop->change desk...->visual effects-> choose none there. post here if successful.

---

### Post by static_void on 2010-05-19
I've disabled the desktop effects by going into system->preferrences->appearance->visual effects and selecting None and it's still crashing.

---

### Post by ankit singh on 2010-05-19
change the game to lower resolution or u can see in doom setting box there 's a tool which adjust the game display settings acc to environment available. i think its name starts from detect hardware (i don remember that). Most probably its a display problem. I played doom via wine and mine was running very smooth when compiz fusion was disabled.Also check log files System->admin..->log file viewer->system log and see what is goofing up.Also once again review ur installation steps.

---

### Post by static_void on 2010-05-19
I changed the resolution to lowest, switched to window mode, turn off all effects (shadows etc) and it still crashes. I even tried to run it on wine but the installation failed. I also checked the system log and couldn't see anything.

I says in the linux install guide: [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/) that it will run on the ati proprietary driver fglrx or the DRI driver with the S3CT patch. I've tried installing the ati propietary driver but I don't thing my card is supported. any advice?

---

### Post by static_void on 2010-05-19
I managed to get the console output saved to a text file:

```

DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.1.2/255.255.255.0
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
/home/craig/.doom3/base
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
XFree86-VidModeExtension: not fullscreen, ignored
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: Mesa DRI R300 (RV515 7187) 20090101 x86/MMX/SSE2 TCL
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_MESAX_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_bgra GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.20
opened Alsa PCM device default for playback
device buffer size: 5461 frames ( 21844 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
X..GL_EXT_texture_compression_s3tc not found
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
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
found DLL in pak file: /usr/local/games/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/craig/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Jan 16 2007
Initializing event system
...473 event definitions
Initializing class hierarchy
...142 classes, 382184 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 1800 MHz
Compiled 'removeInitialSplineAngles': 1467.0 ms
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
terminal support disabled
pid: 1906
1008 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
guess failed, return default low-end VRAM setting ( 64MB VRAM )
64 MB Video Memory
Async thread started
idUsercmdGenLocal::MouseMove: Ignoring ridiculous mouse delta.
guid set to k0ofMWHCOtc

```


It says my VRAM is 64MB when it is actually 256MB...

---

### Post by ankit singh on 2010-05-19
> **static_void said:**
> I changed the resolution to lowest, switched to window mode, turn off all effects (shadows etc) and it still crashes. I even tried to run it on wine but the installation failed. I also checked the system log and couldn't see anything.

I says in the linux install guide: [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/) that it will run on the ati proprietary driver fglrx or the DRI driver with the S3CT patch. I've tried installing the ati propietary driver but I don't thing my card is supported. any advice?

After reading all the stuff i found that at the bottom of the page they mentioned this issue 


> Known issues  
Doom III would hang  during starting if you redirect the output. Pass *+set in_tty 0*  on the command line to fix: *$ doom3 +set in_tty 0 > output.txt*

---

### Post by ankit singh on 2010-05-19
pass this command at terminal

```
*doom3 +set in_tty 0 > output.txt*
```


You might want to google out for this

---

### Post by static_void on 2010-05-20
thats how I got the console output. It still crashes :(

---

### Post by Dezemerel on 2010-05-22
> **static_void said:**
> thats how I got the console output. It still crashes :(


Hi static_void.

Have you finally solved your problem? 
I also had some issues to run doom 3 as well, but finally I managed to get everything working. Maybe I could help you (or maybe not :)).

- What version of Ubuntu are you running? (Karmic, Lucid... x86, x64...)
- What is your graphics card?
- Have you installed its proprietary drivers, (if applicable)

---

### Post by gradinaruvasile on 2010-05-22
This is because the ati video drivers. The 1xxx series are no longer supported by Ati's proprietary fglrx, the only driver that works with these cards is the opensource. And that is not stable. At all.
The only thing to try is the patch you mentioned (S3CT). 
Also look around for newer driver versions in the xorg-edgers PPa.
BTW Ubuntu 10.04 has newer drivers, you may try to install it.

---

