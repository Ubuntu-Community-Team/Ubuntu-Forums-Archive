---
title: "Why is Doom 3 Running Like a Slug?"
date: 2007-01-02
forum: Gaming &amp; Leisure
---

### Post by rekahsoft on 2007-01-02
Hi all, i have bought Doom 3 a long time ago and have switched to linux some time ago (about a year ago) but have not played the game since my graphics card drivers (fglrx) were messed. Now i have them working and i have installed Doom 3 correctly using my cd's but when i boot it up it runs very slow and slugish and when i get the main menu the mouse movement is very slow not to mention the fact that mars in the background is messy. Note that the sound runs fine and my computer meets the Doom 3 requirments. Here is the output when i run Doom 3 from terminal:```
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.2.168/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/collin/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
execing DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: RADEON XPRESS Series Generic
GL_EXTENSIONS: GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ARB_draw_buffers GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_blend_square GL_NV_occlusion_query GL_NV_texgen_reflection GL_SGI_color_matrix GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.11
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5461 frames ( 65532 bytes )
allocated a mix buffer of 49152 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
...using GL_ATI_separate_stencil
...using GL_ATI_fragment_shader
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
GL_NUM_FRAGMENT_REGISTERS_ATI: 6
GL_NUM_FRAGMENT_CONSTANTS_ATI: 8
GL_NUM_PASSES_ATI: 2
GL_NUM_INSTRUCTIONS_PER_PASS_ATI: 8
GL_NUM_INSTRUCTIONS_TOTAL_ATI: 16
GL_COLOR_ALPHA_PAIRING_ATI: 1
GL_NUM_LOOPBACK_COMPONENTS_ATI: 3
GL_NUM_INPUT_INTERPOLATOR_COMPONENTS_ATI: 3
FPROG_FAST_PATH
---------------------
---------- R_ARB2_Init ----------
Available.
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfp
glprogs/test.vfp
glprogs/interaction.vfp
glprogs/interaction.vfp
glprogs/bumpyEnvironment.vfp
glprogs/bumpyEnvironment.vfp
glprogs/ambientLight.vfp
glprogs/ambientLight.vfp
glprogs/shadow.vp
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
found DLL in pak file: /usr/local/games/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/collin/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: May 10 2005
Initializing event system
...472 event definitions
Initializing class hierarchy
...142 classes, 381376 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 2200 MHz
Compiled 'removeInitialSplineAngles': 1554.9 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67866, 1357320 bytes
   Functions: 2108, 250452 bytes
   Variables: 147244 bytes
    Mem used: 2478772 bytes
 Static data: 2277552 bytes
   Allocated: 3284208 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
