---
title: "Checking for texture_from_pixmap: not present"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by MourningWood on 2007-10-22
I've been try to get compiz running for sometime now with no luck.  I have an NVIDIA 8600GT and did the upgrade from feisty to gutsy using update manager.  I've tried remove and reinstalling compiz along with my NVIDIA driver and emerald.  There error its giving me is

```
mourningwood@mourningwood-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

The Xgl doesn't matter because of NVIDIA but the texture_from_pixmap is whats killing it.  I also have an old laptop too slow to run compiz but does say that the piximap is present from a clean install.

I'm not sure what it is referring to but is there a way to install it without doing a clean install?

---

### Post by FuturePilot on 2007-10-22
What is the output of 
```
glxinfo
```

---

### Post by MourningWood on 2007-10-22
Thanks for the quick reply

```
mourningwood@mourningwood-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: Brian Paul
server glx version string: 1.4 Mesa 7.0.1
server glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
client glx vendor string: Brian Paul
client glx version string: 1.4 Mesa 7.0.1
client glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
GLX version: 1.4
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_program_debug, GL_MESA_resize_buffers, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x22 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x28 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2b 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2c 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2d 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2e 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2f 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x30 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x31 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x32 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x33 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x34 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x35 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x36 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x37 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x38 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x39 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3b 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3c 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3d 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3e 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x40 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x41 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x42 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x43 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x44 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x45 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x46 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x47 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x48 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x49 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4a 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4b 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4c 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4d 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x50 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x51 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x52 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x53 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x54 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x55 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x56 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x57 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x58 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x59 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x5a 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5b 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5d 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5e 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5f 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x60 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x61 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x63 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x64 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x65 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x66 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x67 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x68 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x69 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6a 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6b 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6c 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6d 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6e 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6f 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x70 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x71 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None

