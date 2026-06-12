---
title: "World of Padman loading problem"
date: 2007-05-09
forum: Gaming &amp; Leisure
---

### Post by cisforcojo on 2007-05-09
Hey guys,

I've just installed World of Padman, the intro, menu, everything work fine up until I load the game to play.
Then it seems to never stop. I've never let it go on for more than 2 minutes but that seems REALLY excessive. I have a 1.7GHz system with an ATI Mobility Radeon X600 (128MB) and 512MB RAM. I have to manually power off my system (hate doing it) and can't get any sort of feedback because of it! Any ideas??

---

### Post by Bekker on 2007-05-09
Hi,

I have some suggestions: First let it load for a bit longer, one to two minutes is about the load time I get on my system. Does the load bar show any progress when loading?

I don't know how much effect the speed of the internet connection has on the loading time, but you should at least try to connect to a server with a low ping (under 100ms).

If you really hate powering of manually, press alt+ctrl+F1 all together. This will throw you into a terminal only enviroment, don't worry. Enter your username and password when prompted then enter ```
ps -ax | grep wop
```
This will give you some output with each line starting with a process number and ending with the name of the process. You are looking for something like wop_engine (probably the only line of output). Enter
```
sudo kill *process number for wop_engine*
```
Finally enter ```
exit
```
and use alt+ctrl+F7 to get back to your regular desktop.

Good luck

---

### Post by cisforcojo on 2007-05-11
I had forgotten how to do the Alt-Cntrl-F1 thing to switch to another terminal!

Alas, it didn't work. I let Padman load for 10 minutes. Nothing. There's no activity from my hard drive after about 10 seconds. And Cntrl-Alt-F1 does nothing, Cntrl-Alt-Bksp and Cntrl-Alt-Del also do nothing. I have to physically shut it off.

---

### Post by hikaricore on 2007-05-12
This won't solve your padman problem.  But if in case of a solid lockup, your only choice is a power off, you might want to remeber that [Raising Skinney Elephants Is Utterly Boring]("http://http://en.wikipedia.org/wiki/Raising_Skinny_Elephants_Is_Utterly_Boring").

---

### Post by cisforcojo on 2007-05-12
hikaricore - that is fantastic!

I had no idea that button (SysRq) even existed!

EDIT: I'm really not having ANY luck. Beyond the Red Line crashes (complains about GART memory)
and this other game Lost Labyrinth (or something...) I can't read the HOWTO so I dunno what the controls are, but it actually looks pretty good!
I've been trying to get Vega Strike but my downloads often timeout (China's internet isn't very good).

---

### Post by cisforcojo on 2007-05-19
Bump! Please if anyone knows anything or knows of a way I could check to see what is causing the problem, I'd love to know.

---

### Post by houstonbofh on 2007-05-19
What games run successfully?  Can you run RTCW:ET?  Urban Terror?

---

### Post by cisforcojo on 2007-05-20
Warsow and Vega Strike run fine. 

Just have problems with Padman and BtRL.

Never tried Enemy Territory or Urban Terror.

---

### Post by houstonbofh on 2007-05-21
Padman, RTCW:ET and Urban Terror are all ID based games.  Warsow and Vega are not.  I would suggest following the howto at [http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php) to install RTCW:ET and see if it gives you hints on padman.  I do not know of a similarly well written howto for padman.

---

### Post by hobieone on 2007-05-21
you install padman  with linix installer from ther website?  just curious onmy system it instaled and runs fine  but did lock up my system like yours that happened when i had the desktop effects turnned on. i notice with the desktop effects on it messes with iother games also but when you turn it off they run normally. so i check to see if you have that turned on and if you use beryl and compiz shut them off as well  when playing games those tend to fight the games over system resources causing lockups and such at least with nvidia cards

---

### Post by cisforcojo on 2007-05-22
Trying RTCW now. I'll let you know how it goes.

I don't have Beryl turned on, I know about that problem. I actually have permanently disabled Beryl. It made my system unstable and messed with too much. Some Java apps wouldn't display, videos wouldn't show right. Not worth the hassle. I'll wait until it's more developed.

---

### Post by cisforcojo on 2007-05-24
Return to Castle Wolfenstein works fine. After 5 minutes, it exits with a signal 11 error but that's a different problem. Padman, I have no idea.

---

### Post by houstonbofh on 2007-05-24
OK.  It could be the startup animation.  Do you have the typical codecs installed?

---

### Post by cisforcojo on 2007-05-25
Well, I'd like to say yes. I haven't had any problems playing videos (except for with Totem under Beryl.) I just got rid of Beryl and switched completely to MPlayer. I can play .wmv, .avi no problem. Btw, I can NEVER see any online games. I always have to 'create' one to test it out. I'm not sure if this is because I live in China and they've blocked the address or what. But even creating the game I can't do it. Come to think of it, the problem could potentially come from trying to connect with the WoP server and not being able to???

---

### Post by houstonbofh on 2007-05-25
I doubt that is it, as I can play with bots and no network at all.  As to the codecs, mplayer uses it's own built in codecs.  You may need to install more.  Here is a short script I wrote for feisty to install a lot of stuff I want.  Edit as you see fit, but somehow make sure you have the codecs.
```

