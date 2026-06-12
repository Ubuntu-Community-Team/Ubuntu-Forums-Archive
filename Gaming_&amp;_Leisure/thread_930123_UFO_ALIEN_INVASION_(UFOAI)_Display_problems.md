---
title: "UFO ALIEN INVASION (UFOAI): Display problems"
date: 2008-09-25
forum: Gaming &amp; Leisure
---

### Post by fedemw on 2008-09-25
Hello all,

I am trying to play UFO AI under Ubuntu Hardy 8.04

[http://ufoai.ninex.info](http://ufoai.ninex.info)

The problem is:
I can execute the game (console or launcher) but the game tilts my computer when i play first mission. I can start move soldiers, pass turns but for some reason in no more than 5 minutes all is broken.

As i seen [http://ufoai.ninex.info/forum/index.php?topic=2926.0](http://ufoai.ninex.info/forum/index.php?topic=2926.0) The Xserver on Ubuntu Hardy freezes and flickers randomly

I downloaded the 2.2.1 game from:
deb [http://trylegaldownloads.de/ubuntu](http://trylegaldownloads.de/ubuntu) hardy games 

Machine configuration:

```
glxgears -info
SGIX_depth_texture GL_SUN_multi_draw_arrays
5406 frames in 5.0 seconds = 1081.200 FPS
123094 frames in 5.0 seconds = 24618.761 FPS
128303 frames in 5.0 seconds = 25660.538 FPS
78168 frames in 5.0 seconds = 15621.830 FPS
4779 frames in 5.0 seconds = 955.725 FPS

```

```
lenin@CCCP:~$ uname -a
Linux CCCP 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```

```
enin@CCCP:~$ glxinfo | grep direct
direct rendering: Yes
```

Video Card
```
lenin@CCCP:~$ lspci | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```


The UFO console is here. IT seems not report anything special:

```
lenin@CCCP:~/.ufoai/2.2.1/base$ more ufoconsole.log 

----- network initialization -------
libcurl/7.18.0 OpenSSL/0.9.8g zlib/1.2.3.3 libidn/1.1 initialized.

------ server initialization -------

----- console initialization -------
couldn't load history
Console initialized.

------- video initialization -------
SDL version: 1.2.12
I: desktop depth: 32bpp
I: setting mode 6: 1024x768 (fullscreen: no)
I: got 8 bits of stencil
I: got 24 bits of depth buffer
I: got double buffer
I: got 8 bits for red
I: got 8 bits for green
I: got 8 bits for blue
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 7.0.3-rc2
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_shadow GL_AR
B_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_AR
B_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_objec
t GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_l
ogic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_text
ure GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset 
GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_t
exture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture
_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels 
GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_
MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_col
or_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays
ignoring GL_EXT_LockArrays
using GL_ARB_multitexture
using GL_EXT_texture_env_combine
GL_SGIS_multitexture not found
ignoring GL_ARB_texture_compression
using GL_EXT_texture_filter_anisotropic [ 2 max] [ 1 selected]
using GL_EXT_texture_lod_bias
using GL_EXT_stencil_wrap
using GL_EXT_fog_coord
GL_ATI_separate_stencil not found
GL_EXT_stencil_two_side not found
max texture size: detected 2048
SDL_ttf version 2.0.9 - we need at least 2.0.7

------- sound initialization -------
SDL_mixer version: 1.2.8
...audio rate: 44100
...audio channels: 2
...driver: 'alsa'

--- save subsystem initialization --
added size subsystem (check ff)
added base subsystem (check 0)
added campaign subsystem (check 1)
added hospital subsystem (check 2)
added market subsystem (check 3)
added research subsystem (check 4)
added employee subsystem (check 5)
added aliencont subsystem (check 6)
added production subsystem (check 7)
added aircraft subsystem (check 8)
added messagesystem subsystem (check 9)
added stats subsystem (check a)
added nations subsystem (check b)
added transfer subsystem (check c)

----------- parse scripts ----------
Shared Client/Server Info loaded
... 94 items parsed
... 31 damage types parsed
... 52 map definitions parsed
... 25 equipment definitions parsed
... 10 inventory definitions parsed
... 22 team definitions parsed
Could not load 'PsymongN3' background track
CL_LanguageInit()... language settings are stored in configuration: en
123 static models loaded
====== UFO Initialized ======

Switch grab input off

------- video initialization -------
SDL version: 1.2.12
I: desktop depth: 32bpp
I: setting mode 6: 1024x768 (fullscreen: no)
I: got 8 bits of stencil
I: got 24 bits of depth buffer
I: got double buffer
I: got 8 bits for red
I: got 8 bits for green
I: got 8 bits for blue
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 7.0.3-rc2
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_shadow GL_AR
B_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_AR
B_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_objec
t GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_l
ogic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_text
ure GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset 
GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_t
exture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture
_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels 
GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_
MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_col
or_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays
ignoring GL_EXT_LockArrays
using GL_ARB_multitexture
using GL_EXT_texture_env_combine
GL_SGIS_multitexture not found
using GL_ARB_texture_compression
using GL_EXT_texture_filter_anisotropic [ 2 max] [ 1 selected]
using GL_EXT_texture_lod_bias
using GL_EXT_stencil_wrap
using GL_EXT_fog_coord
GL_ATI_separate_stencil not found
GL_EXT_stencil_two_side not found
max texture size: detected 2048
SDL_ttf version 2.0.9 - we need at least 2.0.7
...registering 10 fonts
Could not set mission aircraft

------- video initialization -------
SDL version: 1.2.12
I: desktop depth: 32bpp
I: setting mode 6: 1024x768 (fullscreen: no)
I: got 8 bits of stencil
I: got 24 bits of depth buffer
I: got double buffer
I: got 8 bits for red
I: got 8 bits for green
I: got 8 bits for blue
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 7.0.3-rc2
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_shadow GL_AR
B_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_AR
B_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_objec
t GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_l
ogic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_text
ure GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset 
GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_t
exture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture
_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels 
GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_
MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_col
or_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays
ignoring GL_EXT_LockArrays
using GL_ARB_multitexture
using GL_EXT_texture_env_combine
GL_SGIS_multitexture not found
ignoring GL_ARB_texture_compression
using GL_EXT_texture_filter_anisotropic [ 2 max] [ 1 selected]
using GL_EXT_texture_lod_bias
using GL_EXT_stencil_wrap
using GL_EXT_fog_coord
GL_ATI_separate_stencil not found
GL_EXT_stencil_two_side not found
max texture size: detected 2048
but using 256 as requested
SDL_ttf version 2.0.9 - we need at least 2.0.7
...registering 10 fonts
Could not set mission aircraft
I: setting mode 4: 800x600 (fullscreen: no)
TAB - nextsoldier
ENTER - confirmaction
SPACE - nextalien
1 - soldier_select 0
2 - soldier_select 1
3 - soldier_select 2
4 - soldier_select 3
5 - soldier_select 4
6 - soldier_select 5
7 - soldier_select 6
8 - soldier_select 7
^ - toggleconsole
a - +turnleft
c - standcrouch
d - +turnright
e - nextround
f - +turndown
i - invopen
j - showchat
k - messagesay
l - messagesayteam
q - +turn
r - +turnup
s - leveldown
t - drawspottedlines;nextalienactor
v - cameramode
w - levelup
x - togglereaction
PAUSE - pause
UPARROW - levelup
DOWNARROW - leveldown
LEFTARROW - +turnleft
RIGHTARROW - +turnright
CTRL - +turn
SHIFT - targetalign
INS - +turnup
DEL - +turndown
PGDN - +zoomout
PGUP - +zoomin
F1 - game_quicksave
F2 - mn_push quickload
F10 - mn_push irc
F11 - hidehud
F12 - screenshot
KP_UPARROW - +shiftup
KP_LEFTARROW - +shiftleft
KP_RIGHTARROW - +shiftright
KP_DOWNARROW - +shiftdown
MOUSE1 - +select
MOUSE2 - +turn
MOUSE3 - +action
MWHEELDOWN - zoomoutquant
MWHEELUP - zoominquant
Changing to Singleplayer
Global data loaded - size 5204572 bytes
...techs: 166
...buildings: 21
...ranks: 16

...nations: 8

Activate stage intro
Sanity check for script data
...buildings ok
...tech ok
...aircraft ok
...menu ok
Could not load 'van_geoscape' background track
I: setting mode 4: 800x600 (fullscreen: yes)
Save 'slotquick'
...subsystem 'size' - saved 101 bytes
...subsystem 'base' - saved 13245 bytes
...subsystem 'campaign' - saved 326 bytes
...subsystem 'hospital' - saved 0 bytes
...subsystem 'market' - saved 2899 bytes
...subsystem 'research' - saved 7929 bytes
...subsystem 'employee' - saved 5778 bytes
...subsystem 'aliencont' - saved 0 bytes
...subsystem 'production' - saved 79 bytes
...subsystem 'aircraft' - saved 353 bytes
...subsystem 'messagesystem' - saved 1597 bytes
...subsystem 'stats' - saved 28 bytes
...subsystem 'nations' - saved 1248 bytes
...subsystem 'transfer' - saved 86400 bytes
Campaign 'QuickSave' saved.
------- Loading game.so -------
LoadLibrary (./base/game.so)
==== InitGame ====
checksum for the map '+orientaln': 4127275723
ufo script checksum 3967328534
Created AI player (team 0)
Created AI player (team 7)
-------------------------------------
Connecting to localhost...
Could not load 'van_mission' background track
Map: +orientaln
Starting the game...
 has joined team 0
(player 0) It's team 1's round
 has taken control over team 1.
Changed camera mode to first-person.
Changed camera mode to first-person.
Changed camera mode to first-person.
Changed camera mode to first-person.
Changed camera mode to first-person.
Changed camera mode to first-person.
Changed camera mode to remote.
I: sett

```


Pls let me know if you need another information. I really wanna play this game; i enjoyed so many years ago and now its free!

Thanks in advance and sorry my english.

;-)

---

