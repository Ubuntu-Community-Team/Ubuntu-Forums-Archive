---
title: "revert to compiz default, window managers"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by cottoncloth on 2007-06-27
Had a great thing going for a long time with 7.04 default desktop-effects compiz and metacity, using (I think) indirect rendering and my ATI x550.  it just worked so i didn't ask questions.

Installed compiz fusion (great stuff!), worked perfectly, beautifully, till I had to restart.  Then I lost my window decorator like others have.  Alt+F2 metacity --replace & brought them back, could not compiz --replace & without crashing my session.  So from them on out no more compiz fusion.

Removed the repo links, uninstalled everything compiz-fusion, reinstalled desktop-effects + default compiz, but still cannot get the old eye candy back up and running.  I get the feeling i have multiple window managers, but I don't know how that happened... 

Anybody have any suggestions how I can revert or even get compiz-fusion running again?  Do I have to use emerald?  I don't remember having direct rendering, but I could be wrong...

```

/xorg.conf

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
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV370 [Sapphire X550 Silent]"
	Driver		"ati"
	BusID		"PCI:5:0:0"
	Option "XAANoOffscreenPixmaps" "true"
	Option "AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
	Identifier	"G220f"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 [Sapphire X550 Silent]"
	Monitor		"G220f"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"2048x1536" "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"2048x1536" "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"2048x1536" "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"2048x1536" "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"2048x1536" "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"2048x1536" "1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	Option "AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

```

and some other info:

```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_gpu_program_parameters, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

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
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

```
$ dpkg-query -s xserver-xorg-video-ati|grep Version
Version: 1:6.6.3-2ubuntu6
```
```

$ glxinfo | grep direct
direct rendering: Yes

```

```
$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing...
```

```

$ metacity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager
```.
```

$ compiz
/usr/bin/compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

```

---

### Post by hyperair on 2007-06-27
Could you get the output from compiz- --replace? Try something like:
```
compiz --replace -c emerald 2>&1 | tee something.txt
```

---

### Post by cottoncloth on 2007-06-27
hi!  thank you! 

```
$ compiz --replace -c emerald 2>&1 | tee something.txt
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
/usr/bin/compiz.real: Couldn't load plugin '-c'
/usr/bin/compiz.real: Couldn't load plugin 'emerald'
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

then i installed emerald (w/ beryl-core, etc., too)  and got:
```

$ compiz --replace -c emerald 2>&1 | tee something.txt
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
/usr/bin/compiz.real: Couldn't load plugin '-c'
/usr/bin/compiz.real: Couldn't load plugin 'emerald'
/usr/bin/compiz.real: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu
/usr/bin/compiz.real: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu
/usr/bin/compiz.real: Failed to load slide: /home/Untitled.png
inotify_add_watch: No such file or directory
/usr/bin/compiz.real: Couldn't load plugin 'showdesktop'
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

...terminal hangs and i don't get the txt file

is there a way i can "clean out" completely?  just starting with the basics?

---

### Post by hyperair on 2007-06-27
Wait. You aren't using Compiz Fusion are you? And you want it bacl? or what. Do you have trevino's eyecandy repository in your /etc/apt/sources.list file?

---

### Post by cottoncloth on 2007-06-28
didn't mean to confuse.  by now i have removed trevino's sources, and completely uninstalled everything compiz, beryl, and emerald.  after many blunt tries i was able to get the default compiz stuff back up and running with GTK and metacity.

everyone keeps talking about emerald when you lose window decorations so i figured it was supposed to be there somehow and installed it so I could run without editing the command..  

under almost any other circumstances than default "desktop-effects"/compiz 0.3.6/GTK/metacity, I kept getting two kinds of error, 1 - that screen 0,0 already had a window manager in use (that i could not --replace) or 2 -

```
"Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded "
```

also i was wrong about the video card, i AM using direct rendering with AIGLX but it's an R370 so i shouldn't have been expecting peaches anyhows.  

nice to see what's on the bleeding edge, if just for a bit.

thanks again hyperair

---

### Post by hyperair on 2007-06-29
Actually the default Compiz in the Ubuntu repositories won't work with Emerald. Only Compiz Fusion works with Emerald. For default compiz, you have to use gtk-window-decorator instead. 

Also you say that --replace does not work, could you provide us with the full, exact output?

---

### Post by cottoncloth on 2007-06-30
with compiz fuzion/gtk-window-decorator/metacity installed

running this command using alt+F2
```

compiz --replace 2>&1 |  tee /home/Desktop/compiztest.txt
```

produces this:

```
Adding plugin cubereflex (cubereflex)
Adding plugin decoration (decoration)
Adding plugin fadedesktop (fadedesktop)
Adding plugin put (put)
Adding plugin inotify (inotify)
Adding plugin clone (clone)
Adding plugin plane (plane)
Adding plugin resize (resize)
Adding plugin glib (glib)
Adding plugin wall (wall)
Adding plugin opacify (opacify)
Adding plugin animation (animation)
Adding plugin extrawm (extrawm)
Adding plugin imgjpeg (imgjpeg)
Adding plugin trailfocus (trailfocus)
Adding plugin water (water)
Adding plugin svg (svg)
Adding plugin neg (neg)
Adding plugin video (video)
Adding plugin scaleaddon (scaleaddon)
Adding plugin addhelper (addhelper)
Adding plugin switcher (switcher)
Adding plugin minimize (minimize)
Adding plugin place (place)
Adding plugin scale (scale)
Adding plugin group (group)
Adding plugin zoom (zoom)
Adding plugin showdesktop (showdesktop)
Adding plugin regex (regex)
Adding plugin thumbnail (thumbnail)
Adding plugin screenshot (screenshot)
Adding plugin blur (blur)
Adding plugin vpswitch (vpswitch)
Adding plugin snap (snap)
Adding plugin dbus (dbus)
Adding plugin rotate (rotate)
Adding plugin splash (splash)
Adding plugin wobbly (wobbly)
Adding plugin bench (bench)
Adding plugin mblur (mblur)
Adding plugin winrules (winrules)
Adding plugin fade (fade)
Adding plugin firepaint (firepaint)
Adding plugin ring (ring)
Adding plugin png (png)
Adding plugin fs (fs)
Adding plugin text (text)
Adding plugin annotate (annotate)
Adding plugin expo (expo)
Adding plugin move (move)
Adding plugin reflex (reflex)
Adding plugin crashhandler (crashhandler)
Adding plugin resizeinfo (resizeinfo)
Adding plugin cube (cube)
Adding core settings (General Options)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing decoration options...done
Initializing resize options...done
Initializing minimize options...done
Initializing place options...done
Initializing zoom options...done
Initializing showdesktop options...done
Initializing blur options...done
Initializing wXIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"

      after 3020 requests (3009 known processed) with 2 events remaining.

obbly options...done
Initializing fade options...done
Initializing move options...done
Initializing cube options...done
Initializing trailfocus options...done
Initializing switcher options...done
Initializing scale options...done
Initializing rotate options...done
Initializing expo options...done
Initializing cubereflex options...done
```

---

### Post by hyperair on 2007-06-30
Could be an ATi problem. I'm an nVidia user so I'm rather inexperienced with ATi cards.

---