#!/bin/sh
# Ubuntu Update Script (Feisty)
#
# This is a script to update a default install to 
# a fully functional system. Most things are automated,
# but a few things still need to be done by hand.
#
# NTP Config
# Set the clock to update automatically from
# us.pool.ntp.org
#
# Note: Sudo must be enabled for this to work.
# (Type 'sudo ls' and the passowrd before running
# this script)
#

# Add extra repositories

# Medibuntu
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

# Wine HQ
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

# Refresh repositories
sudo apt-get update

# Install everything

sudo apt-get install ssh traceroute p7zip unace rar xfonts-intl-european flashplugin-nonfree sun-java5-plugin faad ffmpeg gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse lame liba52-0.7.4 libartsc0 libdc1394-13 libdvdread3 libfaac0 libfaad2-0 libgsm1 libid3tag0 libimlib2 liblame0 libmad0 libmjpegtools0c2a libmms0 libmodplug0c2 libmp4v2-0 libmpcdec3 libmpeg2-4 liboggflac3 libquicktime0 libsidplay1 libswfdec0.3 libxine-extracodecs libxine-main1 libxvidcore4 libxvmc1 mjpegtools ntp ntp-simple sox vorbis-tools libdvdcss2 w32codecs msttcorefonts ogle-mmx ogle-gui streamtuner streamripper

```

---

### Post by cisforcojo on 2007-05-26
That script is really good, thanks!

I have good news and bad news. Before, the loading would seem to hang at 15% or so. Now the loading bar loads fully but then does nothing after that bar shows that its fully loaded. =(
I think this is probably the same as before except now the loading bar is accurate.

---

### Post by houstonbofh on 2007-05-27
Run it from a terminal and post the output, please.  At least slow progress is progress!

---

### Post by cisforcojo on 2007-05-27
I can't post the output. It hangs my system. I can't switch terminals, restart X, restart the computer, nothing.
Is there a way I could run it and have it copy output to a file so after I do a hard reboot I can see what happened?

---

### Post by houstonbofh on 2007-05-28
I do not know of one.  However, run the program, and exit from the menue without loading a game.  That will give you a screen to post and compare.
```

user@system:~$ wop
WoP 1.1 (1.33_SVN43M) linux-i386 Mar 28 2007
----- FS_Startup -----
Current search path:
/home/user/.WoPadman/wop
/usr/local/games/WoP/wop/wop_vms.pk3 (4 files)
/usr/local/games/WoP/wop/wop_005.pk3 (2558 files)
/usr/local/games/WoP/wop/wop_004.pk3 (698 files)
/usr/local/games/WoP/wop/wop_003.pk3 (187 files)
/usr/local/games/WoP/wop/wop_002.pk3 (1341 files)
/usr/local/games/WoP/wop/wop_001.pk3 (499 files)
/usr/local/games/WoP/wop

