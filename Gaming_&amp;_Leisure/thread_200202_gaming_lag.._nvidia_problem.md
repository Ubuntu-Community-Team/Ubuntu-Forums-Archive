---
title: "gaming lag.. nvidia problem?"
date: 2006-06-19
forum: Gaming &amp; Leisure
---

### Post by maka on 2006-06-19
running: dapper 32bit
specs: amd 3200+, 768 mb ram.

I have a nvidia 5200 and i installed the drivers for it.


When I play CS it lags with fps which fluctuates too much...  Anyways I was wondering if this is a problem with my nvidia driver installation.

is there any way how i can check if its correctly installed
or how do i go about _completely_ uninstalling the drivers and reinstalling them?

when i type glxgears -printfps
i get:

13820 frames in 5.0 seconds = 2763.981 FPS
18545 frames in 5.0 seconds = 3708.864 FPS
16154 frames in 5.0 seconds = 3230.685 FPS

oh yeah, i dont have any XGL or compiz installed..

thanks in advance! :confused:

---

### Post by livingtarget on 2006-06-19
First thing is did you install the drivers from the nvidia website?

If you did so, try opening a console and doing:
> 
sudo apt-get update
sudo apt-get install nvidia-glx
This will install the drivers that are in dapper's repositories, these are usually your best choice.

Optionally you can remove/reinstall those by doing the following and then installing them again.
> sudo apt-get remove nvidia-glx

I always find that the drivers from the nvidia are a bit tougher to get working.

If you've already done that, try checking the equivelant of your task/process manager and see what is eating up cpu cycles. As that is usally a good cause for fluctuating frame speeds.

---

### Post by Trab on 2006-06-19
try typing glxinfo in bash and posting the results here.
it gives more info about ur card.
cheers,
Trab
(PS. if it says direct rendering: no, then thats why. im having problems with that right now, its driving me up the wall)

---

### Post by AngryKidJoe on 2006-06-20
You are not alone in the inconsistant frame rate department.

---

### Post by handy on 2006-06-20
I use [**Automatix**]("http://www.ubuntuforums.org/showthread.php?t=177646") to do a lot of dirty-work for me.

It will install the closed nVidia drivers for you, amongst over 45 (at last count) other pieces of popular software that are listed in it's install menu!

---

### Post by maka on 2006-06-20
[QUOTE=Trab]try typing glxinfo in bash and posting the results here.
it gives more info about ur card.
cheers,
Trab
(PS. if it says direct rendering: no, then thats why. im having problems with that right now, its driving me up the wall)[/QUOTE]

