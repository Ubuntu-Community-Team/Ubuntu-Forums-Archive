---
title: "Help...3D-acceleration, not correct"
date: 2006-02-20
forum: Gaming &amp; Leisure
---

### Post by Corvus_corax on 2006-02-20
I tried several 3D games. and they, or dont work, or have a very very slow and low framerate. 
I have the correct driver for via/S3 Unichrome.

Games arent really that important 2 me but i still want it 2 work correctly, especially since i recently bought a new pc...

I tried playing planetpenguin-racer... slune...freedoom(doesnt work and show in the menu at all) etc...

Pleaz help me out, someone...

---

### Post by deadlydeathcone on 2006-02-21
Could you post your /etc/X11/xorg.conf file and check if DRI is enabled by running 'glxinfo' (minus the quotes) in the console?

This will probably require a bit of work, as you're probably either going to have to download a driver or upgrade to dapper.

---

### Post by akiro.yamamoto on 2006-02-21
Actually I think the S3 video card only has Accelerated 2D support no 3D support.
For true 3D support you will need a Nvidia or ATI video card. Check pricewatch for a good Nvidia FX5200 AGP/PCI card. It is relatively cheap and can handle most games.

---

### Post by Corvus_corax on 2006-02-21
Okay...@deadlydeathcone,

Here is the requested content:
[QUOTE="Xorg.conf"][COLOR="SeaGreen"]Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"S3G Unichrome Pro"
	Driver		"via"
	BusID		"PCI:1:0:0"
	VideoRam	65536
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Philips 107B"
	Option		"DPMS"
	HorizSync	30-92
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3G Unichrome Pro"
	Monitor		"Philips 107B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection[/COLOR][/QUOTE]
and here's what I get when I run 'glxinfo':
[QUOTE="glxinfo"][COLOR="Blue"]root@DD77XQ60-B:~# glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square,
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None[/COLOR]
[/QUOTE]

I hope you can find something...

@akiro.yamamoto

Could it be...? 
Tomb raider, TAXI DRIVER, Half Life, etc... all work very well on windows XP Pro...
Is this because Direct X is far more superior then all 3D-accelerators?

Maybe i should plug-in my old Nvidia Riva TNT2 Pro 32MB, 
from my other old pc(Piii500Mhz)...?!
It worked fine with Debian...

@all
Well anyway...
I hope it'll work with my hardware configuration the way it is,
when not, I'm in no hurry and don't care about games, so I'll have some time to save money 4 a new VGA-card...
Untill then, when I want 2 play games, It'll be under windows XP.

---

### Post by deadlydeathcone on 2006-02-21
It seems that you have the correct drivers installed, so hopefully this is a configuration problem. First off add "Option" (without the quotes) before VideoRam under the Devices section and add the lines:

	Option		"DisableIRQ"
	Option		"EnableAGPDMA"

If this doesn't work try commenting out Option "UseFBDev" "true", then type the command "lsmod" into the console and see if it the modules via, via_agp and drm show up in the horrible mess it spews at you.

Your games should work as well under linux as they do in windows (if they actually work, that is). Your card just doesn't have direct rendering enabled, meaning all of the 3d work is being dumped on your processor.

---

### Post by Corvus_corax on 2006-02-21
Ohw NOOO!!! How stupid am I...:mrgreen: 
I just found out what the problem is, not having a VGA-card...
3D games also didn't work on windows...:-#  

On my other old pc they did work...:mrgreen:  
I was a bit confused...so I mixed the 2 pc's in my mind
I'm so sorry 4 wasting your time...:-k 

Do you think that when I plug my Nvidia RIVA TNT2 Pro (32Mb) in the new pc it'll work?

I've just installed Ubuntu 5.10-i386 on the old Piii (501.1Mhz) 
Lets C if 3D-acceleration does better on the oldie then on the new one...

I am sooooo sorry, that's what you get when you stay up all night(s)...