--- Common Initialization Complete ---
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 4839
752 MB System Memory
128 MB Video Memory
Async thread started
--------- Game Map Shutdown ----------
--------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------
shutdown terminal support
```Now the question is why is Doom 3 running so slow and how do i fix it.

---

### Post by Ferrat on 2007-01-02
run fglrxinfo and say what the output says

---

### Post by rekahsoft on 2007-01-02
> **Ferrat said:**
> run fglrxinfo and say what the output says

i do have fglrx working. here is my output from fglrx info:```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)
```

---

### Post by rekahsoft on 2007-01-05
Anybody? I can upload some images if they help...what is the problem...it is definitly not sound...the graphics just move extremely slow...i fullfill all the requirements of the game (128mb Accelerated gpu, 2.2ghz processor, and 752mb of RAM.

---

### Post by Lord Illidan on 2007-01-05
> **rekahsoft said:**
> Anybody? I can upload some images if they help...what is the problem...it is definitly not sound...the graphics just move extremely slow...i fullfill all the requirements of the game (128mb Accelerated gpu, 2.2ghz processor, and 752mb of RAM.

Do you have Windows installed? Does it play on it?

---

### Post by rekahsoft on 2007-01-05
When i did have windows installed (about a year ago since i touch that garbage :)) and it worked fine.

---

### Post by Lord Illidan on 2007-01-05
> **rekahsoft said:**
> When i did have windows installed (about a year ago since i touch that garbage :)) and it worked fine.

Then I'd say either your Linux drivers are not working as they should or else I dunno. Doom 3 is in opengl, and ATI sucks at it.

EDIT : And I quote : [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)

> ATI's Proprietary Linux Drivers (fglrx) version 3.14.6 and up will run DOOM3. Download fglrx from [[IMG]http://zerowing.idsoftware.com/wiki/modern/img/moin-www.png[/IMG] http://www.ati.com/support/drivers/linux/radeon-linux.html]("http://www.ati.com/support/drivers/linux/radeon-linux.html"). 
 The DRI drivers for ATI cards may run the game with some tweaking ( you need to apply the S3TC patch for instance ). But the rendering quality will be sub-optimal, as a number of important graphic features are not available in the DRI drivers.


---

### Post by rekahsoft on 2007-01-05
well i know for a fact that DRI is working as seen by this:```
glxinfo | grep direct
direct rendering: Yes
```and yes ATI is very very bad at it :'(

Edit: Could it be something with OpenGL?

---

### Post by rekahsoft on 2007-01-06
ok so is it fglrx and its bad support for OpenGL? Can i get it working with a patch for fglrx? Is anybody running Doom 3 with an ATI card with the fglrx drivers?

---

### Post by rekahsoft on 2007-01-08
> **rekahsoft said:**
> ok so is it fglrx and its bad support for OpenGL? Can i get it working with a patch for fglrx? Is anybody running Doom 3 with an ATI card with the fglrx drivers?

Anybody?

---

### Post by jdong on 2007-01-09
You have a radeon Xpress integrated graphics solution; that's likely not fast enough to run Doom 3.

---

### Post by rekahsoft on 2007-01-09
> **jdong said:**
> You have a radeon Xpress integrated graphics solution; that's likely not fast enough to run Doom 3.

Works in windows

---

### Post by sourchier on 2007-01-21
have you tried any of the tweaks mentioned on this url:
[http://www.megagames.com/news/html/pc/doom3enhancetheexperiencept2.shtml](http://www.megagames.com/news/html/pc/doom3enhancetheexperiencept2.shtml)

---

### Post by rekahsoft on 2007-01-21
> **sourchier said:**
> have you tried any of the tweaks mentioned on this url:
[http://www.megagames.com/news/html/pc/doom3enhancetheexperiencept2.shtml](http://www.megagames.com/news/html/pc/doom3enhancetheexperiencept2.shtml)

just tried it and it did nothing :(

---

### Post by jdong on 2007-01-21
You have to realize that the Radeon Xpress is one of fglrx's worst-maintained chipsets to this point, and fglrx's performance is markedly worse than the Windows Catalyst drivers to begin with...

---

### Post by rekahsoft on 2007-01-21
> **jdong said:**
> You have to realize that the Radeon Xpress is one of fglrx's worst-maintained chipsets to this point, and fglrx's performance is markedly worse than the Windows Catalyst drivers to begin with...

awesome (sarcastic) :(

---

### Post by jdong on 2007-01-21
yeah, tell me about it. but I do have good news... I just saved a bunch of money on my car insurance! :)

---

### Post by rekahsoft on 2007-01-21
> **jdong said:**
> yeah, tell me about it. but I do have good news... I just saved a bunch of money on my car insurance! :)

lol :D
Next video card i get will be nvidia for sure...or intel...

---

### Post by rekahsoft on 2007-01-27
So to close up this thread....is there anyway to run Doom 3 with a Radeon 200M Xpress using fglrx 8.33.6 at the time of this writing?

---

### Post by jdong on 2007-01-27
What we said is what we meant. On Linux Doom3 on your card will run very slowly at even the lowest settings because:

(1) Speaking on a computational power perspective, that wimpy integrated card is BARELY enough to power Doom3 at the lowest settings factoring out all software variables.

(2)ATI's fglrx driver performs miserably worse than their Windows drivers on the identical cards.

---

### Post by rekahsoft on 2007-01-27
> **jdong said:**
> What we said is what we meant. On Linux Doom3 on your card will run very slowly at even the lowest settings because:

(1) Speaking on a computational power perspective, that wimpy integrated card is BARELY enough to power Doom3 at the lowest settings factoring out all software variables.

(2)ATI's fglrx driver performs miserably worse than their Windows drivers on the identical cards.

OK...well, i will never install windows so i guess i can do without the games...i very, very rarely play games anyways...i would rather code, read about coding, or read about math :)

---

### Post by retrorob on 2007-02-16
I have this same issue with a Radeon Express 1100.
I doubt it is a hardware issue as such as I can run Half-Life 2 cranked at 1280 X 800 .
I don't really care for the "blame the wimpy hardware" attitude of some Linux users (Note that I only use windows at work, I run a Linux household). If it works in Windows, it should work in Linux as fast if not faster.
I agree that something smells in the ATI Linux driver world. I wish they would put out a little more effort.

If anyone has had this problem and has some constructive help, could you let everyone know?

---

### Post by jdong on 2007-02-16
It was not my intention to totally blame hardware on this.... You've hit the nail on the head as far as blame goes -- ATI's Linux drivers perform significantly worse than their Windows drivers.... At this point there are open source projects (DRI) trying to rectify this but progress is not exactly blazingly fast.

Wish I could do more to help :(

---

### Post by retrorob on 2007-02-16
Just as a couple quick notes on this (quick apology to jdong: the post was more terse then I meant to be - :) )

I am now running the latest ATI 8.33.06 driver with no improvement.

I did notice that the Radeon Xpress 1100 is not listed in the supported cards, Maybe a future version will work a little better . 

Accel. is working, and generally works well in most games. 

Has anyone tried running this in WINE ?? If its not too painful maybe I will try it out there.

Also, the Tenebrae version of Quake has the same ripping effect, although I can run GLQuake and Quake 2 native without issue.

I think this has something to do with the lighting or shadows.

---

### Post by retrorob on 2007-02-24
OK, I have a solution that will significantly speed up Doom3 on Radeon Express based cards and get rid of that nasty tearing.

The game will look OK, but nothing like if ATI straightened out their drivers.

Start the game and get into the console by hitting the Ctrl, Alt, and  ~ keys all at the same time.
type:
 r_renderer ARB

and hit enter. This will switch to world's crappiest Doom3 renderer, but it's way better than the default for us Radeon Express sufferers.  You can tweak it out after to get a "decent" frame rate and graphics quality.

You can exit the console the same way you got in.


Extra note: there is a specific R200 renderer, but it was still crap on my 1100, if you want to try it change the renderer to r_renderer R200.


Happy Gaming!

---

### Post by rekahsoft on 2007-02-24
> **retrorob said:**
> OK, I have a solution that will significantly speed up Doom3 on Radeon Express based cards and get rid of that nasty tearing.

The game will look OK, but nothing like if ATI straightened out their drivers.

Start the game and get into the console by hitting the Ctrl, Alt, and  ~ keys all at the same time.
type:
 r_renderer ARB

and hit enter. This will switch to world's crappiest Doom3 renderer, but it's way better than the default for us Radeon Express sufferers.  You can tweak it out after to get a "decent" frame rate and graphics quality.

You can exit the console the same way you got in.


Extra note: there is a specific R200 renderer, but it was still crap on my 1100, if you want to try it change the renderer to r_renderer R200.


Happy Gaming!

Very clever :D Doom 3 now works but it is not as fast as it should be...darn ATI and thier horrable driver :'( Thanks for the time tho... :D

---

### Post by PrimoTurbo on 2007-02-25
LOL, I wouldn't expect a on board video card to run doom3 period.

---

### Post by rekahsoft on 2007-02-25
> **PrimoTurbo said:**
> LOL, I wouldn't expect a on board video card to run doom3 period.

It worked fine in windows...but thanks to fglrx and dumb ATI it is not very good in linux :'(

---

### Post by jdong on 2007-02-25
I still find that hard to believe. I know of a lot of midgrade dedicated video cards that run doom3 horribly except at lowest possible resolution and settings.

---

### Post by retrorob on 2007-02-28
> **jdong said:**
> I still find that hard to believe. I know of a lot of midgrade dedicated video cards that run doom3 horribly except at lowest possible resolution and settings.

Like I said before, my Xpress runs HL2 cranked with no problems. Mine is a slightly diff. model though. I have win XP installed on a usb drive around here, I'll install Doom 3 and see if it runs as well as HL2 sometime this weekend and let you know. It may be that it does not work so hot even in XP. I'm pretty sure this is an ATI driver issue though -- I take a 3D performance hit in almost everything in Ubuntu, but I really don't care that much as the stability of it (not to mention the vast amount of free software) makes up for ATI's 3D woes. I'm sure they will catch up sooner or later.

---

### Post by Jason_25 on 2007-02-28
> **retrorob said:**
> Like I said before, my Xpress runs HL2 cranked with no problems. Mine is a slightly diff. model though. I have win XP installed on a usb drive around here, I'll install Doom 3 and see if it runs as well as HL2 sometime this weekend and let you know. It may be that it does not work so hot even in XP. I'm pretty sure this is an ATI driver issue though -- I take a 3D performance hit in almost everything in Ubuntu, but I really don't care that much as the stability of it (not to mention the vast amount of free software) makes up for ATI's 3D woes. I'm sure they will catch up sooner or later.

Since when did integrated cards attain the performance of X800/6800 series cards?  Last time I checked, the best integrated solutions were equal in performance to midrange ati/nvidia desktop cards of 2000 or so.

My friend did insist the same thing to me about his intel graphics.  He claimed it worked better in windows than kubuntu.  But the fact of the matter is integrated hardware (especially intel) is incredibly weak, hundreds of times slower than is needed for modern games.

---

### Post by retrorob on 2007-03-02
OK, while Doom 3 looks a heck of a lot better under Windows, and the speed is much better, I have to say it still pretty much sucks. It lags in some of the open areas, while it is pretty good in the cramped areas. 640 X 480 fares better than 1024 x 768, but not a lot better. I would say in Linux it takes about a 30% performance hit and a big ol' hit with an ugly stick on the graphics.

As far as HL2 goes. On the ATI xpress it's all easy going. I crank that puppy. It shouldn't be that surprising to anyone. The game is a couple years old (I realize Doom 3 is too).  The 1.5gb memory and dual core processor may help a bit, but I'm guessing it does not work the shadow and lighting engine as hard.

Anyway,  the xpress is no gamer's dream chipset, but it can be expected to perform decently in many situations. The point is that the ATI drivers really do suck, and major improvements need to be made before ATI is ready for prime time in linux. My next system will have Nvidia based video as I have read they are in much better shape.

---

### Post by rajeev1204 on 2007-03-03
Hi

i have an integrated geforce 6100 and doom 3 plays fine at 800 *600 medium settings and 512 mb ram , - same in windows and linux. Integrated graphics are not that bad if u have enough ram. I mean 1 GB .


Anyways , i just got a geforce 7600 GT hehe

Also i agree ,with the others here -- iam a gamer and thanks to nvidia iam using linux 64 bit.

Or i would have moved back to windows


regards
rajeev

---

