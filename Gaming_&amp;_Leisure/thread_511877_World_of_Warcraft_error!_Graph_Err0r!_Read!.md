---
title: "World of Warcraft error! Graph Err0r! Read!"
date: 2007-07-28
forum: Gaming &amp; Leisure
---

### Post by mu:te on 2007-07-28
Good morning,

All ever since I've began using Ubuntu, few months now, I've always had problems playing games!

I found a temporary way to play World of Warcraft, I had about 10fps, my mouse was dazed(bugged) and plenty of other problems so I gave up, I decided that this couldn't go on like this forever so I though it might be a good idea to change my "config.wtf" file in world of warcraft, which is basically the configure file of WoW.

What I did was, I c/p my friends WTF file and put it in my WoW folder. I opened the game with Crossover and Wine and the game was really really smooth, plus the mouse was working properly.

Now the problem is, when I enter the WoW after I've chosen character that I want to play I get this failure message.

```
2) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 191
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 191
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 191
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 191

```

infinity..

Now does anyone know how to fix this saint lords failure?

---

### Post by mu:te on 2007-07-28
I discovered something BIG!

The new Config that I got does not have "SET gxApi "OpenGL" in it!

After I added that In the config, the game became SLOW!

So basically, If I run the game in OpenGL it becomes terrible! Funky mouse, bad graphics, lag and stuff!

When I run the game in D3D its very very smooth, perfect mouse, nolag but the game crashes and gives me the error messages that I posted.

What can I do dear Penguin fellas??

---

### Post by darksidedude on 2007-07-28
did you install the game on linux or C/P from a winblows computer, because i noticed that if c/p it doesn't work right, because ive gotten upto 18fps outside on a nvidia 6200 in OPenGl mode

---

### Post by mu:te on 2007-07-28
> **darksidedude said:**
> did you install the game on linux or C/P from a winblows computer, because i noticed that if c/p it doesn't work right, because ive gotten upto 18fps outside on a nvidia 6200 in OPenGl mode

Installed, not c/p! What else might help?

---

### Post by darksidedude on 2007-07-28
i had the same problems for a while, maybe you could post your config.wtf so i can have a lookie loo

---

### Post by Ralgunagar on 2007-07-28
so how do i install world of warcraft on my comp?

---

### Post by mu:te on 2007-07-29
> **darksidedude said:**
> i had the same problems for a while, maybe you could post your config.wtf so i can have a lookie loo

**fglrxinfo**
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.0.6474 (8.38.7)

**glxinfo | grep rendering**
direct rendering: Yes

**glxgears** - when I'm watching the gears spinning I noticed that they always hang ever 2 seconds for just a little tick (0.1sek) and than continue. When I'm watching them I always got about 870 FPS but when I put some window over the gears I got over 4.600 frames. So I did a little research,. I put a window over half of the gears window and than I got about 1300FPS and I also noticed that they hang a lot less and less noticeable. Ill put the summary here below and you will see what I was talking about.
```
4337 frames in 5.0 seconds = 867.386 FPS
4287 frames in 5.0 seconds = 857.349 FPS
4288 frames in 5.0 seconds = 857.574 FPS
4288 frames in 5.0 seconds = 857.547 FPS
10157 frames in 5.0 seconds = 2031.390 FPS
22915 frames in 5.0 seconds = 4582.815 FPS
21581 frames in 5.0 seconds = 4316.024 FPS
23127 frames in 5.0 seconds = 4625.349 FPS
23178 frames in 5.0 seconds = 4635.527 FPS
23173 frames in 5.0 seconds = 4634.500 FPS
23160 frames in 5.0 seconds = 4631.841 FPS
23182 frames in 5.0 seconds = 4636.329 FPS
23189 frames in 5.0 seconds = 4637.795 FPS
23197 frames in 5.0 seconds = 4639.235 FPS
23251 frames in 5.0 seconds = 4650.199 FPS
23228 frames in 5.0 seconds = 4645.445 FPS
23209 frames in 5.0 seconds = 4641.623 FPS
23004 frames in 5.0 seconds = 4600.741 FPS
23237 frames in 5.0 seconds = 4647.332 FPS
23181 frames in 5.0 seconds = 4636.044 FPS
23159 frames in 5.0 seconds = 4631.621 FPS
21937 frames in 5.0 seconds = 4387.224 FPS
23252 frames in 5.0 seconds = 4650.338 FPS
23202 frames in 5.0 seconds = 4640.392 FPS
23170 frames in 5.0 seconds = 4616.266 FPS
23112 frames in 5.0 seconds = 4621.897 FPS
23014 frames in 5.0 seconds = 4602.692 FPS
23168 frames in 5.0 seconds = 4633.431 FPS
23105 frames in 5.0 seconds = 4620.974 FPS
21612 frames in 5.0 seconds = 4321.639 FPS
13014 frames in 5.0 seconds = 2602.640 FPS
7114 frames in 5.0 seconds = 1422.716 FPS
7109 frames in 5.0 seconds = 1421.770 FPS
6667 frames in 5.0 seconds = 1333.346 FPS
17561 frames in 5.0 seconds = 3512.180 FPS
23121 frames in 5.0 seconds = 4624.170 FPS
23136 frames in 5.0 seconds = 4627.151 FPS
23118 frames in 5.0 seconds = 4623.543 FPS
16949 frames in 5.0 seconds = 3389.153 FPS

```

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
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.0.6474 (8.38.7)
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

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

