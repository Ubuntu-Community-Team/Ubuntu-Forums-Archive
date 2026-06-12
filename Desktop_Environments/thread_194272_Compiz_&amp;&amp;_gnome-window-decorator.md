---
title: "Compiz &amp;&amp; gnome-window-decorator"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Barns on 2006-06-11
Hi all, (this is my first post...),

I've been using Ubuntu for a while, was using Breezy, now using Dapper. I have had no problems, till now.

I decided to try install Xgl and Compiz by following the tutorial on the wiki. Everything seemed to go ok, this is what I did:

Installed packages: xserver-xgl, compiz and compiz-gnome. I couldn't install gset-compiz as there isn't a gset-compiz package in the repository I use (I'm on an university campus, and I am restricted to the local mirror of the official repository). (Important note: I'm using an AMD64 system, so that seems to make sense).

I then configured Xgl and got it working. My system loads Xgl instead of X.org and seems fine with it.

Then, however, things start to work a little less well: If I launch the gnome-window-decorator (using ```
gnome-window-decorator &
```), it launches, but there is no noticeable output. Then if I launch compiz (using 
```
compiz --replace gconf
```) all my window borders disapear and the only way I can get them back is by switching back to metacity. (Note here, if after running the above, I run ```
ps -A | grep compiz
```, I get no output at all, so it seems as though compiz doesn't actually remain running?

I've read what posts I can find on these forums, and others, but I can't seem to find a way to get compiz to load window borders. There are no settings for compiz available if I run ```
gconf editor
```.

I'd apreciate any help with being able to get compiz to generate settings, and getting a few window borders, etc...

Thanks,
Barns

---

### Post by olsonar on 2006-06-11
can you start compiz in a terminal and give us the output?

---

### Post by Barns on 2006-06-11
If I type in ```
compiz --replace
``` I get no output whatsoever, except that my window decorations vanish. Compiz also seems to terminate instantly as I am returned to the shell.

---

### Post by Rashid584 on 2006-06-11
Not that it'll help you at all, but I'm experiencing similar, if not the same problem. I was about to make my own thread so its fortunate I just saw this.

I'd be interested if anyone finds a fix/solution.

-Rashid

---

### Post by pratzabrat on 2006-06-11
I also align myself with the expressed views. On starting compiz window borders disappear. When I try to open one of the borderless windows from the taskbar, all other windows are thrown up. Plus movie playback is jerky in fullscreen.

---

### Post by Rashid584 on 2006-06-11
I don't even get those windows thrown up. If I click on anything on kicker (i use kubuntu) nothing happens.

And I can't type anything in a terminal emulator because even if the window is open, and the command typed in, it won't let me focus on the window, if that makes sense?

-Rashid

---

### Post by dlyons on 2006-06-11
Aye, I am at the same point as well. Was going to make a post but found this one. Everything else seems to work fine, my nvidia drivers are installed correctly as I get the splash at startup. Also, ps -A | grep Xgl shows it is running. However, when compiz runs the windows disappear and ps -A | grep compiz shows no output. compiz shows no output. 

Hopefully we can get this resolved...

---

### Post by christhemonkey on 2006-06-11
You have to run the gnome-window-decorator **after** compiz --replace

(at least in my experience)

---

### Post by dlyons on 2006-06-11
I still get the same thing.. gnome-window-decorator runs but there is no compiz process running. Just typing 'compiz' at the prompt shows no output and no process. What gives? I'm on AMD64 / Nvidia.

---

### Post by ironfistchamp on 2006-06-11
I get pretty much the same thing. If I run the "thefuture" script from a tutorial on here I get

 
$ thefuture
$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

And the window borders disappear. I can't switch between windows at all. The tutorial said run the command many times to fix it but it doesn't work. It just says that there is one already running. 

Thanks

---

### Post by Rashid584 on 2006-06-11
Curious...

Is it a bug or have we all done something (the same thing?) wrong?

-Rashid

---

### Post by dlyons on 2006-06-11
Let's post our specs--

AMD64 / Ubuntu 6.06 / Nvidia GeForce 6800

My drivers are installed correctly. I've installed and reinstalled glitz, mesa, all the libraries i could think of, xgl, and compiz. Xgl runs fine. compiz just crashes with no output!!

Also, my gconf-editor shows no entry for compiz. and 'compiz --help' shows compiz is responding in some fashion.

---

### Post by ironfistchamp on 2006-06-11
AMD64 (running 32bit though as its easier)/Ubuntu 6.06/7800GTX 256Mb

I am pretty sure my drivers are installed ok and I followed the tutorial. Same here with the gconf-editor.

---

### Post by Rashid584 on 2006-06-11
Intel P4 / Kubuntu 6.06 / Intel 82845G/GL ?MB

I'm also confident my drivers are installed fine. XGL runs quite/very slowly, but is tolerable.

-Rashid

---

### Post by dlyons on 2006-06-11
Hmmmm..... it's killing me, I really can't seem to figure this out. Tried everything I can think of. I've read many reports of glx/compiz running FINE.. I don't get it..

---

### Post by petew00 on 2006-06-11
Hi,

I experience the same problem too. However: are you sure that glx is really up and running. When I type 'glxinfo' it says:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

---

### Post by petew00 on 2006-06-11
For the record: I had previously installed SuSE 10.1 on my Dell Precision M65, Intel DuoCore, Nvidia Quadro FX. 

Glx and compiz where running absolutely FINE on gnome.

---

### Post by ironfistchamp on 2006-06-11
My glx seems fine

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
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
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7800 GTX/PCI/SSE2/3DNOW!
OpenGL version string: 2.0.2 NVIDIA 87.62
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers,
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow,
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite,
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query,
    GL_EXT_vertex_array, GL_HP_occlusion_test, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence,
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program,
    GL_NV_fragment_program_option, GL_NV_fragment_program2, GL_NV_half_float,
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint,
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range,
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners,
    GL_NV_register_combiners2, GL_NV_texgen_reflection,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3,
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_NV_vertex_program3,
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum
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
0x134 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


Thats the output I get from glxinfo. Don't understand any of it but there you go.

---

### Post by dlyons on 2006-06-11
My glxinfo and glxgears brings up:

name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  147 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  15
  Current serial number in output stream:  16


Someone informed me that glx on nvidia/64 under XGL doesn't work? glxgears and glxinfo work under X.Org.

---

### Post by ironfistchamp on 2006-06-11
I gave up on the 64 when I found out flash didnt work straight off :p I was alot less patient in those days.

---

### Post by Rashid584 on 2006-06-11
glxinfo for me is same as ironfistchamp, seems fine

Well, some other (minor) annoyances (caused mostly by myself) have driven me to decide to re-install Kubuntu...so I'll have another go at XGL and compiz (when i get the time) and get back to see if it makes any difference.

-Rashid

---

### Post by ironfistchamp on 2006-06-11
I really don't want to have to reinstall. Hope we can find some way to sort this.

---

### Post by christhemonkey on 2006-06-11
Ironfistchamp:
Your glxinfo shows that you are missing the essential GLX_EXT_texture_from_pixmap.
This is the glx extension that compiz needs to function.
Currently nvidia do not have it in their drivers, so you need to use the mesa rendering, which does not utilise the full potential of the GPU.

But still, hopefully nvidia will release new drivers with GLX_EXT_texture_from_pixmap support!

---

### Post by ironfistchamp on 2006-06-11
Oh right so waiting is the key?

---

### Post by christhemonkey on 2006-06-11
Indeed.

The GLX_EXT_texture_from_pixmap extension was written with some of the nvidia developers support, so them writting it into the nvidia drivers should be arround anytime soon....

---

### Post by ironfistchamp on 2006-06-11
Great :D  I hate doing drivers on linux tho. On windows its double click next next next finish restart done. On this I dont have a clue.

---

### Post by bulldog on 2006-06-11
Well, I did my first install  on a 64bit version too and didn't get it to work either.
So I installed the i386 Ubuntu and every thing works fine for now.
I think that something is missing for the 64bit,don't know what however.
My system is an AMD3200 64bit and the graphic's run with an nVidia 6800Ultra with i386 Ubuntu.
I used this tutorial,

[http://www.compiz.net/viewtopic.php?id=652](http://www.compiz.net/viewtopic.php?id=652)

I hope this is of any use to you.

---

### Post by christhemonkey on 2006-06-11
For the nvidia drivers, its really not that hard;

Either someone will package them for us (which is always nice),  in which case we can just go into synaptic and install linux-restricted-modules-`uname -r`

Or we will have to install with nvidias installer,
which is normally just an sudo sh ./nvidia-installer.sh (or something like that....)

And at least we dont have to restart the whole pc :p
Just the Xserver...

---

### Post by ironfistchamp on 2006-06-11
Yeah I like the whole not restarting the whole computer but I hate the three flashes and the detailed output of why the X Server didnt start.

---

### Post by Rashid584 on 2006-06-11
Well, I'm not using an nVidia card so any ideas why it dies for me after a few minutes?

This is my output from glxinfo:

rashid@rashid-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGI_video_sync, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20050225
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1,
    GL_APPLE_client_storage, GL_APPLE_packed_pixels,
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
rashid@rashid-desktop:~/easyubuntu$ glxinfo | grep GLX_EXT_texture*
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
rashid@rashid-desktop:~/easyubuntu$ clear
rashid@rashid-desktop:~/easyubuntu$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGI_video_sync, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20050225
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1,
    GL_APPLE_client_storage, GL_APPLE_packed_pixels,
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

-Rashid

---

### Post by dlyons on 2006-06-11
Ok, I reinstalled the x86 ubuntu and not 64-bit, used the same guide as bulldog and had it running in about 5 minutes :) thanks!!!!

---

### Post by dlyons on 2006-06-11
wow... just a sidenote, xgl/compiz seems to run FASTER than x.org... everything "just works". freaking awesome. also as a benefit to 32-bit i get my flash player :) everyone with 64-bit... imo, it's not worth the effort right now... do yourself a favor and install i386.

