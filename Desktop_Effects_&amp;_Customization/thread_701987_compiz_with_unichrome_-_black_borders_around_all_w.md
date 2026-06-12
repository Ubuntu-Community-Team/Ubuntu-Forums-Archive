---
title: "compiz with unichrome - black borders around all windows"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by bhospadaruk on 2008-02-19
What a long strange trip it's been for this newbie!

I finally have compiz working but there are thick black borders around all window and menus.  I think that this has something to do with the drop shadow area that I see on other peoples screens.  a screen shot is attached

I am using Gutsy 7.10 with a VIA board that has CN700 integrated graphics.

I am using the driver binary from VIA found at :
[_http://www.viaarena.com/_]("http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=158")

The output from glxinfo looks like this:
```
bob@bob-ubuntu:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
OpenGL version string: 1.2 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  1 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x23 24 tc  1 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  1 24  0 r  .  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  1 24  0 r  y  .  8  8  8  0  0 32  0  0  0  0  0  0 0 None
0x27 24 tc  1 24  0 r  .  .  8  8  8  0  0 32  0  0  0  0  0  0 0 None
0x28 24 tc  1 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  1 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  1 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x2b 24 tc  1 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16 16  0 0 None
0x2c 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x2d 24 tc  1 24  0 r  .  .  8  8  8  0  0 16  0 16 16 16 16  0 0 None
0x2e 24 tc  1 24  0 r  y  .  8  8  8  0  0 32  0 16 16 16 16  0 0 None
0x2f 24 tc  1 24  0 r  .  .  8  8  8  0  0 32  0 16 16 16 16  0 0 None
0x30 24 tc  1 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  0 0 None
0x31 24 tc  1 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  0 0 None
0x53 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
bob@bob-ubuntu:~$ 

```

My xorg.conf looks like:
```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"extmod"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
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
	Identifier	"Generic Video Card"
	Boardname	"via"
	Busid		"PCI:1:0:0"
	Driver		"via"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"MonitorGeneric Video Card"
	Vendorname	"Hewlett-Packard"
	Modelname	"HP 7550 Color Monitor"
	Horizsync	30.0-86.0
	Vertrefresh	50.0-140.0
  modeline  "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
  modeline  "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
  modeline  "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"MonitorGeneric Video Card"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1280x854"	"1280x768@60"	"1152x768@54"	"1280x720@60"	"800x600@60"	"1280x800@75"	"800x600@85"	"1280x768@75"	"800x600@75"	"1280x720@50"	"800x600@72"	"1280x800@60"	"800x600@56"	"1440x900@75"	"720x400@85"	"1440x900@60"	"640x350@85"	"1600x1024@60"	"640x400@85"	"1680x1050@60"	"1680x1050@75"	"1920x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
	Group	0
EndSection
Section "ServerFlags"
EndSection
```

Just to let everyone else know, I could never enable "visual effects" (compiz) until I edited compiz:

sudo gedit /usr/bin/compiz

And I changed this:
# Driver whitelist
WHITELIST="nvidia intel ati radeon i810"
to this:
# Driver whitelist
WHITELIST="**via** nvidia intel ati radeon i810"

Thanks for any help you can provide!:popcorn:

---

### Post by jaygo on 2008-02-20
well I'm happy to hear you're getting 3d out of a VIA chipset. The general verdict is that it's too buggy to use, let alone run compiz successfully. Is it stable?

As for the black borders, those look a lot like shadows. Can you check your compiz & non-compiz settings for drop shadows and disable them? (I only know where to find them for Xfce & KDE)

---

### Post by bhospadaruk on 2008-02-20
It does seem stable enough - I'm just startin to use the system, but it hasn't crashed or locked up yet.

I also don't really know what to do about the shadows.  There is alot of similar sounding situations out there, but nothing like this.  I saw some KDE posts from people with white borders... but didn't seem to find a clear resolution there either - perhaps except turning off drop shadows altogether.  But that misses the point doesn't it?

---

### Post by mrmiserable on 2008-02-20
could be reflection plugin on compiz

---

### Post by programmer8922 on 2008-02-20
It looks to me like you need to enable transparency in your xorg file. Add this to the "Device" section of your xorg file. ```
 Option         "AddARGBGLXVisuals" "True"
```

---

### Post by jaygo on 2008-02-21
well, for now, I'd happily give up drop shadows to have 3d eye candy like compiz.

BTW, just read at the very end of VIA's readme that this is a known issue:
> 11. Known issues
  Due to the formal driver release is based on Fedora Core Series, there are some
  known issues below under Ubuntu 7.10 testing.
 ....
  b. There are black borders around working window when the “3D Desktop Effects” is
      enabled.

So if you can get it working without borders, you're ahead of the curve. GL & let us know what else you find. I'm trying these binary drivers next.

---

### Post by bhospadaruk on 2008-02-26
> **programmer8922 said:**
> It looks to me like you need to enable transparency in your xorg file. Add this to the "Device" section of your xorg file. ```
 Option         "AddARGBGLXVisuals" "True"
```

Hmmm.. I tried this option buut no change.  For sure this black border thing is all about transparency.  When I try other transparency using compic settings like "opacity"  I see black (or nearly black) where anything that should be transparent is.

---

### Post by bhospadaruk on 2008-02-26
> **mrmiserable said:**
> could be reflection plugin on compiz

Could you say more about your point?

---

### Post by mrmiserable on 2008-02-26
my point is probably wrong but here goes anyway 

i thought if you turn off the reflection plugin on compiz it might be your problem as apparently you have lets say awkward graphics card and perhaps it is not rendering this plugin correct just a thought always good to check all options i am probably totally way off but maybe 

anyway good luck

---

### Post by Hugolp on 2008-03-13
Hi

bhospadaruk I am thinking on buying a VIA with CN700 chipset as a media player. Can you comment on video performance? 720p? 1080p maybe? (probably being too optimistic here).

Also during this three weeks since you posted did you had any stability isues with the drivers?

Thanks

Hugo

---

### Post by bhospadaruk on 2008-03-13
As much as I like the idea of VIA's low power boards, I can't recommend them for graphic anything - not at least until VIA comes out with some better drivers.  From all I've read, I think you'd be much better off with something else more mainstream.  I'm still hoping I can get this thing working ok though...

---