```


My Config.WTF
```
SET locale "enGB"
SET hwDetect "0"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET farclip "177"
SET specular "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET MusicVolume "0.30000001192093"
SET SoundVolume "0.40000000596046"
SET MasterVolume "0.40000000596046"
SET realmList "eu.logon.worldofwarcraft.com"
SET cameraYawMoveSpeed "270"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET AmbienceVolume "0.10000000149012"
SET minimapZoom "0"
SET uiScale "0.79999995231628"
SET useUiScale "1"
SET autoSelfCast "1"
SET gameTip "69"
SET cameraView "4"
SET minimapInsideZoom "0"
SET readScanning "-1"
SET readContest "-1"
SET DesktopGamma "1"
SET gxVSync "0"
SET profanityFilter "0"
SET cameraSmoothStyle "0"
SET guildMemberNotify "1"
SET timingTestError "0"
SET scriptMemory "131072"
SET EnableErrorSpeech "0"
SET ffx "0"
SET gxWindow "1"
SET cameraWaterCollision "0"
SET ShowTargetCastbar "1"
SET patchlist "eu.version.worldofwarcraft.com"
SET checkAddonVersion "0"
SET mouseSpeed "1"
SET weatherDensity "0"
SET realmName "Burning Blade"
SET showGameTips "0"
SET showToolsUI "0"
SET secureAbilityToggle "0"
SET UnitNamePlayer "0"
SET gxApi "d3d"
SET gxCursor "0"
SET lod "1"
SET baseMip "1"
SET spellEffectLevel "0"
SET lastCharacterIndex "2"
SET MasterSoundEffects "0"
SET EnableMusic "0"
SET EmoteSounds "0"
SET SoundListenerAtCharacter "0"
SET shadowLOD "0"
```

My Xorg.Conf

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
   Identifier  "ATI RADEON X300"
   Driver      "fglrx"
   Option       "Capabilities" "0x00000800"
   Option       "UseFastTLS" "off"
   Option       "KernelModuleParm" "locked-userpages=0"
 EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X300"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "0"
EndSection

```

---

### Post by darksidedude on 2007-07-29
hmm when you ran in gl mode was it in windowed mode? if it was that could be the problem, also try if ur in windowed mode set it to ur desktop resolution, heard that causes major issues with X 


1st try GL mode full screen, ( remove the part about gxwindow in config.wtf) 
2nd try open Gl mode window mode set at screen rez ( 1024x768 )  seems to work the best

best of luck:)

---

### Post by mu:te on 2007-07-29
> **darksidedude said:**
> hmm when you ran in gl mode was it in windowed mode? if it was that could be the problem, also try if ur in windowed mode set it to ur desktop resolution, heard that causes major issues with X 


1st try GL mode full screen, ( remove the part about gxwindow in config.wtf) 
2nd try open Gl mode window mode set at screen rez ( 1024x768 )  seems to work the best

best of luck:)

I opened glxgears and full sized the windows, I got 100fps, incredibly now! and a funny thing, the gears hanged so much that they went reverse!

Than I opened WoW with openGL in full size, and the game hanged and lag so much that I could barely move the mouse!

Than I opend WoW with openGL in windows mode in the 1024 x 768 rez, and I was able to play the game with 15 fps, kind of lame.. because with the same setting with d3d I had 40fps.. but of course the game always crashed after 3 sek.. :(

Any more tips mate?

---

### Post by darksidedude on 2007-07-29
hmm 100fps for gears is kinda low dude, with that rateing you should be lucky to get 15fps in wow

one last thing to try is this

open gl no window, go into config.wtf and then set it to be  640x 480 dont know how low it can go, try bumping up your refresh rate from 60 to about 65 see if that makes a difference,  


i had a laptop that had that card once, when i ran windows ( yes i did at one time) 2k to be exact i was getting about 18fps so 15 isnt that bad on linux

---

### Post by mu:te on 2007-07-29
> **darksidedude said:**
> hmm 100fps for gears is kinda low dude, with that rateing you should be lucky to get 15fps in wow

one last thing to try is this

open gl no window, go into config.wtf and then set it to be  640x 480 dont know how low it can go, try bumping up your refresh rate from 60 to about 65 see if that makes a difference,  


i had a laptop that had that card once, when i ran windows ( yes i did at one time) 2k to be exact i was getting about 18fps so 15 isnt that bad on linux

It is, it really is and only if I could get the answer how to run the game in D3D than I wouldn't have this problem now because WoW runs with 40-60fps on D3D!

Although in 800 x 600 which is the lowest res I could get I had only 18fps.

---

### Post by michaelfitzi on 2007-07-29
Hello quick question. I have World of Warcraft installed on the Windows XP side, if I use Wine, can I play it, or will i have to re-install the whole thing?

Thanks for any help! World of Warcraft is the only think keeping windows on my computer now!

---

### Post by darksidedude on 2007-07-29
you can try and c/p it all you *theoretically have to do is change the wow config.wtf 

there is cedega cvs  but i never have used it ( dont like to compile from source :popcorn: )
supsoedly cedega can run games with DX but im not to shure ive heard the horror storys about cedega,

---

