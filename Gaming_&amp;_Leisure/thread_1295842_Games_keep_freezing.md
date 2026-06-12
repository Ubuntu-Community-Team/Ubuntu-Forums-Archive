---
title: "Games keep freezing"
date: 2009-10-20
forum: Gaming &amp; Leisure
---

### Post by izackrp on 2009-10-20
*Edit
It turns out this is a driver problem with a mini-itx Jetway J7F2WE-1G2E and VIA CN700 North Bridge Chipset.
so skip to post#5


So far I tried to run open arena and super tux kart both freeze and at (sort of) random places. OA freezes during the menus, ingame (usually within a few seconds), and when bring the menu up during the game. From the command line (after terminating the game) it said some stuff about not loading skins and returned exit code 15.

I spent the whole day trying to get this game to work going from moonos to dsl(didn't install right) to xubuntu ](*,). And its getting very frustrating. Some of the freezes wouldn't let me ctrl+alt+f1...

I generated hardware specs for people who want to help me and know what they are looking for [http://survey4free.co.cc/hardinfo_report.html](http://survey4free.co.cc/hardinfo_report.html) (ignore the domain; its for a landing page I use)

more info:
```
running lastest xbuntu
latest sdl
using microatx (i think) motherboard (jet somthing)
using built-in graphics card
disabled screen saver
only pulselib0 is installed
```loading sauerbraten:
```
Using home directory: /home/izack/.sauerbraten
init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: Mesa DRI UniChrome 20060710 x86/MMX/SSE2 (VIA Technology)
Driver: 1.2 Mesa 7.4
WARNING: No framebuffer object support. (reflective water may be slow)
WARNING: No occlusion query support! (large maps may be SLOW)
WARNING: No cube map texture support. (no reflective glass)
WARNING: Non-power-of-two textures not supported!
WARNING: No shader support! Using fixed-function fallback. (no fancy visuals for you)
Rendering using the OpenGL 1.5 fixed-function path.
init: console
init: gl: effects
init: world
init: sound
init: cfg
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.3 seconds)
Mining Station by metlslime
game mode is ffa/default
Segmentation fault
```extreme tux racer worked

alien arena got me this:
```
using /home/izack/.alien-arena/data1/ for writing
using /home/izack/.alien-arena/arena/ for writing
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 22050
------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting fullscreen mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
GL_VENDOR: VIA Technology
GL_RENDERER: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
GL_VERSION: 1.2 Mesa 7.4
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_APPLE_packed_pixels GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
...allowing CDS
...enabling GL_EXT_compiled_vertex_array
...ignoring GL_EXT_point_parameters
...3DFX_set_global_palette not found
...GL_EXT_shared_texture_palette not found
...using GL_ARB_multitexture
...GL_SGIS_multitexture not found
...using GL_ARB_texture_env_combine
...GL_NV_texture_shader not found
...GL_ARB_fragment_program not found
------------------------------------
======== CRX Initialized ========

------- Loading game.so -------
LoadLibrary (./arena/game.so)
==== InitGame ====
Master server at 74.63.48.146:27900
Sending a ping.
------- Server Initialization -------
name is not a field
name is not a field
name is not a field
name is not a field
0 entities inhibited
0 teams with 0 entities
-------------------------------------
Ping acknowledge from 74.63.48.146:27900
Player connected
Sending heartbeat to 74.63.48.146:27900
0.0.0.0:0: client_connect
Ping acknowledge from 74.63.48.146:27900
game will be changed for next game.




Dismal Outpost
Received signal 11, exiting...
```Glest (huh, i thought this game worked on moonos; this seems to be an unrelated problem anyways...)
```
Exception: Your system supports OpenGL version "1.2 Mesa 7.4"
Glest needs at least version 1.3 to work
You may solve this problem by installing your latest video card drivers
```supertux kart(worked for a little bit until it froze):
```
ata files will be fetched from: '/usr/share/games/supertuxkart/'
Highscores will be saved in '/home/izack/.supertuxkart/highscore.data'.
WARNING: Music not playing when it should be. Source state: 4116
Killed
```so any help would be much appreciated (what to do I do now?)

---

### Post by u235sentinel on 2009-10-20
> **izackrp said:**
> So far I tried to run open arena and super tux kart both freeze and at (sort of) random places. OA freezes during the menus, ingame (usually within a few seconds), and when bring the menu up during the game. From the command line (after terminating the game) it said some stuff about not loading skins and returned exit code 15.


Dismal Outpost
Received signal 11, exiting...[/code]Glest (huh, i thought this game worked on moonos; this seems to be an unrelated problem anyways...)
```
Exception: Your system supports OpenGL version "1.2 Mesa 7.4"
Glest needs at least version 1.3 to work
You may solve this problem by installing your latest video card drivers
```supertux kart(worked for a little bit until it froze):
```
ata files will be fetched from: '/usr/share/games/supertuxkart/'
Highscores will be saved in '/home/izack/.supertuxkart/highscore.data'.
WARNING: Music not playing when it should be. Source state: 4116
Killed
```so any help would be much appreciated (what to do I do now?)

maybe I missed it but what video card are you running?  I didn't see it in the config file you published.

If it's an ATI card then perhaps you should try an Nvidia.  I've had lots of problems with ATI cards over the years and buy only Nvidia these days.

Just a thought.

---

### Post by hikaricore on 2009-10-20
The "video" hardware is probably intel.
If you notice they're using the mesa.

Would you mind giving more info about your hardware?

---

### Post by izackrp on 2009-10-20
I believe I have a mini-itx Jetway J7F2WE-1G2E mainboard which consists of 2 chipsets
VIA CN700 North Bridge Chipset
VT 8237RP South Bridge Chipset

Thanks for the effort :KS

btw I don't think i have slots for more (or different) video cards. + it would be more money then its worth ><

> If it's an ATI card then perhaps you should try an Nvidia. I've had lots of problems with ATI cards over the years and buy only Nvidia these days.I'll keep this in mind.

**Edit**

Also, want to add that 
battletanks froze at options menu.
opencity worked.. slow but didn't crash :D
oolite appears to work cant really play cause my keyboard is far away from me ><
scorched3d: I can get to the main menu on normal settings after a few seconds it freezes
snowballz: can't load - AttributeError: 'NoneType' object has no attribute '__name__'
simutrans: works
spaceorbit: window all of a sudden turns transparent and becomes non-playable (no errors showed up, game still runs)
after killing spaceorbit, any window that gets dragged into the same place the game was before turns transparent and messed up (had to restart)

---

### Post by izackrp on 2009-10-27
So, I decided to experiment with the drivers. Apparently I'm using something called openchrome, so I go to the via website, get, and install the drivers for the cn700 chipset (which is a VIA Unichrome Pro).

Well I restart linux, and there is loads of stuff telling me I have to run in low graphics mode. Which I did, then I decided to run open arena. Obviously it was going to be slow, but I wanted to see if OA froze at all. Guess what? I let it run for 20 minutes and it didn't freeze! Anyways, I restart hit some recover button, but everything is still slow. So, I uninstalled the via driver. Everything goes back to normal speed. Then tried OA it froze...

So apparently
1) I have the wrong driver, or the driver is incompatible, and/or
2) Some sort of settings is wrong

so if anyone can shed some light?

perhaps there is an openchrome alternative? 

adding/changing these lines in the xorg.conf stops the freezing but games are ultra slow
```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "openchrome"
EndSection

Section "Module"
    Disable        "dri"
EndSection
```

---