```

I just tried to remove and reinstall the NVIDIA Driver using the Restricted Driver Manager and again with Envy with no luck.

---

### Post by MourningWood on 2007-10-23
I thought I would go ahead and past my xorg.conf

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Samsung"
    ModelName      "Samsung SyncMaster 225BW (Digital)"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@75" 107.2 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
    ModeLine       "1280x768@75" 103.0 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@75" 136.5 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    BoardName      "vesa"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1920 1200
        Depth       24
        Modes      "1680x1050@60" "1920x1200@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Thats the auto generated one from Envy.  I had it cleaned up and looking good before but it still didn't help anything.

```
Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	28.0	-	84.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"nVidia Corporation [GeForce 8600 GT]"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation [GeForce 8600 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	16
		Modes		"1680x1680"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by FuturePilot on 2007-10-23
Did you reboot after installing the driver? It's strange because a lot of your glxinfo is referring to MESA instead of Nvidia.

---

### Post by MourningWood on 2007-10-23
I've rebooted quite a few times and uninstalled and reinstalled my NVIDIA drivers quite a few times.  It is kind of weird that it not changed it to NVIDIA.  Is there a way to do it manually?

---

### Post by MourningWood on 2007-10-23
bump

---

### Post by FuturePilot on 2007-10-23
Which one is the xorg.conf that you are currently using? The first one is no good, as it's got almost everything as failsafe.
If you're using the first one try switching it with the second one, then logout  and login

---

### Post by MourningWood on 2007-10-23
I'll give it a try when I get home tonight.  I was actually using the second for a while then when I reinstalled my NVIDIA driver with the Restricted Drivers Module it created that screwy one.

---

### Post by MourningWood on 2007-10-23
I changed my xorg.conf but it still gives me the same error.

new xorg.conf
```
Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  	screen 		"Screen0" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
	RgbPath		"/usr/lib/X11/rgb"
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"extmod"
	Load		"type1"
	Load		"freetype"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	ModelName	"Samsung SyncMaster"
	Horizsync	30.0	-	81.0
	Vertrefresh	56.0	-	75.0
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	VendorName	"NVIDIA Corporatin"
	BoardName	"GeForce 8600 GT"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"metamodes" "nvidia-auto-select +0+0; 1680x1050_60 +0+0"
	Option		"RenderAccel" "True"
	Option		"AllowGLXWithComposite" "True"
	Option		"AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth	24
		Modes		"1680x1680"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```


glxinfo
```
mourningwood@mourningwood-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: Brian Paul
server glx version string: 1.4 Mesa 7.0.1
server glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
client glx vendor string: Brian Paul
client glx version string: 1.4 Mesa 7.0.1
client glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
GLX version: 1.4
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_program_debug, GL_MESA_resize_buffers, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x22 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x28 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2b 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2c 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2d 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2e 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2f 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x30 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x31 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x32 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x33 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x34 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x35 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x36 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x37 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x38 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x39 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3b 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3c 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3d 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3e 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x40 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x41 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x42 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x43 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x44 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x45 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x46 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x47 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x48 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x49 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4a 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4b 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4c 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4d 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x50 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x51 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x52 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x53 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x54 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x55 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x56 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x57 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x58 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x59 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x5a 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5b 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5d 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5e 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5f 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x60 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x61 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x63 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x64 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x65 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x66 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x67 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x68 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x69 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6a 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6b 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6c 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6d 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6e 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6f 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x70 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x71 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
mourningwood@mourningwood-desktop:~$ sudo gedit /etc/X11/xorg.conf

```

error running compiz from terminal
```
mourningwood@mourningwood-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```


Thank for helping me out FuturePilot, this one has had me completely baffled and frustrated.

---

### Post by FuturePilot on 2007-10-23
I think it's got me baffled too.:lolflag: I'm taking a wild guess here
Open the System Log (System>Administration>System Log) and select the kern.log on the left. Then do View>Filter and Filter for "NVRM"
You should see something like  NVRM: loading NVIDIA UNIX x86 Kernel Module  **100.14.19**  Wed Sep 12 14:12:24 PDT 2007
Make sure you only have one version being loaded. The version number is in bold

---

### Post by MourningWood on 2007-10-23
It has that exact line for each time I rebooted and two others talking about RmPowerManagment.  

I'm getting to the point of doing a clean install but I don't want to loose my settings and go through the headache of backing up all my stuff.

So the piximap error is basically from loading the wrong glx?

---

### Post by FuturePilot on 2007-10-23
I'm not sure. Something weird is going on there. Your xorg.conf looks fine. It's got to be something messed up with the way the driver installed. I know you said you installed and uninstalled the driver already, but did you try purging it? You can do that by opening Synaptic and marking nvidia-glx-new to be Completely Removed and then reinstall it.

---

### Post by MourningWood on 2007-10-23
Just the nvidia-glx-new?  And do I need to reboot in between?

---

### Post by FuturePilot on 2007-10-23
Yes, just that package. Don't reboot in between but after. So purge, install, reboot

---

### Post by MourningWood on 2007-10-23
done, and it still tells me the same thing in terminal

---

### Post by FuturePilot on 2007-10-23
This is bizarre. I'm kind of out of ideas. Anyone else have some?
The only other option I see is a fresh install. Sometimes the upgrades can cause some problems that require a reinstall.

---

### Post by MourningWood on 2007-10-23
I appreciate all the help that you have given.  I'm going to hang tight for a couple of days to see if any good suggestions come through and if not take a dive and do a clean install and hours of fun setting up everything back the way I had it.

If the clean install works which I'm sure it will I'll post it up here so anyone with the same problem knows.

---

### Post by FuturePilot on 2007-10-23
> **MourningWood said:**
> I appreciate all the help that you have given.  I'm going to hang tight for a couple of days to see if any good suggestions come through and if not take a dive and do a clean install and hours of fun setting up everything back the way I had it.

If the clean install works which I'm sure it will I'll post it up here so anyone with the same problem knows.

You're welcome. Yeah probably a good idea to see if anyone else knows anything. I hope you can get it working again, one way or another;)

---

### Post by MourningWood on 2007-10-25
Alright, I ended up doing a clean install and after installing my NVIDIA driver with the Synaptic Package Manager and a reboot Compiz loaded right up.  I'm also really impressed with it, runs a lot cleaner than Beryl.

Now time to set things up the way I like them again.

Hopefully someone finds an easier way to fix this problem.

---

### Post by lakefire on 2007-10-27
I am also having the same issues.  I would rather not have to reinstall the software.  I did an upgrade from 7.04.

Here is my glxinfo:

```
eric@master-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x6a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

and my xorg.conf (I am running dual monitors which works)

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"GLcore"
	load	"dbe"
	#Load	"int10"
	#Load	"vbe"
	#Load	"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option 		"ZAxisMapping" "4 5"
	Option 		"Emulate3Buttons" "true"
	Option 		"Buttons" "6"
	Option 		"ButtonMapping" "1 2 3 6"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV370 [Sapphire X550 Silent]"
	Driver		"radeon"
	BusID		"PCI:3:0:0"
	Option          "monitor-DVI-0" "Dell [1]"
        Option          "monitor-VGA-0" "CyberMax [2]"
        #Option          "AddARGBGLXVisuals" "true"
        #Option          "AGPFastWrite" "true"
        #Option          "AGPMode" "8"
        #Option          "TripleBuffer" "true"
        Option          "XAANoOffscreenPixmaps" "true"
        #Option          "DisableGLXRootClipping" "true"
        #Option 	 "DMAForXv" "true"
        #Option          "EnablePageFlip" "true"
        #Option          "AccelMethod" "XAA"
        #Option          "AccelDFS" "true"
        #Option          "DRI" "true" 
EndSection

Section "Monitor"
        Identifier      "Dell [1]"
        Option          "DPMS"
        Option 		"PreferredMode" "1280x1024"
EndSection

Section "Monitor"
        Identifier      "CyberMax [2]"
        Option          "DPMS"
	Option          "RightOf"  "Dell [1]"        
	Option 		"PreferredMode" "1280x1024"
EndSection 

Section "Screen"
         Identifier      "Default Screen"
         Device          "ATI Technologies Inc RV370 [Sapphire X550 Silent]"
         Monitor         "Dell [1]"
         DefaultDepth    24
         SubSection "Display"
         Modes           "1280x1024"
         Virtual         2560 1024
         EndSubSection
EndSection 

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"AIGLX"		"true"
EndSection

Section "DRI"
	Mode		0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection 
```

---

### Post by akiratheoni on 2007-10-28
So I have Ubuntu 7.10 Gutsy Gibbon and an Intel GMA 950 using the intel driver that came with 7.10. I'd rather avoid reinstalling as well.

The desktop effects have been working perfectly fine for me, until just a couple minutes ago and it just completely died out after I rebooted the computer.

When I run compiz --replace &, I get this error.

```
abong@zantherus-desktop:~$ compiz --replace &
[1] 6436
abong@zantherus-desktop:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

When I run the glxinfo, it says I have no direct rendering.

```
abong@zantherus-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: Brian Paul
server glx version string: 1.4 Mesa 7.0.1
server glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
client glx vendor string: Brian Paul
client glx version string: 1.4 Mesa 7.0.1
client glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
GLX version: 1.4
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_program_debug, GL_MESA_resize_buffers, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x28 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2b 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2c 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2d 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x30 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x31 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x32 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x68 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
```

Going to System > Preferences > Appearance > Visual Effects and selecting any of the options for desktop effects tells me that 'Desktop effects could not be enabled'.

It was just working earlier today!

---

### Post by Yfrwlf on 2007-11-05
This problem happened to me as well except it wasn't after an upgrade.  I did a fresh install of 7.10, and then switched back and forth a few times between the ati and fglrx drivers, and somehow that broke Compiz.  At first it said my driver wasn't in the whitelist, so I added it, and now it gives the texture_from_pixmap not present error.

All you'd have to do, since the problem most likely lies in an incorrect xorg.conf file that has been screwed up, is someone needs to save their xorg.conf and then do a reinstall and compare the two xorg.confs to find out the difference, then post the differences on this and other threads.  I may do that tonight. >.<  I just hate having to reboot Linux though...

---

### Post by pmmike on 2007-11-06
I just changed from an nvidia card to an ATI one and suddenly compiz is throwing up this exact same error.

---

### Post by Yfrwlf on 2007-11-08
> **pmmike said:**
> I just changed from an nvidia card to an ATI one and suddenly compiz is throwing up this exact same error.

Of course you installed the Nvidia restricted drivers I assume and Xorg.conf IS set to use it I assume?  If so then yeah, it sounds like the driver configure scripts need to be updated so that they make sure the proper needed Compiz lines are installed or remain in place.  Out of curiosity, you could perhaps try completely removing, and then installing Compiz to see if the configuration tweaks are being done by the Compiz packages instead? :/

I will post a functional Nvidia and Compiz functional Xorg.conf in a bit to see if you or any other interested parties can glean anything from it. :D

---

### Post by Yfrwlf on 2007-11-08
Alright, here's a functional nvidia + Compiz driver xorg.conf for Nvidia users.  ATI users to my knowledge should probably not try this at all since I think the Compiz tweaks for ATI are quite different.  If you modify your own xorg.conf to reflect this one, do not fully replace it and leave in your own configuration where necessary like your monitor settings and monitor and card identifications, etc.```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation GeForce 7100 GS"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation GeForce 7100 GS"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by Yfrwlf on 2007-11-09
I just finished reinstalling and it looks like it is an updated fglrx installation script that breaks compatibility with Compiz.  It WAS working, but the new driver breaks the system once installed, even from a fresh install.  I didn't do any system updates, only the fglrx installation, and it wouldn't work.  Then, I did all system updates which did update Compiz, and then rebooted just to be sure, and again it still didn't change anything so I'd blame the new fglrx installation scripts on this one.

Compiz works fine under the ati (which is open source for those who don't know) driver though, so in case anyone is having difficulty using Compiz under the ati driver, here is my working one.  Of course, if you want to play any 3D games then you'll need to switch over to the fglrx closed source driver, which is annoying to have to do.  Blame ATI for not releasing hardware specs. ^^  Though I do wish someone would have tested the latest fglrx a bit more before submitting it as an update, but mistakes happen...```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL1711"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"Acer AL1711"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```Again, remember to not copy this verbatim as the modes and identifiers will be different on your own systems.

---

### Post by 3doff on 2008-04-15
Reinstall graphical driver. It will solve this problem.

---