----------------------
5287 files in pk3 files
execing default.cfg
execing wop_config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 6: 1024 768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 6600 GT/AGP/SSE2
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6600 GT/AGP/SSE2
GL_VERSION: 2.0.2 NVIDIA 87.76
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_gpu_program_parameters GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/pad_ddmix.shader'
...loading 'scripts/pad_glowsky.shader'
...loading 'scripts/pad_glowsound.shader'
...loading 'scripts/pad_harmsky.shader'
...loading 'scripts/pad_harm.shader'
...loading 'scripts/pad_flare.shader'
...loading 'scripts/pad_wop.shader'
...loading 'scripts/q3map2_wop_dinerbb.shader'
...loading 'scripts/q3map2_wop_diner.shader'
...loading 'scripts/pad_bath.shader'
...loading 'scripts/pad_jail.shader'
...loading 'scripts/glowstar.shader'
...loading 'scripts/grtrees.shader'
...loading 'scripts/padmod_keyboard.shader'
...loading 'scripts/pad_glowstar_nb.shader'
...loading 'scripts/pad_mousetrap.shader'
...loading 'scripts/pad_sunflower.shader'
...loading 'scripts/pad_trash.shader'
...loading 'scripts/q3map2_wop_kaistrashmap.shader'
...loading 'scripts/ente.shader'
...loading 'scripts/pad_liquidfx.shader'
...loading 'scripts/pad_maps.shader'
...loading 'scripts/pad_attic.shader'
...loading 'scripts/pad_bookroom.shader'
...loading 'scripts/pad_garden.shader'
...loading 'scripts/pad_kitchen.shader'
...loading 'scripts/pad_shipcurves.shader'
...loading 'scripts/pad_cyb.shader'
...loading 'scripts/pad_gardencurves.shader'
...loading 'scripts/pad_cryduck.shader'
...loading 'scripts/pad_pirate.shader'
...loading 'scripts/padcar_nascars.shader'
...loading 'scripts/padfigures.shader'
...loading 'scripts/pad_petesky.shader'
...loading 'scripts/pad_tex02.shader'
...loading 'scripts/pad_enteflare.shader'
...loading 'scripts/wopsa_mapmodels.shader'
...loading 'scripts/white.shader'
...loading 'scripts/wop_surfacesounds.shader'
...loading 'scripts/wopascii.shader'
...loading 'scripts/biopad.shader'
...loading 'scripts/blood_screen.shader'
...loading 'scripts/boaster.shader'
...loading 'scripts/bookend.shader'
...loading 'scripts/code.shader'
...loading 'scripts/common.shader'
...loading 'scripts/forcode.shader'
...loading 'scripts/gummybears.shader'
...loading 'scripts/icons.shader'
...loading 'scripts/lfsprites.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/puppetmaster.shader'
...loading 'scripts/pad_armour.shader'
...loading 'scripts/pad_balloonbox.shader'
...loading 'scripts/pad_balloony.shader'
...loading 'scripts/pad_betty.shader'
...loading 'scripts/pad_boaster.shader'
...loading 'scripts/pad_bubbleg.shader'
...loading 'scripts/pad_cake.shader'
...loading 'scripts/pad_condiments.shader'
...loading 'scripts/pad_console.shader'
...loading 'scripts/pad_cups.shader'
...loading 'scripts/pad_cutlery.shader'
...loading 'scripts/pad_ducks.shader'
...loading 'scripts/pad_effect.shader'
...loading 'scripts/pad_fish.shader'
...loading 'scripts/pad_flowerfx.shader'
...loading 'scripts/pad_gfx02.shader'
...loading 'scripts/pad_gfx02b.shader'
...loading 'scripts/pad_gfx.shader'
...loading 'scripts/pad_healthstation.shader'
...loading 'scripts/pad_imperius.shader'
...loading 'scripts/pad_killerduck.shader'
...loading 'scripts/pad_lamps.shader'
...loading 'scripts/pad_marblefx.shader'
...loading 'scripts/pad_nipper.shader'
...loading 'scripts/pad_openbook.shader'
...loading 'scripts/pad_pumper.shader'
...loading 'scripts/pad_punchy.shader'
...loading 'scripts/pad_splasher.shader'
...loading 'scripts/pad_steps.shader'
...loading 'scripts/pad_teleporter.shader'
...loading 'scripts/pad_tft.shader'
...loading 'scripts/pad_waterbottle.shader'
...loading 'scripts/pad_weaponmarker.shader'
...loading 'scripts/pad_weaponsfx2.shader'
...loading 'scripts/pad_weaponsfx.shader'
...loading 'scripts/padgold_statue.shader'
...loading 'scripts/paditems.shader'
...loading 'scripts/padmodel.shader'
...loading 'scripts/padra.shader'
...loading 'scripts/padrock.shader'
...loading 'scripts/padskin_winner_statue.shader'
...loading 'scripts/padsoldier.shader'
...loading 'scripts/padtv.shader'
...loading 'scripts/pelvis.shader'
...loading 'scripts/simplemenubg.shader'
...loading 'scripts/spraymode.shader'
...loading 'scripts/spraypistol.shader'
...loading 'scripts/stonepad.shader'
...loading 'scripts/superpad.shader'
...loading 'scripts/pad_gtb_misc.shader'
...loading 'scripts/pad_spiegelboden.shader'
...loading 'scripts/bblevelshots.shader'
...loading 'scripts/sometestlogos.shader'
trying sun.TGA...
----- finished R_Init -----
------ Initializing Sound ------
Initializing SDL audio driver...
SDL audio driver is "alsa".
SDL_AudioSpec:
  Format:   AUDIO_S16LSB
  Freq:     22050
  Samples:  512
  Channels: 2
