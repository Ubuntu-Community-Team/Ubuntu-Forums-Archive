---
title: "3d acceleration"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Matthew Bartram on 2006-06-04
Having upgraded to dapper, 3d acceleration works... partly

My graphics card is an ATI Rage 128 RF/SG AGP, my cpu is 450MHz, and I have 384MB ram

glx gears shows that 3d acceleration is working in virtual terminal 7 (the first one), but not in any subsequent ones. If, in another, I switch to 1024x768 resolution, glxgears works for a few seconds, then stops working. And does the same if I start it again. If I then switch back to 1152x864, it works then stops, but then won't work again.

Armagetron detects that 3d acceleration is present, but runs very slowly (e.g. 2fps at last test). Unless I'm in a different vertual terminal, where the 3d doesn't work, so armagetron accounts for that, and runs more reasonably, but with lower performance.

gltron simply quits when I select game (fromthe main menu; to start the actual play)

and gl-117 runs slow on the lowest quality options

Celestia runs a bit jerkily; I don't know if that's just my computer speed.

---

### Post by JoWilly on 2006-06-04
[QUOTE=Matthew Bartram]Having upgraded to dapper, 3d acceleration works... partly

My graphics card is an ATI Rage 128 RF/SG AGP, my cpu is 450MHz, and I have 384MB ram

glx gears shows that 3d acceleration is working in virtual terminal 7 (the first one), but not in any subsequent ones. If, in another, I switch to 1024x768 resolution, glxgears works for a few seconds, then stops working. And does the same if I start it again. If I then switch back to 1152x864, it works then stops, but then won't work again.

Armagetron detects that 3d acceleration is present, but runs very slowly (e.g. 2fps at last test). Unless I'm in a different vertual terminal, where the 3d doesn't work, so armagetron accounts for that, and runs more reasonably, but with lower performance.

gltron simply quits when I select game (fromthe main menu; to start the actual play)

and gl-117 runs slow on the lowest quality options

Celestia runs a bit jerkily; I don't know if that's just my computer speed.[/QUOTE]


It its jerky (but wasnt before) : have you checked if agp is enabled ?

---

### Post by Matthew Bartram on 2006-06-04
[QUOTE=JoWilly]It its jerky (but wasnt before) : have you checked if agp is enabled ?[/QUOTE]

Rather than not being jerky before (in breezy), 3d acceleration simply did not work.

How do I check if agp is enabled?

---

### Post by patrick295767 on 2006-06-17
[QUOTE=Matthew Bartram]Having upgraded to dapper, 3d acceleration works... partly

My graphics card is an ATI Rage 128 RF/SG AGP, my cpu is 450MHz, and I have 384MB ram

glx gears shows that 3d acceleration is working in virtual terminal 7 (the first one), but not in any subsequent ones. If, in another, I switch to 1024x768 resolution, glxgears works for a few seconds, then stops working. And does the same if I start it again. If I then switch back to 1152x864, it works then stops, but then won't work again.

Armagetron detects that 3d acceleration is present, but runs very slowly (e.g. 2fps at last test). Unless I'm in a different vertual terminal, where the 3d doesn't work, so armagetron accounts for that, and runs more reasonably, but with lower performance.

gltron simply quits when I select game (fromthe main menu; to start the actual play)

and gl-117 runs slow on the lowest quality options

Celestia runs a bit jerkily; I don't know if that's just my computer speed.[/QUOTE]
  
this means your jerky glxgears is giving you no graphics acceleration
 
Do u have this when u type : 
glxinfo
```
name of display: :0.0
display: :0  screen: 0
direct rendering: [COLOR="Red"]No[/COLOR]          # no = no acceleration
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_vis
```
  
What 's ur /etc/X11/xorg ?

[http://www.ubuntuforums.org/showthread.php?t=171297&highlight=Rage+128+RF%2FSG+AGP](http://www.ubuntuforums.org/showthread.php?t=171297&highlight=Rage+128+RF%2FSG+AGP)
for agp, sthg like : Option "UseInternalAGPGART" "no"

grtz

---

### Post by Matthew Bartram on 2006-06-18
glxinfo gives
```
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: VA Linux Systems, Inc.
OpenGL renderer string: Mesa DRI Rage 128 20041026 AGP 1x
OpenGL version string: 1.2 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_compression, GL_ARB_texture_env_add,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_separate_specular_color, GL_EXT_subtexture, GL_EXT_texture,
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format,
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x26 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x2a 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2b 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x2e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x32 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
```

My xorg.conf file is:
[indent]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 RF/SG AGP"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"ViewSonic GS"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 RF/SG AGP"
	Monitor		"ViewSonic GS"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection[/indent]

Glxinfo from vertual terminal 8 tells me "direct rendering: No"

---

### Post by disturbed1 on 2006-06-18
Try changing your driver to "r128". Using the driver "ati" Xorg should decide to use "radeon", "r128", or "atimisc", but it may not of here.
Then read 
```
man r128
```

Look at this section and see if it pertains to you, or any of the other sections.

[quote="man r128"]
Option "VGAAccess" "boolean"
              Tell  the  driver  if  it  can  do  legacy VGA IOs to the card. This is necessary for properly resuming consoles when in VGA text mode, but
              shouldn’t be if the console is using radeonfb or some other graphic mode driver. Some platforms like PowerPC have issues  with  those,  and
              they aren’t necessary unless you have a real text mode in console. The default is off on PowerPC and on on other architectures.
[/quote]

---

### Post by Matthew Bartram on 2006-06-30
Thanks. I'm going to get a new computer soon, so I'll try again with that (it will be the same graphics card.)

---

