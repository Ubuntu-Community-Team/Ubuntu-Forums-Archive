---
title: "Beryl / XGL / KDE / Kwin / KDM / ATI / Edgy"
date: 2007-02-07
forum: Desktop Environments
---

### Post by Kure on 2007-02-07
Hello,

I have a problem with installing Beryl+XGL on my KDE desktop with ATI Radeon 9600 XT.

When I try to run Xgl via normal login from kdm, desktop gets loaded, but it is incredibly slow (e.g. it takes a minute to draw K Menu). I was able to get this log by running the XGL start script from text mode:

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux hal9000 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.94.log", Time: Wed Feb  7 12:06:52 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "B90A"
(**) |   |-->Device "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) xf86ReadBIOS: Failed to open /dev/mem (Permission denied)
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0

Fatal server error:
xf86OpenConsole: Cannot open /dev/tty0 (No such file or directory)

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor


```

Some info about my system:

```

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

My kde&kwin&kdm are version 3.5.6, my Xorg is 7.1.1. I followed guide from, [Beryl project wiki](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL).

I have the starting script in /usr/bin/startxgl.sh, with this code (possibly customized for ATI cards):
```

#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
export DISPLAY=:1
exec startkde

```

I have Composite=disable in my Xorg.conf, for obvious reasons as it would make my drivers defunct.

