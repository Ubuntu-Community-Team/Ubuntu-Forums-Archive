---
title: "Beryl on Ubuntu Edgy Eft"
date: 2007-03-07
forum: Desktop Environments
---

### Post by vertigo- on 2007-03-07
Hello,
Earlier today i decided i would get an ubuntu system with beryl up and running, but i quickly ran into trouble.
Basicly, the problem is this: Beryl-manager runs just fine, but when running beryl when choosing window manager, it crashes and goes back to Metacity.

This is the output from beryl-manager when running from terminal:
```
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

libberylsettings: dlopen: /usr/lib/beryl/libbench.so: cannot open shared object file: No such file or directory
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libwallpaper.so' plugin
beryl-xgl: Support for non power of two textures missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :1.0

```
I have tried different ways to install and methods of running and usung beryl, but the last error has remained the same.

Originally i used the script found at beryl-project.org's wiki Install Beryl on Ubuntu Edgy with XGL and ATI".

I have found alot of comments on blogs and forum posts where people have the same problem, but I have yet to see a clear solution to it. I hope someone can point me in the right direction.

System Info:
ATI Mobility Radeon 7500 (IBM ThinkPad T41)
Ubuntu 6.10, installed and updated today
Beryl svn as of today, tried with 0.1.9999 eariler (the one the script from beryl-projects wiki installs)

xorg.conf:
```
(....)
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver      "radeon"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
#	Identifier  "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Identifier "aticonfig-Device[0]"
	Driver      "radeon"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
	Option "DRI" "true"
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
	Option "XAANoOffscreenPixmaps"
	Option "RenderAccel" "true"
	Option "AGPFastWrite" "on"
	#Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
EndSection
(....)
Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
  Option "Composite" "0"
	#Option "Composite" "Enable" 
EndSection
```

Im using XGL, so heres the output from xglinfo:
```
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 1x TCL
OpenGL version string: 1.2 (1.2 (1.3 Mesa 6.5.1))
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias
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

I am very inexperienced with using GUI's on linux, so i may have left some important info out.

Also, I have tried alot of different things gathered all over the place, so I can't really remember each detail and solution I have tried - but mainly, different versions of beryl, different ways of launching it, PriceChilds fix and using a .Xsession in my homedir to force DISPLAY=:1

Thank you :)

---

### Post by CocoAUS on 2007-03-07
What method did you use to install Beryl?

---

### Post by vertigo- on 2007-03-07
I reinstalled ubuntu, and used the "Install Beryl on Ubuntu Edgy with AIGLX" now its running smoothly :)
And it looks goooooood. Too bad it doesent work well with rdesktop. But im happy anyway, now i have something to show off tomorrow.

---