this is what i get:
```
-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE2/3DNOW!
OpenGL version string: 2.0.2 NVIDIA 87.62
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side,
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_sRGB,
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_HP_occlusion_test,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color,
    GL_NV_depth_clamp, GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance,
    GL_NV_fragment_program, GL_NV_fragment_program_option, GL_NV_half_float,
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint,
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range,
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners,
    GL_NV_register_combiners2, GL_NV_texgen_reflection,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3,
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x118 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

---

### Post by livingtarget on 2006-06-20
All looks healthy on the driver side... ](*,) as far as i can tell

---

### Post by AngryKidJoe on 2006-06-20
Maka, what sound card do you have? I'm actually noticing the rate dropping when a sound plays and distorts. I have a SoundBlaster Live! 24-Bit, it could well be that these are related.

Thinking back to when my frame rate was smooth as glass, I was running onboard sound and not my PCI card.

---

### Post by handy on 2006-06-20
I am running a SBLive 5:1 card, & don't notice any lag in UT2k4 on Dapper, or GW under Breezy (Cedega).

For all it's worth!

---

### Post by maka on 2006-06-20
[QUOTE=AngryKidJoe]Maka, what sound card do you have? I'm actually noticing the rate dropping when a sound plays and distorts. I have a SoundBlaster Live! 24-Bit, it could well be that these are related.

Thinking back to when my frame rate was smooth as glass, I was running onboard sound and not my PCI card.[/QUOTE]

lol im not even sure. i think its just an onboard generic one.

anyways i just found something out.

after finding out about this "powernowd" thing which controls ur cpu,
i killed the process and tried the game again

after that, i was able to get fps constant at above 60! 8) 

not sure what the downsides of having powernowd off is... im thinking it has to do with overheating possibly.

---

### Post by AngryKidJoe on 2006-06-20
Post when you find out, or I'll see what I can dig  up on it.

---

### Post by maka on 2006-06-21
[QUOTE=AngryKidJoe]Post when you find out, or I'll see what I can dig  up on it.[/QUOTE]

still havent found out anything about powernowd..

but i was thinking about how i can go about to just disable powernowd whenever I run wine to enable full CPU power when I'm gaming.  otherwise turn back on Powernowd.

I was thinking about writing a script to killall powernowd whenever I run CS (Wine), but this command requires sudo.  So i was wondering if anyone knew how to get around this because I don't want to have to type in my password everytime I run the script.  Thanks in advance. ](*,)

---

### Post by handy on 2006-06-22
If you haven't done so, please try this:

Right click on the **Menu Bar**, then ***choose***, -  **Add to Panel**.  Then ***choose***  - **CPU Frequency Scaling Monitor** from the options window.  

***Choose*** in the last case, means drag the **Frequency Scaling Monitor** up to the **Menu Bar**. ;) 

Now open a Terminal & type the following:
[B][I]
sudo chmod +s /usr/bin/cpufreq-selector[/I][/B]

Now you have the option of left clicking on the little icon in the menu bar & choosing how you want your CPU to run!

I leave mine at **ondemand**, except when I play games, then I use **performance** switching back to **ondeman**d after I finish gaming! :KS

**[Edit:]** *By the way, if you don't use powernowd, it just means that your CPU & the CPU fan will run at full speed all the time.  Thats the way all machines work that don't have a powersaving feature built into the hardware.  It's not really any kind of problem.  Unless you look at it from the global resources point of view!*

---

### Post by maka on 2006-06-23
> **handy]If you haven't done so, please try this:

Right click on the **Menu Bar**, then ***choose***, -  **Add to Panel**.  Then ***choose***  - **CPU Frequency Scaling Monitor** from the options window.  

***Choose*** in the last case, means drag the **Frequency Scaling Monitor** up to the **Menu Bar**.  said:**
> [I]
sudo chmod +s /usr/bin/cpufreq-selector[/I][/B]

Now you have the option of left clicking on the little icon in the menu bar & choosing how you want your CPU to run!

I leave mine at **ondemand**, except when I play games, then I use **performance** switching back to **ondeman**d after I finish gaming! :KS

**[Edit:]** *By the way, if you don't use powernowd, it just means that your CPU & the CPU fan will run at full speed all the time.  Thats the way all machines work that don't have a powersaving feature built into the hardware.  It's not really any kind of problem.  Unless you look at it from the global resources point of view!*


wow!!!! thank you, that helps a lot! btw, is there any command line command which can change the CPU from ondemand to performance or vice versa?

Thanks again! :D

---

### Post by AngryKidJoe on 2006-06-23
[QUOTE=handy]If you haven't done so, please try this:

Right click on the **Menu Bar**, then ***choose***, -  **Add to Panel**.  Then ***choose***  - **CPU Frequency Scaling Monitor** from the options window.  
[/QUOTE]
I don't see it in KDE. I remember seeing it in GNOME. If you know the setting in KDE, please share. I'm going to go look to see what I can find on it.

---

### Post by handy on 2006-06-24
[QUOTE=AngryKidJoe]I don't see it in KDE. I remember seeing it in GNOME. If you know the setting in KDE, please share. I'm going to go look to see what I can find on it.[/QUOTE]

Sorry, I don't know KDE!

[QUOTE=Maka]wow!!!! thank you, that helps a lot! btw, is there any command line command which can change the CPU from ondemand to performance or vice versa?[/QUOTE]

My pleasure, I enjoy that one too! :) 

The **cpufreq-selector** command may do it for you Maka:

[B][I]handy@BirdFish:~$ cpufreq-selector -?
Usage:
  cpufreq-selector [OPTION...] - CPUFreq Selector

Help Options:
  -?, --help          Show help options

Application Options:
  -c, --cpu           CPU Number
  -g, --governor      Governor
  -f, --frequency     Frequency in KHz

handy@BirdFish:~$[/I][/B]

Let us know how you go? :KS

---

### Post by AngryKidJoe on 2006-06-24
*sudo apt-get cpufreq* works just fine for KDE then. *goes to follow the thread's suggestions*

---

