---
title: "beryl segmentation fault"
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by Eezyville on 2007-09-09
Ok so when I load up beryl it crashes on me and says it has a segmentation fault. How do I fix this? 
[PHP]**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
Segmentation fault (core dumped)[/PHP]

If I can't fix this then how do I make an error report?

---

### Post by armorm2 on 2007-09-10
I'm getting a similar error:

ok....I've gone through the usual 20 hours of searching for an answer to my problem with no luck. I'm trying to install Beryl 0.3.0. A simpler description of the problem -

1) i run 'beryl' in terminal.....screen flashes and gives me the error directly below in terminal. Also all of the window title bars (minimize, max...buttons) stop showing.

2) i run beryl-manager.........screen flashes me to the login screen.

For both of the above, it is not the 'white screen of death' error.

More specifically, i get a segmentation fault ERROR when i try to run it:
************************************************** ************
* Beryl system compatibility check *
************************************************** ************

Detected xserver : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension : passed (v0.2)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : passed
Checking for non power of two texture support : passed
Checking maximum texture size : passed (4096x4096)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

************************************************** ************
* Beryl system compatibility check *
************************************************** ************

Detected xserver : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension : passed (v0.2)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : passed
Checking for non power of two texture support : passed
Checking maximum texture size : passed (4096x4096)

Segmentation fault

The first time i installed it, i got the little diamond/emerald/whatever to show. I was even able to choose between the window managers (metacity, kwin, and beryl) when i right clicked on it. The problems began when i did 'CTRL ALT BCKSPCE' after installing and choosing between wind. managers. When i logged in again beryl would give me the above error and my kxdocker began having this stupid black frame error (which ironically is supposed to be fixed by installing a compositon manager).

So I got the latest NVIDIA driver for my video card. Next i re-installed beryl (and its dependencies) successfully according to synaptic packet manager. Here's a little info. about my system:

-Ubuntu Dapper 6.06 w/ kernel 2.6.15-29-686 and KDE version 5:45
-NVIDIA Geforce FX5500 w/ driver 100.14.11 installed from NVIDIA's site
-This is what my xorg.conf looks like:

************************************************** *******************
....blah blu bla

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

...bla blu blah bla
..........

Section "Monitor"
Identifier "DELL E173FP"
Option "DPMS"
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV34 [GeForce FX 5500]"
Driver "nvidia"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV34 [GeForce FX 5500]"
Monitor "DELL E173FP"
DefaultDepth 24
Option "NoLogo" "true"
Option "AllowGLXWithComposite" "true"
Option "RenderAccel" "true"
Option "XaaNoOffscreenPixmaps" "true"
Option "AddARGBGLXVisuals" "true"
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "Extensions"
Option "Composite" "Enable"
Option "RENDER" "Enable"
EndSection
************************************************** ******************

as you can see i've been adding a bunch of extra options i found online to try and make beryl work. Some of those options were under the 'Device' section, but got moved under the 'Screen' section by the NVIDIA driver installer after i installed the latest driver. Here's what running 'glxinfo'gives:

************************************************** ******************
name of display: :0.0
display: :0 screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap,
GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer,
GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/AGP/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.11
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
GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit,
GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object,
GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays,
GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side,
GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_sRGB,
GL_EXT_timer_query, GL_EXT_vertex_array, GL_IBM_rasterpos_clip,
GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence,
GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program,
GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage,
GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_filter_hint,
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

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
0x21 24 tc 0 32 0 r y . 8 8 8 0 4 24 8 16 16 16 16 0 0 None
0x22 24 dc 0 32 0 r y . 8 8 8 0 4 24 8 16 16 16 16 0 0 None
0x24 24 tc 0 32 0 r y . 8 8 8 8 4 24 8 16 16 16 16 0 0 None
0x25 24 tc 0 32 0 r . . 8 8 8 0 4 24 8 16 16 16 16 0 0 None
0x26 24 tc 0 32 0 r . . 8 8 8 8 4 24 8 16 16 16 16 0 0 None
0x27 24 tc 0 32 0 r y . 8 8 8 0 4 24 0 16 16 16 16 0 0 None
0x28 24 tc 0 32 0 r y . 8 8 8 8 4 24 0 16 16 16 16 0 0 None
0x29 24 tc 0 32 0 r . . 8 8 8 0 4 24 0 16 16 16 16 0 0 None
0x2a 24 tc 0 32 0 r . . 8 8 8 8 4 24 0 16 16 16 16 0 0 None
0x2b 24 tc 0 32 0 r y . 8 8 8 0 4 16 0 16 16 16 16 0 0 None
0x2c 24 tc 0 32 0 r y . 8 8 8 8 4 16 0 16 16 16 16 0 0 None
0x2d 24 tc 0 32 0 r . . 8 8 8 0 4 16 0 16 16 16 16 0 0 None
0x2e 24 tc 0 32 0 r . . 8 8 8 8 4 16 0 16 16 16 16 0 0 None
0x2f 24 tc 0 32 0 r y . 8 8 8 0 4 0 0 16 16 16 16 0 0 None
0x30 24 tc 0 32 0 r y . 8 8 8 8 4 0 0 16 16 16 16 0 0 None
0x31 24 tc 0 32 0 r . . 8 8 8 0 4 0 0 16 16 16 16 0 0 None
0x32 24 tc 0 32 0 r . . 8 8 8 8 4 0 0 16 16 16 16 0 0 None
0x33 24 tc 0 32 0 r y . 8 8 8 0 4 24 0 16 16 16 16 0 0 Ncon
0x34 24 tc 0 32 0 r y . 8 8 8 8 4 24 0 16 16 16 16 0 0 Ncon
0x35 24 tc 0 32 0 r y . 8 8 8 0 4 24 0 16 16 16 16 0 0 Ncon
0x36 24 tc 0 32 0 r y . 8 8 8 8 4 24 0 16 16 16 16 0 0 Ncon
0x37 24 tc 0 32 0 r . . 8 8 8 0 4 24 0 16 16 16 16 0 0 Ncon
0x38 24 tc 0 32 0 r . . 8 8 8 8 4 24 0 16 16 16 16 0 0 Ncon
0x39 24 tc 0 32 0 r . . 8 8 8 0 4 24 0 16 16 16 16 0 0 Ncon
0x3a 24 tc 0 32 0 r . . 8 8 8 8 4 24 0 16 16 16 16 0 0 Ncon
0x3b 24 tc 0 32 0 r y . 8 8 8 0 4 24 8 16 16 16 16 0 0 Ncon
0x3c 24 tc 0 32 0 r y . 8 8 8 8 4 24 8 16 16 16 16 0 0 Ncon
0x3d 24 tc 0 32 0 r y . 8 8 8 0 4 24 8 16 16 16 16 0 0 Ncon
0x3e 24 tc 0 32 0 r y . 8 8 8 8 4 24 8 16 16 16 16 0 0 Ncon
0x3f 24 tc 0 32 0 r . . 8 8 8 0 4 24 8 16 16 16 16 0 0 Ncon
0x40 24 tc 0 32 0 r . . 8 8 8 8 4 24 8 16 16 16 16 0 0 Ncon
0x41 24 tc 0 32 0 r . . 8 8 8 0 4 24 8 16 16 16 16 0 0 Ncon
0x42 24 tc 0 32 0 r . . 8 8 8 8 4 24 8 16 16 16 16 0 0 Ncon
0x43 24 tc 0 32 0 r y . 8 8 8 0 4 16 0 16 16 16 16 0 0 Ncon
0x44 24 tc 0 32 0 r y . 8 8 8 8 4 16 0 16 16 16 16 0 0 Ncon
0x45 24 tc 0 32 0 r y . 8 8 8 0 4 16 0 16 16 16 16 0 0 Ncon
0x46 24 tc 0 32 0 r y . 8 8 8 8 4 16 0 16 16 16 16 0 0 Ncon
0x47 24 tc 0 32 0 r . . 8 8 8 0 4 16 0 16 16 16 16 0 0 Ncon
0x48 24 tc 0 32 0 r . . 8 8 8 8 4 16 0 16 16 16 16 0 0 Ncon
0x49 24 tc 0 32 0 r . . 8 8 8 0 4 16 0 16 16 16 16 0 0 Ncon
0x4a 24 tc 0 32 0 r . . 8 8 8 8 4 16 0 16 16 16 16 0 0 Ncon
0x4b 24 dc 0 32 0 r y . 8 8 8 8 4 24 8 16 16 16 16 0 0 None
0x4c 24 dc 0 32 0 r . . 8 8 8 0 4 24 8 16 16 16 16 0 0 None
0x4d 24 dc 0 32 0 r . . 8 8 8 8 4 24 8 16 16 16 16 0 0 None
0x4e 24 dc 0 32 0 r y . 8 8 8 0 4 24 0 16 16 16 16 0 0 None
0x4f 24 dc 0 32 0 r y . 8 8 8 8 4 24 0 16 16 16 16 0 0 None
0x50 24 dc 0 32 0 r . . 8 8 8 0 4 24 0 16 16 16 16 0 0 None
0x51 24 dc 0 32 0 r . . 8 8 8 8 4 24 0 16 16 16 16 0 0 None
0x52 24 dc 0 32 0 r y . 8 8 8 0 4 16 0 16 16 16 16 0 0 None
0x53 24 dc 0 32 0 r y . 8 8 8 8 4 16 0 16 16 16 16 0 0 None
0x54 24 dc 0 32 0 r . . 8 8 8 0 4 16 0 16 16 16 16 0 0 None
0x55 24 dc 0 32 0 r . . 8 8 8 8 4 16 0 16 16 16 16 0 0 None
0x56 24 dc 0 32 0 r y . 8 8 8 0 4 0 0 16 16 16 16 0 0 None
0x57 24 dc 0 32 0 r y . 8 8 8 8 4 0 0 16 16 16 16 0 0 None
0x58 24 dc 0 32 0 r . . 8 8 8 0 4 0 0 16 16 16 16 0 0 None
0x59 24 dc 0 32 0 r . . 8 8 8 8 4 0 0 16 16 16 16 0 0 None
0x5a 24 dc 0 32 0 r y . 8 8 8 0 4 24 0 16 16 16 16 0 0 Ncon
0x5b 24 dc 0 32 0 r y . 8 8 8 8 4 24 0 16 16 16 16 0 0 Ncon
0x5c 24 dc 0 32 0 r y . 8 8 8 0 4 24 0 16 16 16 16 0 0 Ncon
0x5d 24 dc 0 32 0 r y . 8 8 8 8 4 24 0 16 16 16 16 0 0 Ncon
0x5e 24 dc 0 32 0 r . . 8 8 8 0 4 24 0 16 16 16 16 0 0 Ncon
0x5f 24 dc 0 32 0 r . . 8 8 8 8 4 24 0 16 16 16 16 0 0 Ncon
0x60 24 dc 0 32 0 r . . 8 8 8 0 4 24 0 16 16 16 16 0 0 Ncon
0x61 24 dc 0 32 0 r . . 8 8 8 8 4 24 0 16 16 16 16 0 0 Ncon
0x62 24 dc 0 32 0 r y . 8 8 8 0 4 24 8 16 16 16 16 0 0 Ncon
0x63 24 dc 0 32 0 r y . 8 8 8 8 4 24 8 16 16 16 16 0 0 Ncon
0x64 24 dc 0 32 0 r y . 8 8 8 0 4 24 8 16 16 16 16 0 0 Ncon
blah blah bla
.....
************************************************** ********************

at this point i have no idea what is going wrong. If anyone could help, i would really apreciate it. I can post any other info about the problem as well....thank you in advance.

---

### Post by Eezyville on 2007-09-10
A friend of mine at work said that he encountered a similar problem and was looking around for an answer. He said he found a forum where people had the same problem as me an him and they (the forum members) said that it was due to Envy and the kernel. The problem showed up when the kernel automatically updated last night for me. He told me that when the kernel updated then Envy encountered some problems and thats why I cannot run Beryl properly. 


   Well I tried to uninstall the drivers through Envy and then tried reinstalling them with Restricted Drivers manager but they didn't install correctly and I was somewhat forced to reinstall through Envy since I know how to launch Envy by command line. I figured I could wait until the developers update Envy because I don't need the eyecandy now.

---

### Post by armorm2 on 2007-09-21
I managed to get it to work...........

turns out that xgl was not running or properly installed or something of that sort. Sorry for being so vague, but i myself am not sure what the exact problem is/was, i just know that i messed around with xgl for a bit, then re-installed beryl and what do ya know,,,it works. Marvelous.

---