---

### Post by ironfistchamp on 2006-06-11
Christhemonkey or anyone am I right in thinking that this magic guide won't work for me? Even if it should sods law that it won'.t.:p

---

### Post by bulldog on 2006-06-12
[QUOTE=dlyons]wow... just a sidenote, xgl/compiz seems to run FASTER than x.org... everything "just works". freaking awesome. also as a benefit to 32-bit i get my flash player :) everyone with 64-bit... imo, it's not worth the effort right now... do yourself a favor and install i386.[/QUOTE]

Nice to hear I could help you out
Yep I had the same experience,and the flashplayer is a nice bonus.;) 
Seem something isn't working in 64bit mode.
But i386 works fine enough for me,so I stick with it.

If my memory not fales me,I've seen a guide fot the ATI cards too..........
when I find it I'll post it here.
Here is some extra info,

[http://www.compiz.net/viewforum.php?id=4](http://www.compiz.net/viewforum.php?id=4)

---

### Post by Rashid584 on 2006-06-12
I have a Pentium processor so it can't be anything to do with 64-bit :S

I'm deciding whether its worth re-installing...is it likely to make a difference? 

-Rashid

---

### Post by bulldog on 2006-06-12
If you don't try you'll never know:p 
With 64 bit I mean the X64 install package of Ubuntu and not the processor.
I have a AMD X64 proc but I installed the 32-bit version of Ubuntu. 
Can't speak about Intel procs however,only my own experience I can share with you.

But if you can get Xgl/Compiz working on your system you'll see it's wordt he effords:cool: 
I hope you give it another try and if it come to work you can share your experience with other Intel users.

---

### Post by Rashid584 on 2006-06-12
Well, I know for sure my computer can handle XGL (and pretty well too at that) because I've already tried it with the [Kororaa Xgl LiveCD](http://kororaa.org/static.php?page=static060318-181203) and I had all the cool effects, and they worked fast too.

So I know its something to do with my setting up of xgl/compiz...but I've lost the impetus to do a re-install now :( lol

I've looked everywhere for a howto for intel 82845G chips on Kubuntu 6.06 but can't find ANYTHING.

-Rashid

---

### Post by nohope_no on 2006-06-15
[QUOTE=christhemonkey]Ironfistchamp:
Your glxinfo shows that you are missing the essential GLX_EXT_texture_from_pixmap.
This is the glx extension that compiz needs to function.
Currently nvidia do not have it in their drivers, so you need to use the mesa rendering, which does not utilise the full potential of the GPU.

But still, hopefully nvidia will release new drivers with GLX_EXT_texture_from_pixmap support![/QUOTE]
[QUOTE=poofyhairguy]Yeah, I get that sometimes. Just keep running the command till it goes away. Even if thats like twenty times. It will eventually go away.[/QUOTE]

How do you set xorg/Xgl to use mesa rendering, then? (While waiting for new nVidia-drivers)

---

### Post by cillian on 2006-06-17
I'm struggling with this too. Various posts seem to suggest variations of moving libGL.so.* files to various places and linking them or using LD_PRELOAD to load them for compiz and sometimes also gnome-window-decorator.

If you look at the installed files in the package properties for both nvidia-glx and libgl1-mesa in synaptic you'll see 
nvidia wants to install:
/usr/lib/libGL.so.1 (which links to)
/usr/lib/libGL.so.1.0.8762
and libgl1-mesa wants to install:
/usr/lib/libGL.so.1 (and link it to)
/usr/lib/libGL.so.1.2

so if you're supposed to install both nvidia-glx and libgl1-mesa the order you install them will determine what /usr/lib/libGL.so.1 points to

**WARNING**
moving library files and relinking them means that you may need to remove them by hand afterwards since apt-get will see they've been changed. You can tell what is supposed to be where by listing the installed files as mentioned above, so that's how you'll know what to delete if you want to start from fresh.

I linked /usr/lib/libGL.so.1 to /usr/lib/libGL.so.1.2
ln -sf /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1 
and rebooted (restarting x, rmmod-ding nvidia etc. was not enough)
and now when I start xgl and run glxinfo I get GLX_EXT_texture_from_pixmap listed in the extensions. No other method got me that far. But compiz still complains that it's missing :-({|= 

Other tricks I've seen are to install the mesa-libs first copy the libGL.so* ones to somewhere else, then install nvidia-glx and use something like
LD_PRELOAD=/opt/mesa/libGL.so.1.2 compiz --replace --replace
and another version suggests using what I believe are mesa libs provided by nvidia?:
LD_PRELOAD=/usr/lib/nvidia/libGL.so.1.2.xlibmesa compiz --replace --replace
if you take a look at /usr/bin/compiz though you'll see that it does this by default.

The other funny thing is that gnome-window-decorator crashes Xgl on me. Stone dead. I'm still trying to find someone who has the same issue. I've no clue how to resolve it. I hope you've better luck!

EDIT:
I now have it working, although the road was somewhat long and winding. I believe the trick with the libraries was to install the nvidia modules and then mesa libs but the real problem was that Xgl was never starting with the xgl.desktop entry method. I noticed I could run the startxgl.sh script as root from a virtual terminal and that got me into xgl where I could then also start compiz successfully. I then tried method B on the wiki i.e. adding the Xgl bits to gdm.conf-custom and this worked fine.
My adapter is a GeForce4 420 Go and I've a feeling it's still not set up correctly. Things ran very slowly when I changed NvAGP to 1 to get hibernate to work (it did, after stopping compiz). Changing it to 3 made a big difference in performance, although things do tend to slow down considerably after 4 hours or so and I get high processor usage when I'm moving windows or rotating etc. (50-90%) And Xgl is using about 130Mb of Ram. I don't think this is normal although it does run very smoothly with a lot of apps running for a few hours.
for reference ls -l /usr/lib/libGL.* looks like:
lrwxrwxrwx 1 root root     10 2006-06-25 16:20 /usr/lib/libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root     17 2006-06-17 14:24 /usr/lib/libGL.so.1 -> libGL.so.1.0.8762
-rw-r--r-- 1 root root 540136 2006-06-15 12:07 /usr/lib/libGL.so.1.0.8762
and compiz preloads /usr/lib/nvidia/libGL.so.1.2.xlibmesa.
I didn't really have to do any fiddling with the libraries after all. 
With method A in the Wiki (adding the xgl.desktop file to provide and extra option in gdm) it seems that if gdm fails to load Xgl it reverts to X after a couple of attempts. I never noticed that and got confused by what it meant to be running Xgl on top of X. Xgl should be listed as a running process.

---

### Post by nythrix on 2006-06-17
I had a similiar problem with compiz. It run fine till I tried to switch windows using Alt+Tab. Then the borders dissapeared and the effects were gone. I had to disable the dock function (useless anyway) and now everything works fine.

Running on 32 bit, GPU is a G4 Ti4200, driver nvidia, I didn't mess around with mesa or such I Just followed this guide:
[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_(or_KDM](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_(or_KDM))

Hope it helps.

---

### Post by Melvil on 2006-06-17
I just installed Xgl+Compiz from scratch using the quinn repos, so I'm running compiz 0.0.13 and the latest xserver-xgl

Xgl starts fine, but as soon as I launch compiz via "compiz --replace gconf" Xgl crashes and I'm thrown back to the GDM login.

Anyone else experienced this and knows how I can fix this? My video driver is fglrx 8.25.18

---

### Post by sog on 2006-08-01
i've got the same problem as most of the other folks here: xGL works fine, Compiz appears to work fine, but runs without gnome-window-decorator. 

i followed first the xGL and then the Compiz tutorials and have been unable to get beyond [this one]("https://help.ubuntu.com/community/CompositeManager/InstallingCompiz") because of this problem. 

hardware is not NVidia, but Intel i810 (Thinkpad x60s). i had a similar problem on Gentoo and fixed it by recompiling everything, but i cannot take the advice earlier in the thread and reinstall Ubuntu. 

any thoughts or advice on why Compiz isn't recognizing gnome-window-decorator would be much appreciated.

---

