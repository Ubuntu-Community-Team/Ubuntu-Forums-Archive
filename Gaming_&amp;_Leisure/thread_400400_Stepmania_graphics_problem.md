---
title: "Stepmania graphics problem"
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by _sluimers_ on 2007-04-03
When I run stepmania the resolution is 640x480 fullscreen on a 1024x768 screen.
My desktop can't change it's resolution.
I have an  Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller.
This is my log:

```

StepMania 3.9
Log starting 2007-04-03 19:15:57
Loading window: gtk
OS: Linux ver 020617
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.4
Threads library: NPTL 2.4
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).
ALSA Driver: 0: Intel ICH6 [ICH6], device 0: Intel ICH [Intel ICH6], 1/1 subdevices avail
ALSA Driver: 0: Intel ICH6 [ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958], 1/1 subdevices avail
Couldn't load driver ALSA: Not enough substreams for hardware mixing, using software mixing
ALSA: Software mixing at 48000hz
Sound driver: ALSA-sw
/////////////////////////////////////////
WARNING: Couldn't find any SM, DWI, BMS, or KSF files in 'Songs/Jeugdsentiment/Kazoku Robinson Hyouryuuki/'.  This is not a valid song directory.
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Couldn't find any SM, DWI, BMS, or KSF files in 'Songs/Jeugdsentiment/Maja de Bij/'.  This is not a valid song directory.
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Couldn't find any SM, DWI, BMS, or KSF files in 'Songs/Jeugdsentiment/Nils no fushigi na tabi/'.  This is not a valid song directory.
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Couldn't find any SM, DWI, BMS, or KSF files in 'Songs/Jeugdsentiment/not good enough for ddr/'.  This is not a valid song directory.
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Couldn't find any SM, DWI, BMS, or KSF files in 'Songs/Jeugdsentiment/Sinbaddo no Boken/'.  This is not a valid song directory.
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Invalid #BGCHANGES value " Better" was ignored
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Invalid #BGCHANGES value " Faster" was ignored
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Invalid #BGCHANGES value " Stronger-bg.png=1.000=0=0=1" was ignored
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Couldn't find any SM, DWI, BMS, or KSF files in 'Songs/MISC 3/6490ateens__mamamia/'.  This is not a valid song directory.
/////////////////////////////////////////

(stepmania:25392): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
Video renderers: 'opengl'
libGL warning: 3D driver claims to not support visual 0x5b
SDL version: 1.2.10
Got 32 bpp (8888), 24 depth, 8 stencil
Paletted textures disabled: GL_EXT_paletted_texture missing.
OGL Vendor: Tungsten Graphics, Inc
OGL Renderer: Mesa DRI Intel(R) 915GM 20050225
OGL Version: 1.3 Mesa 6.5.1
OGL Extensions: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays
OGL Max texture size: 2048
GLU Version: 1.3
Display: :0.0 (screen 0)
Direct rendering: yes
X server vendor: The X.Org Foundation [7.1.1.0]
libGL warning: 3D driver claims to not support visual 0x5b
Server GLX vendor: SGI [1.2]
Client GLX vendor: SGI [1.4]
Fullscreen 640x480 16 color 16 texture 0Hz Vsync AA
Found 0 joysticks
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_japanese 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_korean 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_japanese 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_korean 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_japanese 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_korean 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_japanese 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_korean 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_japanese 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_korean 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_japanese 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_korean 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_japanese 16px.ini has no characters
/////////////////////////////////////////
/////////////////////////////////////////
WARNING: Font Themes/default/Fonts/_korean 16px.ini has no characters
/////////////////////////////////////////
ptrace failed: Operation not permitted
ptrace failed: Operation not permitted
ptrace failed: Operation not permitted

StepMania has crashed.  Debug information has been output to

    /tmp/crashinfo.txt

Please report a bug at:

    http://sourceforge.net/tracker/?func=add&group_id=37892&atid=421366

Fatal signal (Segmentation fault) while still in the crash handler

```

---