Thnx anyway!

---

### Post by aljones15 on 2006-02-22
OpenGL renderer string: Mesa GLX Indirect
all that aside you're running software 3d render
not native. get a pci card if your card doesn't support 3d.

peace,
a

---

### Post by Cysman on 2006-02-24
[QUOTE=deadlydeathcone]Could you post your /etc/X11/xorg.conf file and check if DRI is enabled by running 'glxinfo' (minus the quotes) in the console?

This will probably require a bit of work, as you're probably either going to have to download a driver or upgrade to dapper.[/QUOTE]

Sorry to but in but I'm having the same problem.  I have an ATI 9800 pro card and this is my .conf file.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"MX50"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"MX50"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

And this is my glxinfo:

kenoutten@ubuntuhome:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square,
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None

What am I missing?

---

### Post by polpak on 2006-02-24
[QUOTE=Cysman]Sorry to but in but I'm having the same problem.  I have an ATI 9800 pro card and this is my .conf file.

*...snip...*

What am I missing?[/QUOTE]

What you are missing is a link to the wiki:

[https://wiki.ubuntu.com]("https://wiki.ubuntu.com")

Specifically what you are needing is the ATI binary driver, who's installation is covered here:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

---

### Post by Cysman on 2006-02-24
[QUOTE=polpak]What you are missing is a link to the wiki:

[https://wiki.ubuntu.com]("https://wiki.ubuntu.com")

Specifically what you are needing is the ATI binary driver, who's installation is covered here:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")[/QUOTE]

Thanks for pointing me in the right direction, much appreciated.;)

---

### Post by Cysman on 2006-02-25
[QUOTE=polpak]What you are missing is a link to the wiki:

[https://wiki.ubuntu.com]("https://wiki.ubuntu.com")

Specifically what you are needing is the ATI binary driver, who's installation is covered here:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")[/QUOTE]

Wow, I gotta tell ya, that worked like a charm.  Thanks alot!!\\:D/

---

### Post by cdsboy on 2006-02-26
also for the ati cards i find it is best to change the drive from ati to radeon. the radeon drivve has better 3d support

---

### Post by Corvus_corax on 2006-03-12
Hi folks!

Here I am again...!!!

After all my experience with Debian on my old trustworthy PIII wich i sold...
I feel stupid and a rookie all over again, with my new AMD64bits Sempron PC.
I have the following motherboard Asus K8V-MX with via S3G Unichrome pro VGA onboard.

I found out after all that 3D games like 'half-life'  or 'Tomb Raider' run perfect on XPpro with my onboard VGA...
but still the most simple 3D games like 'SLUNE' works like SHIT under UBUNTU 5.10 AMD64...grrr

I have noticed that a 2D game like 'supertux' has EXACTLY the same problem when I am running it, 
but in the options I can undo the selection 'openGL' and then it goes perfect!!!
In 3D games I've installed there is no such option to de-select openGL.

HELPHELPHELP...

Ciao

---

### Post by ScoobyDan on 2006-03-23
Corvus_corax,

I have a similar set-up to you: AMD Sempron 2600 64bit and Gigabyte motherboard with on-board graphics, sound and network (all from VIA). The graphics is the VIA Unichrome (possibly Pro - depends what version board I have, and I'm not possitive). I also couldn't get DRI to work in Hoary or Breezy.

The good news is that I am currently testing Dapper, and DRI is working fine! When I installed Dapper, it was using the VESA driver, so I still wasn't getting DRI support. I rebooted into recovery mode, and ran
```
dpkg-reconfigure xserver-xorg
```to configure the graphics. My graphics card wasn't auto-detected, so I manually configured it, and voila! DRI is now enabled, and games are now working fine (well, the Mario-type game (can't remember the name) is).

Basically, if you don't want to buy a new graphics card, either install a beta Dapper now, or wait until it is released in July...

Daniel

---