Starting SDL audio callback...
SDL audio initialized.
----- Sound Info -----
    1 stereo
16384 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x8b82818 dma buffer
No background file.
----------------------
Sound initialization successful.
--------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm...
...which has vmMagic VM_MAGIC_VER2
Loading 1243 jump table targets
VM file ui compiled to 749518 bytes of code
ui loaded in 1451936 bytes on the hunk
[WoP Music] Playing "gon 2"
12 arenas parsed
51 bots parsed
searching SprayLogos(jpg):
finished searching ... found 0 logos(jpg)
searching SprayLogos(tga):
Logo:0 Name:38_padgirl
Logo:1 Name:39_greensun
Logo:2 Name:40_dog
Logo:3 Name:41_vendetta
Logo:4 Name:42_water
Logo:5 Name:01_wop
Logo:6 Name:02_cross
Logo:7 Name:03_smile
Logo:8 Name:04_padman
Logo:9 Name:05_fish
Logo:10 Name:06_finger
Logo:11 Name:07_skull
Logo:12 Name:08_clowns
Logo:13 Name:09_sketch
Logo:14 Name:10_yinyan
Logo:15 Name:11_splash
Logo:16 Name:12_heart
Logo:17 Name:13_questman
Logo:18 Name:14_badboy
Logo:19 Name:15_padlogo
Logo:20 Name:16_moon
Logo:21 Name:17_exp
Logo:22 Name:18_padbunny
Logo:23 Name:19_jason
Logo:24 Name:20_quake3
Logo:25 Name:21_apple
Logo:26 Name:22_lips
Logo:27 Name:23_alien
Logo:28 Name:24_hand
Logo:29 Name:25_hairspray
Logo:30 Name:26_spooky
Logo:31 Name:27_ugly
Logo:32 Name:28_moddb
Logo:33 Name:29_pqcom
Logo:34 Name:30_dieselkopf
Logo:35 Name:31_atom
Logo:36 Name:32_padarmy
Logo:37 Name:37_devilskull
finished searching ... found 38 logos(tga)
searching LensFlare-scripts:
Script:0 Name:test
Script:1 Name:photoshop
finished searching ... found 2 scripts
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost
Alias: boat.dnsalias.net
Alias: boat
Alias: nasioc.us.intellitxt.com
Alias: toms.us.intellitxt.com
Alias: boat
Alias: boat.dnsalias.net
IP: 127.0.0.1
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
Shutdown tty console
user@system:~$ 

```

---

### Post by cisforcojo on 2007-05-28
Solved it. The problem was a simple one. I'm a jackass.
I wasn't using fglrx (I have an ATi card)

I followed a Beryl HOWTO way back in the day and that had me use the 'radeon' driver, not fglrx. It had direct rendering (but the performance was generally poor). Switching to fglrx fixed problems with Penumbra Overture so I thought maybe, just maybe, it'll fix this. It did. 

Thanks for all your help! The game looks sick!

---

### Post by houstonbofh on 2007-05-30
> **cisforcojo said:**
> Thanks for all your help! The game looks sick!

Anytime.  And it is!  :biggrin:

---