The problem may be caused, in my opinion, by 
[LIST]
[*] quite uncommon combination (maybe impossible) of KDE, Kwin and kdm (instead of gdm and metacity)
[*] ATI drivers
[*] some kind of misconfiguration
[*] Composite=disabled in my Xorg.conf (but then I won't have direct rendering = no XGL at all)
[*] Something completely different ??
[/LIST]

Any suggestions?

---

### Post by Kure on 2007-02-08
No ideas?

---

### Post by shareMenaPeace on 2007-02-08
Hi the log really looks bad but i cant tell you what you need todo to fix this.

Try a search on the errors
eg check those lines with begin with WW or EE and hook up parts of it in this forum search or on google.


```
(WW) xf86ReadBIOS: Failed to open /dev/mem (Permission denied)
Fatal server error:
xf86OpenConsole: Cannot open /dev/tty0 (No such file or directory)
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
```

If you dont get an answer here start a new topic maybe, as most come here for beryl and your prob looks more like xserver or permission isssues.

---

### Post by shareMenaPeace on 2007-02-08
And looks like you followed a ubuntu guide but i guess you have kubuntu?
In this case dont use edgy guides take drapper or whatever release you installed.

---

### Post by Kure on 2007-02-08
> **shareMenaPeace said:**
> And looks like you followed a ubuntu guide but i guess you have kubuntu?
In this case dont use edgy guides take drapper or whatever release you installed.

I have Egdy, and it was installed from Ubuntu CD (a a long time ago, I am not sure if the original version was Breezy or Dapper). There doesn't seem to be Kubuntu guide, but the Ubuntu one seems to be relatively "logical", e.g. there is nothing too specific.

The problem is quite nonstandard configuration that I try - there are many guides for Beryl, Gnome, XGL and fglrx, many for Gnome, AIXGL, Beryl and open source drivers, but none form a combination of these two. The other problem is Beryl, it is almost like Cedega - no real debug output in the console.

I will try to downgrade my fglrx drivers and see if something changes. Anyway, thank you for suggestions.

---

### Post by shareMenaPeace on 2007-02-08
What is the output of ```
glxinfo
``` ?

---

### Post by g8m on 2007-02-09
The opensource drivers for ATI claim to have better support for beryl.

As far as I know, the combination aixgl/beryl works better than the xgl/beryl.

---

### Post by Kure on 2007-02-11
Open source driver may work better with AIGLX, and AIGLX may work better with Beryl, but the open source driver doesn't offer almost any hardware acceleration (e.g. video playback with fglrx - 5% CPU usage, with open source driver 40-50% in Xine), and fglrx doesn't work with AIGLX (right now, and the future is uncertain).

Here is my glxinfo:

**glxinfo**
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6286 (8.33.6)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend,
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_element_array,
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer,
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3,
    GL_ATI_texture_float, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None

```

I also tried running XGL from normal running X session, it didn't say anything "usefull":
```

_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/hal9000:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

```

It seems to be running, but, IMHO, it lacks window manager - it acts almost as a plain standard X session.

Afterwards I tried to run Beryl, and the output was even more confusing:
```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```
I don't even have AIGLX installed, I have only 'xserver-xgl'.

---

### Post by g8m on 2007-02-11
hmm, I have beryl running with the opensource drivers on an X700, and I have noticed the system load sometimes going to 100%. X is causing it. Always blaimed it on beryl, maybe I should try the fglrx drivers again, but if memory serves me right, i couldn;t get it running. And running games under wine/cedega was very slow too, compared to the nvidia drivers.

---

### Post by shareMenaPeace on 2007-02-11
> **Kure said:**
> Open source driver may work better with AIGLX, and AIGLX may work better with Beryl, but the open source driver doesn't offer almost any hardware acceleration (e.g. video playback with fglrx - 5% CPU usage, with open source driver 40-50% in Xine), and fglrx doesn't work with AIGLX (right now, and the future is uncertain).

Here is my glxinfo:

**glxinfo**
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6286 (8.33.6)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend,
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_element_array,
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer,
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3,
    GL_ATI_texture_float, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None

```

I also tried running XGL from normal running X session, it didn't say anything "usefull":
```

_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/hal9000:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

```

It seems to be running, but, IMHO, it lacks window manager - it acts almost as a plain standard X session.

Afterwards I tried to run Beryl, and the output was even more confusing:
```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```
I don't even have AIGLX installed, I have only 'xserver-xgl'.
Search No composite extension and try disabling it in xorg.conf.

---

### Post by Kure on 2007-02-11
I have already composite extension disabled in xorg.conf, but something interesting happened.

I changed timeout in kdmrc (the time for which kdm waits for the x server to start) and suddenly I was able to start Xgl sessions. Unfortunately, more weird things are coming.

in Xgl:
fglrxinfo
```

**display: :0.0  screen: 0**
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

glxinfo
```

**name of display: :1.0**
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
**direct rendering: No**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.2 (2.0.6286 (8.33.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon


```

and finally ps -A
```

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  127 ?        00:00:00 kseriod
  160 ?        00:00:00 pdflush
  161 ?        00:00:00 pdflush
  162 ?        00:00:00 kswapd0
  163 ?        00:00:00 aio/0
 1732 ?        00:00:00 ata/0
 1866 ?        00:00:00 khubd
 2020 ?        00:00:00 scsi_eh_0
 2021 ?        00:00:00 usb-storage
 2127 ?        00:00:00 kjournald
 2227 ?        00:00:00 logd
 2429 ?        00:00:00 udevd
 3143 ?        00:00:00 shpchpd
 3281 ?        00:00:00 kpsmoused
 3306 ?        00:00:00 kgameportd
 3733 ?        00:00:00 kjournald
 4039 tty1     00:00:00 getty
 4040 tty2     00:00:00 getty
 4041 tty3     00:00:00 getty
 4042 tty4     00:00:00 getty
 4043 tty5     00:00:00 getty
 4044 tty6     00:00:00 getty
 4252 ?        00:00:00 acpid
 4273 ?        00:00:00 syslogd
 4306 ?        00:00:00 dd
 4308 ?        00:00:00 klogd
 4368 ?        00:00:00 kdm
 4408 ?        00:00:00 cupsd
 4475 ?        00:00:00 atieventsd
 4499 ?        00:00:00 dbus-daemon
 4520 ?        00:00:02 hald
 4521 ?        00:00:00 hald-runner
 4527 ?        00:00:00 hald-addon-acpi
 4533 ?        00:00:00 hald-addon-keyb
 4536 ?        00:00:00 hald-addon-keyb
 4565 ?        00:00:00 hald-addon-stor
 4568 ?        00:00:00 hald-addon-stor
 4570 ?        00:00:00 hald-addon-stor
 4600 ?        00:00:00 perl
 4608 ?        00:00:00 dictd
 4770 ?        00:00:00 ivman
 4802 ?        00:00:01 snort
 4856 ?        00:00:00 xinetd
 4885 ?        00:00:00 cron
 6557 ?        00:00:00 artsd
** 6578 tty9     00:00:05 Xorg**
 6581 ?        00:00:00 kdm
 6594 ?        00:00:00 startkde
 6659 ?        00:00:00 ssh-agent
 6660 ?        00:00:00 ssh-agent
 6663 ?        00:00:00 dbus-daemon
 6664 ?        00:00:00 dbus-launch
** 6665 ?        00:00:36 Xgl**
 6719 ?        00:00:00 start_kdeinit
 6720 ?        00:00:00 kdeinit
 6723 ?        00:00:00 dcopserver
 6726 ?        00:00:00 klauncher
 6728 ?        00:00:01 kded
 6734 ?        00:00:00 kwrapper
 6736 ?        00:00:00 ksmserver
 6737 ?        00:00:00 kwin
 6739 ?        00:00:01 kdesktop
 6741 ?        00:00:01 kicker
 6743 ?        00:00:00 kio_file
 6744 ?        00:00:00 kio_file
 6745 ?        00:00:00 kio_file
 6746 ?        00:00:00 kio_file
 6747 ?        00:00:00 kio_file
 6751 ?        00:00:00 kxkb
 6756 ?        00:00:00 artsd
 6758 ?        00:00:00 kaccess
 6761 ?        00:00:01 kgpg
 6776 ?        00:00:00 kio_thumbnail
 6779 ?        00:00:04 firefox-bin
 6781 ?        00:00:01 xchat
 6783 ?        00:00:01 sim
 6813 ?        00:00:00 knotify
 6821 ?        00:00:01 konsole
 6855 ?        00:00:00 gconfd-2
 6864 pts/1    00:00:00 bash
 6884 pts/1    00:00:00 ps

```
Again, quite strange... Why should Xorg run before Xgl? 

----
In normal X session glxinfo is the same as the one in my previous post. I guess there is some mess with screens or something.

---

### Post by shareMenaPeace on 2007-02-11
YOu followed a ubuntu guide check out this guide

[http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html](http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html)

Maybe uninstall beryl - see my suignature for link.

---

### Post by Kure on 2007-02-15
> **shareMenaPeace said:**
> YOu followed a ubuntu guide check out this guide

[http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html](http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html)

Maybe uninstall beryl - see my suignature for link.

I checked the guide, tried... Unfortunately, nothing (still strange errors, XGL doesn't run). I guess I will just wait until ATI properly supports AIXGL (I _could_ buy a low-end nVidia card, but even the slowest GeForce 6200 has an enormous power consumption compared to my current Radeon 9600XT).

---

### Post by LepeKaname on 2007-02-20
Hello, did you solve your problem?

I think I have the same problem... I have ATI Radeon XPRESS 200 with Kubuntu (AMD64) Edgy.

I'm almost sure is something related to permits. 

From the login screen select "console" and then run "sudo startxgl.sh" (just as a test) and you will be able to run XGL at full speed as root user (that is the bad news). 

So, I don't know exactly why, but this is a hint...

I hope this can help you (and help me) to solve the problem.

---

### Post by Kure on 2007-02-21
> **LepeKaname said:**
> Hello, did you solve your problem?

I think I have the same problem... I have ATI Radeon XPRESS 200 with Kubuntu (AMD64) Edgy.

I'm almost sure is something related to permits. 

From the login screen select "console" and then run "sudo startxgl.sh" (just as a test) and you will be able to run XGL at full speed as root user (that is the bad news). 

So, I don't know exactly why, but this is a hint...

I hope this can help you (and help me) to solve the problem.


It is not a problem of permissions. I recently found a bug in Beryl which may be causing this problem - I posted it here, but it was maybe deleted.

Anyway, I think I will never ever buy ATI/AMD in my whole life, and maybe we could start a protest - imagine if every Linux user with ATI graphic card or AMD CPU / motherboard sent an email with protest against their lack of interest in open source drivers. It would cost so much money for the servers and support people that they will pay attention.

---

### Post by johndavid400 on 2007-02-26
I too, have the same problem (exactly the same) with my Radeon 9600xt. I currently run Kubuntu and Ubuntu in Edgy and have even tried the most recent testing Feisty release for both k/ubuntu. I tried a while back to get it working in Kde, but nothing loaded... so I recently switched and tried installing xgl/beryl from ubuntu and get slightly better results. but still when I log into the XGL session, I can spin the desktop cube, but when I open any window it goes straight down to the taskbar, shows me a preview of the window, but won't let me open it up to view... and everything runs extremely slow.

I also get all the same results that KURE got when running tests to verify... i'm too am about to buy a low end nvidia card (newegg.com has some for around $30-$40) b/c the nvidia installs with beryl seem to be more successful.

I am about to try uninstalling fglrx to see if the open source driver works.

---

### Post by Kure on 2007-02-26
> **johndavid400 said:**
> I too, have the same problem (exactly the same) with my Radeon 9600xt. I currently run Kubuntu and Ubuntu in Edgy and have even tried the most recent testing Feisty release for both k/ubuntu. I tried a while back to get it working in Kde, but nothing loaded... so I recently switched and tried installing xgl/beryl from ubuntu and get slightly better results. but still when I log into the XGL session, I can spin the desktop cube, but when I open any window it goes straight down to the taskbar, shows me a preview of the window, but won't let me open it up to view... and everything runs extremely slow.

I also get all the same results that KURE got when running tests to verify... i'm too am about to buy a low end nvidia card (newegg.com has some for around $30-$40) b/c the nvidia installs with beryl seem to be more successful.

I am about to try uninstalling fglrx to see if the open source driver works.

I tried Beryl daily snapshots from svn, still no improvement.

Anyway, don't forget to write angry email to ATI, and I wouldn't buy nVidia card if I were in your place - 9600XT consumes about 20 Watts, lowest nVidia cards (e.g. 6200) eat up to 100 Watts with no performance improvement. I'm thinking about buying motherboard with integrated chip from Intel - but I'm not sure about the performance drop.

---

