---
title: "How do i install windows Quake3Arena"
date: 2005-04-05
forum: Gaming &amp; Leisure
---

### Post by OuR_LanD on 2005-04-05
Would someone *please* explain how to install a windows version of Quake 3 Arena on Ubuntu? BTW i am a complete novice/newbie to ubuntu and linux, so i would greatly appreciate it if you explain it simply. Thanks to all who help!

---

### Post by lao_V on 2005-04-05
You can install WINE through synaptic and then install your Quake3Arena

---

### Post by skoal on 2005-04-05
If you want a nice silver collector's tin case from Loki games, you can find Quake III for Linux on eBay for $2.  Since you have the Windows version already, you might be able to just copy over the .pk3 (?) files and use the Linux binary from some ftp site.

---

### Post by clb137 on 2005-04-05
HI,

The only real way to get good gaming performance is to use the following site
[http://www.transgaming.com/](http://www.transgaming.com/)
the main program is called 'cedega'


clinton

---

### Post by OuR_LanD on 2005-04-05
I've gone to ID Softwares ftp site and tried to download the linux install file...

linuxq3apoint-1.32b-3.x86.run

...but all that happens is lots of text and jibberish comes up! is this meant to happen?!? Heres a sample of the text...

#!/bin/sh
# This script was generated using Makeself 2.1.3
CRCsum="2501996906"
MD5="3c4a321e0fd5e5596ea8f703239248c6"
TMPROOT=${TMPDIR:=/tmp}

...and i can't even copy the jibberish. BTW i'm on a widows 98 machine as my ubuntu machine has no access to the net. Someone please help!

---

### Post by skoal on 2005-04-05
[QUOTE=OuR_LanD]I've gone to ID Softwares ftp site and tried to download the linux install file...

linuxq3apoint-1.32b-3.x86.run

...but all that happens is lots of text and jibberish comes up! is this meant to happen?!? [/QUOTE]

You just need to hover your mouse over the link and *right* click "save link as".  That jiberrish stuff is when some websites don't provide a standard download link.  Don't ask me why that happens sometimes.  You call it 'jibberish'.  I call it 'URL puke'.

Never fear - Icculus is [here](http://www.icculus.org/lgfaq/loki/q3faq.html#32)!

---

### Post by crane on 2005-04-06
*** do not mess with wine or cadega for quake3*****



First make a directory /quake3 I made mine in /usr/local/games/quake3
command:
[list]
[*][color=blue]sudo mkdir /usr/local/games/quake3[/color][/list]
the make a directory called baseq3 under the quake3 directory
command
[list]
[*][color=blue]sudo mkdir /usr/local/games/quake3/baseq3[/color][/list]

then put the quake3 "windows version" in cd rom anf copy a file called pak0.pk3 to the newly made baseq3 directory.

command
[list]
[*][color=blue]sudo cp /media/cdrom0/Qauke3/baseq3/pak0.pk3 /usr/local/games/quake3/baseq3/pak0.pk3[/color][/list]

Now you can go to [Cranework.com](http://www.cranework.com) <--- my site, and get the .run file. (but I think you already have it right?)
if not use this command
[list]
[*][color=blue]wget [http://www.cranework.com/Downloads/linux/quake3/linuxq3apoint-1.32b-3.x86.run](http://www.cranework.com/Downloads/linux/quake3/linuxq3apoint-1.32b-3.x86.run)[/color][/list]
or right click and "save as"

OK now
run that file (lets say the file is in my home directory)
command
[list]
[*][color=blue]sudo sh linuxq3apoint-1.32b-3.x86.run[/color][/list]

after the install has completed just exit. (it's not a good Idea to run as root.)
now just type quake3 in your console and the game should run fine.

---

### Post by OuR_LanD on 2005-04-06
Thanks Skoal, my 'URL Puke' problem is gone and now i'm going to give Crane's install instructions a go. I'll post my results when i'm done. Thanks again!  :D

---

### Post by crane on 2005-04-06
A couple other notes that may help.

[list]
[*] after you run quake3 the first time as a user, it will create a hidden file in your home directory called .q3a . This is where your q3config file is and this is where you want to drop any extra config files as well.


 [*]If your going to play online the I would suggest downloading [pbweb.x86](http://www.evenbalance.com/downloads/pbweb.x86) and placing it in your pb file (~/.q3a/pb) then just cd to the file and run it.
command 
[list]
[*][color=blue]chmod +x ~/.q3a/pb/pbweb.x86[/color]   [color=green]<----makes file executable[/color]
[*][color=blue]cd .q3a/pb [/color]                                   [color=green] <---moves to directory[/color] 
[*][color=blue]~/.q3a/pb/pbweb.x86 [/color]                  [color=green] <---executes files[/color]
[/list]
That will update you punkbuster files so you don't have to wait in spectate while trying to play.


[*]also to protect your install and to avoid having to use sudo alot, you can symlink to you home directory.
commands
[list]
[*][color=blue]mkdir /home/jason/quake3[/color] [color=green]<----creates quake3 folder in your home directory[/color]
[*][color=blue]cp -Rs /usr/local/games/quake3/* /home/jason/quake3/ [/color][color=green]<----creates symlinks to game install, simular to windows shortcuts.[/color]
[/list]
Now you can just drop any files in the directories under your home directories (mapfiles, skinpacks, or what ever)
What this does is kinda protects the base install. Should you drop in a few bad pak files the all you have to do is delete the /home/jason/quake3 file and make a new one. because your base install has remained untouched.

[/list]

Good luck and let me know if I can help.

Oh also once you get it running join me and my friends at the House of pain server
in game drop console and type /connect 207.44.248.20:27969

My site (link in sig below) also has a few quake3 maps. you can also get help and answers at [the forums at ASWP](http://forums.aswp.net/) 
There are a few linux people and a bunch of games there and all are nice and friendly. You should drop by and say Hi!!

Let me know if I can help any. :-D

---

### Post by crane on 2005-04-06
he, one other thing. If your running nvidia I have found that sometimes the load dri is still in the xconfig file. this can sometimes cause the system to lag during game play.
Nvidia says to be sure and remove load dri and load glcore from xserver. 
So you may need to comment out load dri.
command
warty = sudo gedit /etc/X11/XF86.Config-4
hoary = sudo gedit /etc/X11/xorg.conf

then look for the following lines and comment out the dri line.
(these lines should be close to the top of the file)


> Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection 

this is mine from my warty install. I just deleted the line but you could comment it out the # <-- this symbol. so it would look like 
#    load "dri"
#    load "glcore"

---

### Post by skoal on 2005-04-06
Shoot! Crane, you're my kind of poster.  I like your style and can appreciate the time you spent with your methodical instructions.

I'm new to these boards and don't know what this "Add to user Reputation" button does.  I assume it's a good thing, so I'm pressing that icon under your post in rapid succesion as if I were on a Q3A server firing off a few BFG rounds...

---

### Post by crane on 2005-04-06
[QUOTE=skoal]Shoot! Crane, you're my kind of poster.  I like your style and can appreciate the time you spent with your methodical instructions.

I'm new to these boards and don't know what this "Add to user Reputation" button does.  I assume it's a good thing, so I'm pressing that icon under your post in rapid succesion as if I were on a Q3A server firing off a few BFG rounds...[/QUOTE]

Thanks, I remember what it was like learning to install Q3 the first time on linux as well. I always remember how nice it was finding a good complete explanation on doing something.
I was just thinking of sitting down and righting a complete how to on installing q3.

Hope it helped some!!

---

### Post by rocket.nz on 2005-04-10
What i want to know and a few of my friends is how to turn off mouse accelaration in quake3 linux. The sencitivity command seems to do nothing asnd even on the lowest setting the mouse is still far to sensitive. Anyone know a way to tweak this? ubuntu desktop mouse speed seems to havew no effect on the mouse ingame.

---

### Post by OuR_LanD on 2005-04-17
Thanks Crane and Skoal, your advice has been rely helpfull!  \\:D/

---

### Post by snark on 2005-05-01
Hi There

Crane your install guide for Quake 3 in excellent. I followed it line by line and for a total Linux newbie It worked perfectly for me except for one thing. Every time I play quake I have to reenter my cdkey and all of my settings are gone.

I assume that it is a permission issue.  Has anyone else had this problem? How can I fix this? Do I need to launch quake as sudo? I thought it better not to have to do that.

Thanks

Snark (the same Snark who plays on ASWP all the time (XP boot))

---

### Post by crane on 2005-05-01
[QUOTE=snark]Hi There

Crane your install guide for Quake 3 in excellent. I followed it line by line and for a total Linux newbie It worked perfectly for me except for one thing. Every time I play quake I have to reenter my cdkey and all of my settings are gone.

I assume that it is a permission issue.  Has anyone else had this problem? How can I fix this? Do I need to launch quake as sudo? I thought it better not to have to do that.

Thanks

Snark (the same Snark who plays on ASWP all the time (XP boot))[/QUOTE]


Hey snark! Good to see ya!

When you launch quake3 as a user, it should create a hidden file called .q3a should be something like /home/snark/.q3a ( the . at the begining of a file means it's a hidden file.) Check the permissions of the .q3a file and it subdirectories. make sure you have the right permissions set. Also is you look in your baseq3 file in the hidden .q3a file ( /home/snark/.q3a/baseq3) You should see a file called q3key. That is the file that holds the key. You could actually create the file yourself.

This id the contents of mine:

> ***************
// generated by quake, do not modify

// Do not give this file to ANYONE.

// id Software and Activision will NOT ask you to send this file to them. 

Where the *'s are just put your key then save as q3key in your /.q3a/baseq3 file.
Oh and make sure you have the right permissions set so you can read it.

if in doubt about permissions just open terminal and enter 
[list]
[*][color=blue]chmod 755 -R ~/.q3a[/color][/list]
or
[list]
[*][color=blue]chmod 700 -R ~/.q3a[/color][/list]

the first one give read, write exec permissions to you (or the owner of the file) and read, exec to group and others.
The second just gives read, write, exec to owner and nothing to everyone else. 

Using the ~ key is a shortcut to your home directory so instead of /home/snark/.q3a you just enter ~/.q3a.
The -R switch means recursive (sp?) so it will change every file and folder beneath .q3a to the same permissions you specify.

---

### Post by snark on 2005-05-02
Hi Crane

Well I Reinstalled Kubuntu because I screwed a few things up. Then I followed your steps again and this time everything worked fine. One thing, took me forever to get pbweb.x86 to execute since I didnt realize I had to chmod it to allow execution first.

In terms of performance, once  I imported all my custom settings from q3config.cfg, I would say that the gameplay is exactly the same feel as in XP.

Thanks a million Crane. See you in ASWP.

snark.

---

### Post by crane on 2005-05-02
[QUOTE=snark]Hi Crane

Well I Reinstalled Kubuntu because I screwed a few things up. Then I followed your steps again and this time everything worked fine. One thing, took me forever to get pbweb.x86 to execute since I didnt realize I had to chmod it to allow execution first.

In terms of performance, once  I imported all my custom settings from q3config.cfg, I would say that the gameplay is exactly the same feel as in XP.

Thanks a million Crane. See you in ASWP.

snark.[/QUOTE]


Cool!!
Thanks for pointing that out about making pbweb.x86 executable. I edited my little how-to to include this fact and how to make it executable.

Thanks \\:D/

---

### Post by snark on 2005-05-05
Hi Crane / Everyone else

Unfortunately I have a problem with quake3 now. 

When I play, the game is jerky. What I mean by this is that it is like there is a half second pause in the game once every 5 seconds. It is extremely annoying.The game was playing perfectly until today, and I have not changed anything that I can think would cause this. Actually I had this problem in Suse 9.2 also.

This problem is not related to graphics settings. Even if I downgrade to the lowest possible settings I still have it.  Also this is on single player as well as online.

Anyone have any idea what might be causing this? I am using the 7174 drivers from nvidia and Kubuntu. Is there a 3d benchmark type app for linux? Maybe I will look in to that.

The game is perfect in XP so I know its not a hardware problem.

Thanks

---

### Post by void_false on 2005-05-05
Dunno if it help but I had similar problem long time ago. It happened for me when my CPU was heavy loaded. It was temperature issue. New cooler solved the problem.

> Is there a 3d benchmark type app for linux? Maybe I will look in to that. 
Type in console glxgears. If you FPS > 1000 it´s good.


1 question. Can I install Q3A on another partition say hda5 (fat32 filesystem - I use it to share files between my w$ and Linux)? The problem is that I have no more free space on my Linux partition (about 200mo left.)?

EDIT:
I´ve tried to install it on /hda5/Q3A. Install went fine but when I type quake3 it says:
```
bash: /usr/local/bin/quake3: /bin/sh: bad interpreter: Permission denied
``` 
Well. I´m thinking of resizing my Linux partition and installing q3a on it.
How can I uninstall my q3a now with single comand and not by deleting file by file?

---

### Post by crane on 2005-05-05
[QUOTE=snark]Hi Crane / Everyone else

Unfortunately I have a problem with quake3 now. 

When I play, the game is jerky. What I mean by this is that it is like there is a half second pause in the game once every 5 seconds. It is extremely annoying.The game was playing perfectly until today, and I have not changed anything that I can think would cause this. Actually I had this problem in Suse 9.2 also.

This problem is not related to graphics settings. Even if I downgrade to the lowest possible settings I still have it.  Also this is on single player as well as online.

Anyone have any idea what might be causing this? I am using the 7174 drivers from nvidia and Kubuntu. Is there a 3d benchmark type app for linux? Maybe I will look in to that.

The game is perfect in XP so I know its not a hardware problem.

Thanks[/QUOTE]

I had this problem as well. Be sure to check you xorg.conf and make sure all the right modules are commented out.

[listl]
[*]sudo gedit /etc/X11/xorg.conf
[/list]

you should see this section:
> Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection 

Make sure there are no modules called dri or glcore.
If there are just comment them out by putting a # in front of the line so it looks like this.

#Load "dri"

Hope this helps.If not try to runnig q3 in terminal ( open terminal and type quake3. Once it starts you could shut it off and see if there were any errors when it loaded.

---

### Post by Smokemare on 2005-05-05
ive been loading q3 as a benchmark for all my fav distro's...

the easiest way ive found is save all your imp stuff to a cd or another pc on your network smb4 see all hehe..

get the latest point release and run it sh 132b-3...............
it makes all the folders for ya then just cp pk3.0 file from any quake3 cd to
/usr/local/games/quake3/baseq3
then go get pbweb from punkbusters site.
make it executable 
then run the game open a terminal type quake3
then shut the game down open your home folder
go to .q3a folder put pb web in the pb folder then close all
then open a terminal cd to .q3a/pb put ./ in front of pbweb so that it updates
now you should be able to go to pb quake3 servers
sometimes when on servers i have to do /pb_sv_enable
then /pb_cl_enable  then /pb_sv_update
 it all sounds hard but taint after a few hundred times hehe and a few hundred distro's :?

---

### Post by snark on 2005-05-06
Hi Guys

Void: GLXGEARS gives me...

41502 frames in 5.0 seconds = 8300.400 FPS

Seems ok to me. By the way, the gears stop spinning every few seconds. Seems to be the same problem.

Crane: I had DRI in the file. I commented it out, rebooted. Did not solve the problem. Console does not show any obvious errors... 

Here is some output from console... sorry about long post!

Thanks!

----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 2: 512 384
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 512x384
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: GeForce 6800 GT/AGP/SSE2
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6800 GT/AGP/SSE2
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(16-bits) Z(16-bit) stencil(0-bits)
MODE: 2, 512 x 384 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 2
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
HACK: using vertex lightmap approximation
Initializing Shaders
...loading 'scripts/ztn3dm2.shader'
...loading 'scripts/ztn3dm1.shader'
...loading 'scripts/zsq3dm6.shader'
...loading 'scripts/zaxxonia.shader'
...loading 'scripts/yog3dm6.shader'
...loading 'scripts/rocketl.shader'
...loading 'scripts/veldrin.shader'
...loading 'scripts/tymo3t2.shader'
...loading 'scripts/lunbase.shader'
...loading 'scripts/evil6_floors.shader'
...loading 'scripts/evil6_lights.shader'
...loading 'scripts/slamp.shader'
...loading 'scripts/tpalace.shader'
...loading 'scripts/thunda3dm2.shader'
...loading 'scripts/thephhortress.shader'
...loading 'scripts/vogt.shader'
...loading 'scripts/teqdm2.shader'
...loading 'scripts/teqdm1.shader'
...loading 'scripts/szq2dm1ish.shader'
...loading 'scripts/syq3dm1.shader'
...loading 'scripts/ktsdm3.shader'
...loading 'scripts/s3t5_tp.shader'
...loading 'scripts/storm3tourney5.shader'
...loading 'scripts/devilpunch.shader'
...loading 'scripts/jerk.shader'
...loading 'scripts/e7.shader'
...loading 'scripts/e7poojpad.shader'
...loading 'scripts/meat_lights.shader'
...loading 'scripts/meat_objects.shader'
...loading 'scripts/meat_pads.shader'
...loading 'scripts/meat_sfx.shader'
...loading 'scripts/meat_stylized.shader'
...loading 'scripts/stei6.shader'
...loading 'scripts/frozen.shader'
...loading 'scripts/stei4_cold.shader'
...loading 'scripts/spwn3dm2.shader'
...loading 'scripts/compsky02.shader'
...loading 'scripts/sparth.shader'
...loading 'scripts/rebelcielo.shader'
...loading 'scripts/rebelpack.shader'
...loading 'scripts/billspace.shader'
...loading 'scripts/sokar3tny1.shader'
...loading 'scripts/thickerthanwater.shader'
...loading 'scripts/el_tele.shader'
...loading 'scripts/sky2.shader'
...loading 'scripts/sokar3dm5.shader'
...loading 'scripts/sokar3dm3.shader'
...loading 'scripts/greywash.shader'
...loading 'scripts/purplenebula.shader'
...loading 'scripts/ban2.shader'
...loading 'scripts/bumptex.shader'
...loading 'scripts/launchbleu.shader'
...loading 'scripts/telemat.shader'
...loading 'scripts/metbri.shader'
...loading 'scripts/metal_rustygrate.shader'
...loading 'scripts/glass1.shader'
...loading 'scripts/sleep.shader'
...loading 'scripts/oak.shader'
...loading 'scripts/ice.shader'
...loading 'scripts/skytown2.shader'
...loading 'scripts/quadmaniac.shader'
...loading 'scripts/mash.shader'
...loading 'scripts/hunter-aurora.shader'
...loading 'scripts/doom-chain.shader'
...loading 'scripts/simetrik.shader'
...loading 'scripts/shortcircuit.shader'
...loading 'scripts/cardigan_skies.shader'
...loading 'scripts/seqdm1.shader'
...loading 'scripts/evil4.shader'
...loading 'scripts/jerky.shader'
...loading 'scripts/scandm1.shader'
...loading 'scripts/binary_arts.shader'
...loading 'scripts/saiko_tourney1a.shader'
...loading 'scripts/saiko_tourney1.shader'
...loading 'scripts/railbitch.shader'
...loading 'scripts/radbitch1.shader'
...loading 'scripts/rsptn_tdm01.shader'
...loading 'scripts/rqm3dm1.shader'
...loading 'scripts/rq3dm3.shader'
...loading 'scripts/rpg3dm2.shader'
...loading 'scripts/rpg3dm1.shader'
...loading 'scripts/woda.shader'
...loading 'scripts/bathbusch.shader'
...loading 'scripts/rdogdm4.shader'
...loading 'scripts/telestecki.shader'
...loading 'scripts/rcglass.shader'
...loading 'scripts/rcfog.shader'
...loading 'scripts/quakerx.shader'
...loading 'scripts/qxdm4.shader'
...loading 'scripts/qxdm4_v2.shader'
...loading 'scripts/nateleaf.shader'
...loading 'scripts/qxdm3.shader'
...loading 'scripts/spynesky.shader'
...loading 'scripts/atomic.shader'
...loading 'scripts/base_floor.shader'
...loading 'scripts/base_light.shader'
...loading 'scripts/base_trim.shader'
...loading 'scripts/common.shader'
...loading 'scripts/ctf.shader'
...loading 'scripts/test.shader'
...loading 'scripts/gothic_wall.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/harley.shader'
...loading 'scripts/andronicus.shader'
...loading 'scripts/q3tbdm4.shader'
...loading 'scripts/empty.shader'
...loading 'scripts/q3shw15.shader'
...loading 'scripts/spotlamp1.shader'
...loading 'scripts/ikbase_sky.shader'
...loading 'scripts/team3.shader'
...loading 'scripts/kit_ngi2.shader'
...loading 'scripts/crucified.shader'
...loading 'scripts/kit_ngi.shader'
...loading 'scripts/evil8_base.shader'
...loading 'scripts/deck-tele.shader'
...loading 'scripts/hub3media.shader'
...loading 'scripts/mars.shader'
...loading 'scripts/evil6_support.shader'
...loading 'scripts/evil6_trims.shader'
...loading 'scripts/finko1.shader'
...loading 'scripts/q3finkodm6_beta.shader'
...loading 'scripts/evil6_walls.shader'
...loading 'scripts/q3dpduel.shader'
...loading 'scripts/q3diffdm1.shader'
...loading 'scripts/dead_simple.shader'
...loading 'scripts/q3chaosdm4.shader'
...loading 'scripts/q3a2.shader'
...loading 'scripts/2thecoretxtset2.shader'
...loading 'scripts/q32thecore_tourney2_floor.shader'
...loading 'scripts/q32thecore_tourney2_fx.shader'
...loading 'scripts/q32thecore_tourney2_trim.shader'
...loading 'scripts/q32thecore_tourney2_wall.shader'
...loading 'scripts/psidm7.shader'
...loading 'scripts/praetoriansky.shader'
...loading 'scripts/praetorian.shader'
...loading 'scripts/powerdive.shader'
...loading 'scripts/polo3dm5.shader'
...loading 'scripts/polo3dm4.shader'
...loading 'scripts/flyingplutonians.shader'
...loading 'scripts/nunukciel04.shader'
...loading 'scripts/platform6.shader'
...loading 'scripts/multiplant.shader'
...loading 'scripts/pjw3dm6.shader'
...loading 'scripts/el_jumppad.shader'
...loading 'scripts/q3map2_pjw3dm5.shader'
...loading 'scripts/pjw3dm5.shader'
...loading 'scripts/pjw3dm2.shader'
...loading 'scripts/pjw3dm2sky.shader'
...loading 'scripts/pjw3dm1.shader'
...loading 'scripts/glass.shader'
...loading 'scripts/painfromspain.shader'
...loading 'scripts/wiebo.shader'
...loading 'scripts/overkill.shader'
...loading 'scripts/egyptsoc.shader'
...loading 'scripts/egypt.shader'
...loading 'scripts/eoshader.shader'
...loading 'scripts/skin2.shader'
...loading 'scripts/e_skin.shader'
...loading 'scripts/q3hht1.shader'
...loading 'scripts/onenight.shader'
...loading 'scripts/obiwanshouse.shader'
...loading 'scripts/emeraldfog.shader'
...loading 'scripts/ikbase_light.shader'
...loading 'scripts/ne.shader'
...loading 'scripts/nexus.shader'
...loading 'scripts/nemesis.shader'
...loading 'scripts/dsi_textures.shader'
...loading 'scripts/mw3compo.shader'
...loading 'scripts/mw3dm1.shader'
...loading 'scripts/mw514.shader'
...loading 'scripts/mrcq3t3.shader'
...loading 'scripts/mrcq3dm2.shader'
...loading 'scripts/mrcleantex.shader'
...loading 'scripts/mrcleantex_3.shader'
...loading 'scripts/mktech.shader'
...loading 'scripts/mksteel.shader'
...loading 'scripts/whjungle_surfaces.shader'
...loading 'scripts/bfp_gothlbig.shader'
...loading 'scripts/bluefreeze.shader'
...loading 'scripts/kanctex_1.shader'
...loading 'scripts/mrcleantex_4.shader'
...loading 'scripts/mkexp.shader'
...loading 'scripts/mkbase_trim.shader'
...loading 'scripts/mkbase_concrete.shader'
...loading 'scripts/mkbase_light.shader'
...loading 'scripts/mkbase_metal.shader'
...loading 'scripts/mkbase_sky.shader'
...loading 'scripts/bensky.shader'
...loading 'scripts/minima.shader'
...loading 'scripts/ch_sky.shader'
...loading 'scripts/kumlamp.shader'
...loading 'scripts/than_industrial.shader'
...loading 'scripts/meat_sky.shader'
...loading 'scripts/meat_tags.shader'
...loading 'scripts/grimdemon.shader'
...loading 'scripts/fang.shader'
...loading 'scripts/warpspider.shader'
...loading 'scripts/violator128.shader'
...loading 'scripts/xanatos.shader'
...loading 'scripts/massacre.shader'
...loading 'scripts/lobo.shader'
...loading 'scripts/dragonito.shader'
...loading 'scripts/cleanerwolf.shader'
...loading 'scripts/catwoman.shader'
...loading 'scripts/goose.shader'
...loading 'scripts/ctftree.shader'
...loading 'scripts/wvwq3dm7.shader'
...loading 'scripts/wvwq3dm3.shader'
...loading 'scripts/jvx1.shader'
...loading 'scripts/psyho.shader'
...loading 'scripts/sweltdm4.shader'
...loading 'scripts/cpm8.shader'
...loading 'scripts/winter.shader'
...loading 'scripts/flares.shader'
...loading 'scripts/decker.shader'
...loading 'scripts/evils_textures5.shader'
...loading 'scripts/uzul3.shader'
...loading 'scripts/unitooldm3_morpheus.shader'
...loading 'scripts/unitooldm3_bouncefloor.shader'
...loading 'scripts/id_clangdark_ow3.shader'
...loading 'scripts/unitooldm3_teleporter.shader'
...loading 'scripts/unitooldm3_trimlight.shader'
...loading 'scripts/nkd_evil5_trim.shader'
...loading 'scripts/nkd_textures_space.shader'
...loading 'scripts/rzq2dm2.shader'
...loading 'scripts/rzq2dm2_pub.shader'
...loading 'scripts/rjldm3.shader'
...loading 'scripts/rjldm3_decals.shader'
...loading 'scripts/rjldm3_fl.shader'
...loading 'scripts/rjldm3_light.shader'
...loading 'scripts/rjldm3_particles.shader'
...loading 'scripts/rjldm2.shader'
...loading 'scripts/rfwq3dm3.shader'
...loading 'scripts/rfwq3dm1.shader'
...loading 'scripts/qfraggel3.shader'
...loading 'scripts/orbplat.shader'
...loading 'scripts/dustball.shader'
...loading 'scripts/tech1soc.shader'
...loading 'scripts/miniman.shader'
...loading 'scripts/lobdm01.shader'
...loading 'scripts/kt_torch.shader'
...loading 'scripts/custom.shader'
...loading 'scripts/mexicano_models.shader'
...loading 'scripts/mexicano.shader'
...loading 'scripts/charon_sky.shader'
...loading 'scripts/mu_slash.shader'
...loading 'scripts/charon_dm4.shader'
...loading 'scripts/charon3dm3.shader'
...loading 'scripts/charon_bio.shader'
...loading 'scripts/charon_dm13.shader'
...loading 'scripts/charon_dm10.shader'
...loading 'scripts/lava.shader'
...loading 'scripts/aetime.shader'
...loading 'scripts/aepyra.shader'
...loading 'scripts/aeneon.shader'
...loading 'scripts/aedm17.shader'
...loading 'scripts/aedesert.shader'
...loading 'scripts/aearcs.shader'
...loading 'scripts/acid3dm3.shader'
...loading 'scripts/acid3tourney3.shader'
...loading 'scripts/13place.shader'
...loading 'scripts/lun3dm4.shader'
...loading 'scripts/lsjg_coop.shader'
...loading 'scripts/lsdm1.shader'
...loading 'scripts/fire_part.shader'
...loading 'scripts/mrcleantex_2.shader'
...loading 'scripts/wallportal_ls.shader'
...loading 'scripts/tls_telep.shader'
...loading 'scripts/lloydmdm2.shader'
...loading 'scripts/lae3dm1.shader'
...loading 'scripts/el_wlight.shader'
...loading 'scripts/evil.shader'
...loading 'scripts/fennk.shader'
...loading 'scripts/lignennk.shader'
...loading 'scripts/mettex.shader'
...loading 'scripts/picnnk.shader'
...loading 'scripts/telepnnk.shader'
...loading 'scripts/kleskocurves.shader'
...loading 'scripts/kilt_texpack02.shader'
...loading 'scripts/khaooohs.shader'
...loading 'scripts/jugulatordm2.shader'
...loading 'scripts/graveyard.shader'
...loading 'scripts/jofliquids.shader'
...loading 'scripts/jofmultiplant.shader'
...loading 'scripts/jofnateleaf.shader'
...loading 'scripts/jofpalms.shader'
...loading 'scripts/terrademoq3.shader'
...loading 'scripts/jex3dm1.shader'
...loading 'scripts/jb3dm2.shader'
...loading 'scripts/jb3dm13.shader'
...loading 'scripts/jaxdm8.shader'
...loading 'scripts/jaxdm6.shader'
...loading 'scripts/jaxdm5.shader'
...loading 'scripts/jaxtourney3.shader'
...loading 'scripts/g1zm0.shader'
...loading 'scripts/hell.shader'
...loading 'scripts/hell_trim.shader'
...loading 'scripts/hell_floor.shader'
...loading 'scripts/hell_lava.shader'
...loading 'scripts/ikzdm1.shader'
...loading 'scripts/ik3dm2.shader'
...loading 'scripts/ik.shader'
...loading 'scripts/hymn_lava.shader'
...loading 'scripts/hymn_floor.shader'
...loading 'scripts/hymn_trim.shader'
...loading 'scripts/skybox2.shader'
...loading 'scripts/hrodm01.shader'
...loading 'scripts/hammer_liquids.shader'
...loading 'scripts/hammer_sky.shader'
...loading 'scripts/hammer_flag.shader'
...loading 'scripts/stratosphere2.shader'
...loading 'scripts/siege.shader'
...loading 'scripts/hammer_trim.shader'
...loading 'scripts/headlamp.shader'
...loading 'scripts/hornylamp.shader'
...loading 'scripts/nightsky.shader'
...loading 'scripts/grendel.shader'
...loading 'scripts/gon2_accel.shader'
...loading 'scripts/gon2.shader'
...loading 'scripts/gonsky.shader'
...loading 'scripts/gon.shader'
...loading 'scripts/flame.shader'
...loading 'scripts/gm3tourney2.shader'
...loading 'scripts/q3map2_gm3tourney2.shader'
...loading 'scripts/gm3tourney1.shader'
...loading 'scripts/ggrdm1_mm.shader'
...loading 'scripts/industrial.shader'
...loading 'scripts/geit3dm6.shader'
...loading 'scripts/geit3dm5.shader'
...loading 'scripts/geitdm11.shader'
...loading 'scripts/sprites.shader'
...loading 'scripts/end.shader'
...loading 'scripts/fiesling.shader'
...loading 'scripts/padfigures.shader'
...loading 'scripts/kitchen.shader'
...loading 'scripts/f_q3dm01.shader'
...loading 'scripts/models.shader'
...loading 'scripts/models2.shader'
...loading 'scripts/models3.shader'
...loading 'scripts/fr3dm1.shader'
...loading 'scripts/stratosphere.shader'
...loading 'scripts/evil4_techtrims.shader'
...loading 'scripts/ik2k_carpet.shader'
...loading 'scripts/fff.shader'
...loading 'scripts/dub_an.shader'
...loading 'scripts/dk_tyger.shader'
...loading 'scripts/mrctele.shader'
...loading 'scripts/flags.shader'
...loading 'scripts/water.shader'
...loading 'scripts/nusky.shader'
...loading 'scripts/dk_lamp.shader'
...loading 'scripts/dk_ttgd.shader'
...loading 'scripts/cel.shader'
...loading 'scripts/dk_ttgd2.shader'
...loading 'scripts/particles.shader'
...loading 'scripts/17+ctf.shader'
...loading 'scripts/dk_pc.shader'
...loading 'scripts/dk_terrains.shader'
...loading 'scripts/dk_bits.shader'
...loading 'scripts/new.shader'
...loading 'scripts/soc_t1light1.shader'
...loading 'scripts/dk_grunge.shader'
...loading 'scripts/lensflare.shader'
...loading 'scripts/sag_globes.shader'
...loading 'scripts/heart.shader'
...loading 'scripts/bmap1.shader'
...loading 'scripts/dk_pink.shader'
...loading 'scripts/dk_bst.shader'
...loading 'scripts/dk_aom.shader'
...loading 'scripts/ban7.shader'
...loading 'scripts/ban8.shader'
...loading 'scripts/ban1.shader'
...loading 'scripts/concrete12.shader'
...loading 'scripts/concrete14.shader'
...loading 'scripts/distonic.shader'
...loading 'scripts/gr5.shader'
...loading 'scripts/rebordbleu.shader'
...loading 'scripts/deadmeat_lights.shader'
...loading 'scripts/deadmeat_liquid.shader'
...loading 'scripts/deadmeat_metal.shader'
...loading 'scripts/deadmeat_objects.shader'
...loading 'scripts/deadmeat_pads.shader'
...loading 'scripts/deadmeat_sky.shader'
...loading 'scripts/deadmeat_tags.shader'
...loading 'scripts/ddq3dm2.shader'
...loading 'scripts/dayve3dm1.shader'
...loading 'scripts/nero.shader'
...loading 'scripts/cos1.shader'
...loading 'scripts/cos2.shader'
...loading 'scripts/cnid2.shader'
...loading 'scripts/qkq.shader'
...loading 'scripts/elglight2.shader'
...loading 'scripts/mapcent_flag.shader'
...loading 'scripts/ci.shader'
...loading 'scripts/km_fx.shader'
...loading 'scripts/km_lights.shader'
...loading 'scripts/km_misc.shader'
...loading 'scripts/km_noclip.shader'
...loading 'scripts/km_particel_spark.shader'
...loading 'scripts/km_particel_water.shader'
...loading 'scripts/km_water.shader'
...loading 'scripts/chiropteradm.shader'
...loading 'scripts/wallportal.shader'
...loading 'scripts/nihiltex.shader'
...loading 'scripts/grtrees.shader'
...loading 'scripts/qkqtoilet.shader'
...loading 'scripts/shadowpeak.shader'
...loading 'scripts/blooddm2.shader'
...loading 'scripts/bdog3dm1.shader'
...loading 'scripts/bal3hh.shader'
...loading 'scripts/bal3meat.shader'
...loading 'scripts/satellite.shader'
...loading 'scripts/bal3corp.shader'
...loading 'scripts/auhtele31.shader'
...loading 'scripts/auh3dm1.shader'
...loading 'scripts/alientemple.shader'
...loading 'scripts/almostparadise.shader'
...loading 'scripts/ame7q3dm3.shader'
...loading 'scripts/ame7q3dm2.shader'
...loading 'scripts/almdm1.shader'
...loading 'scripts/alm3dm3.shader'
...loading 'scripts/outpost.shader'
...loading 'scripts/aeon_flux.shader'
...loading 'scripts/addict.shader'
...loading 'scripts/q3hh8.shader'
...loading 'scripts/q3mb.shader'
...loading 'scripts/q3hh1.shader'
...loading 'scripts/acl.shader'
...loading 'scripts/smashlamp.shader'
...loading 'scripts/aciddm7.shader'
...loading 'scripts/6+.shader'
...loading 'scripts/harlequin_sky.shader'
...loading 'scripts/lightningnew.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/tim.shader'
...loading 'scripts/base.shader'
...loading 'scripts/base_button.shader'
...loading 'scripts/base_object.shader'
...loading 'scripts/base_support.shader'
...loading 'scripts/base_wall.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/gothic_block.shader'
...loading 'scripts/gothic_floor.shader'
...loading 'scripts/gothic_light.shader'
...loading 'scripts/gothic_trim.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/shrine.shader'
...loading 'scripts/skin.shader'
----- finished R_Init -----

---

### Post by crane on 2005-05-07
Hmmmm, Strange that it's still not working. I didn't see anything really stand out from your quake3 start-up.

what about your xorg.conf file. Think you could post section of it.(mainly the modules being loaded and the video driver section?

Can you play any other games or have you tried? (ET, Wolfy, or tux racer?)

---

### Post by void_false on 2005-05-08
Is it possible to install Q3 on non-linux partition and then play in?

---

### Post by snark on 2005-05-08
Hi Again

Here you go xorg.conf... (below) ... also tux racer seems normal. 

By the way another super annoying thing is that the screen does not repaint quickly enough. So if I drag a window around I can see a trail that the window leaves on the screen. Know what I mean? Again this is not the case in XP. 

Seriously, Linux has a ways to go before it will ever be accepted as a replacement for XP. I am trying so hard!

Thanks....

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	# Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection 

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

---

### Post by void_false on 2005-05-08
Oh guyz I´m f***ing love you! Finally I´ve resized my linux partition and installed Q3A. Now it runs brilliantly! Hehe. Good ol´ times... eh.
Now just 2 little questions. First: what is the command to display fps? Dont remember quake´s console ;)
And second. My KDE runs on 100hz. And Quake switches to 85hz and screen goes beyond the border a little. How do I say Quake to use 100hz?
Thank you very much!  \\:D/

---

### Post by crane on 2005-05-08
[QUOTE=snark]
Seriously, Linux has a ways to go before it will ever be accepted as a replacement for XP. I am trying so hard!

[/QUOTE]

Keep trying, Linux still has a steep leaning curve for really understanding it but it worth it.

You config looks like mine so I see no probs there. I guess the next step would be to make sure you don't have any other processes going?  Is sound working OK for you?

---

### Post by crane on 2005-05-08
> **void_false]Oh guyz I´m f***ing love you! Finally I´ve resized my linux partition and installed Q3A. Now it runs brilliantly! Hehe. Good ol´ times... eh.
Now just 2 little questions. First: what is the command to display fps? Dont remember quake´s console  said:**
> 

In game drop the console (hit ~ key) 
Now type

[color=blue]/cg_drawFPS 1  [/color] [color=green]<------to show fps[/color]

Also you cna change you maxfps to allow better game play.
Mine is set at 125 I think default is 85.

[color=blue] /com_maxFPS 125[/color][color=green]<-----or what ever you want to set it at[/color]

There are also some other setting you could tweak to help game play Like field of Vision (fov). I think it's com_fov but could be wrong.

You can also use auto complete to help.
Just drop console and type the start of a cvar like [color=blue]/com_[/color] then hit the tab key and it will display a list of possible settings following com_ .
I'm not familiar with changing what hz quake3 uses though sorry.

Oh and 
[QUOTE]Oh guyz I´m f***ing love you!  

we love you too! :razz:  :lol:  :mrgreen:

---

### Post by jmanjeff on 2005-05-08
My Problem is no sound in Quake  :( The game runs smooth and at a steady 140 fps i am running debian sarge 2.6 kernel

---

### Post by crane on 2005-05-08
[QUOTE=jmanjeff]My Problem is no sound in Quake  :( The game runs smooth and at a steady 140 fps i am running debian sarge 2.6 kernel[/QUOTE]

Are you running anything else that could use sound? Teamspeak, listening to mp3 or streaming?

Doe the sound work with other games with no Problems?

---

### Post by jmanjeff on 2005-05-08
[QUOTE=crane]Are you running anything else that could use sound? Teamspeak, listening to mp3 or streaming?[/QUOTE]
No 

[QUOTE=crane]
Doe the sound work with other games with no Problems?[/QUOTE]
 no sound in tux racer  
I have sound in videos and i can play mp3s

---

### Post by OuR_LanD on 2005-05-10
Crane, would you be able to help me with my Nvidia graphics drivers? When i try to install them it says that i have X server running and need to turn it off. I downloaded the drivers from the Nvidia website. I'm stuck, i need help.

Btw i have a Nvidia GeForce Fx 5200 graphics card.

---

### Post by snark on 2005-05-10
Crane my sound works perfectly.

I am going to give up on getting quake to work in Ubuntu for now.. I will just use my XP boot for that.

Thanks for all the help.

---

### Post by void_false on 2005-05-10
[QUOTE=OuR_LanD]Crane, would you be able to help me with my Nvidia graphics drivers? When i try to install them it says that i have X server running and need to turn it off. I downloaded the drivers from the Nvidia website. I'm stuck, i need help.

Btw i have a Nvidia GeForce Fx 5200 graphics card.[/QUOTE]

Better fire up Synaptic and install drivers from Ubunty repo's.

---

### Post by crane on 2005-05-10
[QUOTE=OuR_LanD]Crane, would you be able to help me with my Nvidia graphics drivers? When i try to install them it says that i have X server running and need to turn it off. I downloaded the drivers from the Nvidia website. I'm stuck, i need help.

Btw i have a Nvidia GeForce Fx 5200 graphics card.[/QUOTE]

Have you tryied installing nvidia drivers from apt or synaptic or is there a certain driver you want?

I installed mine through apt and all is well.

[ubuntuguide](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by crane on 2005-05-10
[QUOTE=snark]Crane my sound works perfectly.

I am going to give up on getting quake to work in Ubuntu for now.. I will just use my XP boot for that.

Thanks for all the help.[/QUOTE]

Man I'm sorry to hear this. Are you duel booting? I will keep my eyes and ears peeled for a better answer. If I hear of anything I will let you know.

---

### Post by gil-galad on 2005-05-11
[QUOTE=jmanjeff]No 


 no sound in tux racer  
I have sound in videos and i can play mp3s[/QUOTE]

Try 'sudo killall esd' and then run the game.  If that works then I may have a permanent solution for you.

And its a lot easier to install quake3 in your home directory then mess with permissions in the root filesystem, I have all my games installed in ~/games.

---

### Post by crane on 2005-05-11
[QUOTE=gil-galad]And its a lot easier to install quake3 in your home directory then mess with permissions in the root filesystem, I have all my games installed in ~/games.[/QUOTE]


I agree, The only reason I started installing it as root in /usr/local/games was because I was changing distros alot.
Now if I change the distro or have major problems I can reload without losing everything.
Oh I have /dev/hda6 mounted at usr/local/games.!! :)

---

### Post by snark on 2005-05-12
[QUOTE=crane]Man I'm sorry to hear this. Are you duel booting? I will keep my eyes and ears peeled for a better answer. If I hear of anything I will let you know.[/QUOTE]

Hi Crane

Yes I am dual booting. I need XP for work reasons. I have to use a specific VPN client to connect to work....

Thanks for keeping your eyes open... its strange how it worked for a while and then stopped working... hmmm 

Its not a big deal since I have to keep XP on here anyway.

---

### Post by jmanjeff on 2005-05-12
[QUOTE=gil-galad]Try 'sudo killall esd' and then run the game.  If that works then I may have a permanent solution for you.

  [/QUOTE]


Password:
debian:~# killall esd
esd: no process killed
debian:~#

---

### Post by jmanjeff on 2005-05-15
sound fixed did not have alas base installed

---

### Post by crane on 2005-05-15
[QUOTE=jmanjeff]sound fixed did not have alas base installed[/QUOTE]

Glad to here it!! Now you gotta meet us in game sometime!!

---

### Post by themoddingden on 2005-05-18
it will not let me copy the file over at all 
I tried copy pasting your example nada
tried just copy from cd and from desktop nada

---

### Post by crane on 2005-05-19
[QUOTE=themoddingden]it will not let me copy the file over at all 
I tried copy pasting your example nada
tried just copy from cd and from desktop nada[/QUOTE]

Have you tried copying files using terminal?
Make sure you use 'sudo' at the begining of command if your trying to copy to /use/loacl/games/ folder.

You could also use sudo to open nautilus and copy and paste but all the open windows become cumbersome.
[color=blue]sudo nautilus[/color] in a terminal to open the file browser as root.


Sorry I didn't post sooner, I was out of town working :)

---

### Post by themoddingden on 2005-06-16
Hi;
I asked in the yahoo linux chat how to do it after telling them what the problem was.
heres how to;
cp -a lets me 
so i did this:
cp -a file name.pak /local/games/quake3/base and it worked.
the pak file were on the desktop.
now i have quake3 running on a fresh dual boot.
it's the only way i could get them to go there.
hope this helps .

---

### Post by sOnIc on 2005-06-29
Hi
Any of you have Quake3 working in Ubuntu x86_64 ?

I try to install but....

```
sonic@ubuntu$ sudo sh linuxq3apoint-1.32b-3.x86.run
Verifying archive integrity... All good.
Uncompressing Quake III Arena Point Release 1.32b...................... ....................................................................... ....................................................
This installation doesn't support glibc-2.0 on Linux / x86_64
(tried to run setup)
Please contact Id software technical support at bugs@idsoftware.com, or  ttimo@idsoftware.com
The setup program seems to have failed on x86_64/glibc-2.0

Please contact Id software technical support at bugs@idsoftware.com, or  ttimo@idsoftware.com
``` 

Any suggestions ? :roll:
Sorry for my bad english :wink:

---

### Post by Yagisan on 2005-07-05
[QUOTE=sOnIc]Hi
Any of you have Quake3 working in Ubuntu x86_64 ?

I try to install but....

```
sonic@ubuntu$ sudo sh linuxq3apoint-1.32b-3.x86.run
Verifying archive integrity... All good.
Uncompressing Quake III Arena Point Release 1.32b...................... ....................................................................... ....................................................
This installation doesn't support glibc-2.0 on Linux / x86_64
(tried to run setup)
Please contact Id software technical support at bugs@idsoftware.com, or  ttimo@idsoftware.com
The setup program seems to have failed on x86_64/glibc-2.0

Please contact Id software technical support at bugs@idsoftware.com, or  ttimo@idsoftware.com
``` 

Any suggestions ? :roll:
Sorry for my bad english :wink:[/QUOTE]
This should get it installed for you but I don't have this game so I can't help much with getting it to run.
```
sudo apt-get install linux32
sudo linux32 sh linuxq3apoint-1.32b-3.x86.run
```

Yagisan
&#23665;&#32650;&#12373;&#12435;

---

### Post by sOnIc on 2005-07-05
Hi!

Yagisan, m8, u again :D

```
sudo apt-get install linux32
sudo linux32 sh linuxq3apoint-1.32b-3.x86.run
```

This solve my problem, but now i have same black screen!!  ](*,)

---

### Post by Yagisan on 2005-07-05
[QUOTE=sOnIc]Hi!

Yagisan, m8, u again :D

```
sudo apt-get install linux32
sudo linux32 sh linuxq3apoint-1.32b-3.x86.run
```

This solve my problem, but now i have same black screen!!  ](*,)[/QUOTE]
And I have same "fix" again. For sound ```
sudo killall esd
``` right before running quake :) or no sound add ```
+set s_initsound 0
``` to the command line to start quake

---

### Post by sOnIc on 2005-07-05
Now i can play! :grin: :grin: but no sound :roll:
Tks Yagisan!

---

### Post by xaque on 2005-08-06
[QUOTE=sOnIc]Now i can play! :grin: :grin: but no sound :roll:
Tks Yagisan![/QUOTE]
 I have a problem running quake3 where whenever I quit out it gives the error

> ----- CL_Shutdown -----
RE_Shutdown( 1 )
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 135
  Minor opcode of failed request: 10
  Serial number of failed request: 84
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console


Normally this wouldn't be a problem, since I'm quitting the game anyways, what difference does it make if it crashes on exit? But it also resets my screen resolution to 640x480. Any ideas?

---

### Post by Hagbarddenstore on 2006-04-10
Hmm... Hi I'm new to this forum. I have followed the guide and I'm ready to play. But when I start the game trough the Terminal I get a messege saying I don't have OpenGL. How do I get Opengl so I can run Q3? It worked fine in WIndows XP.

---

### Post by crane on 2006-04-10
[QUOTE=Hagbarddenstore]Hmm... Hi I'm new to this forum. I have followed the guide and I'm ready to play. But when I start the game trough the Terminal I get a messege saying I don't have OpenGL. How do I get Opengl so I can run Q3? It worked fine in WIndows XP.[/QUOTE]

Look at the Ubuntu starter guides for help installing #d drivers for you video card. That should take care of the issue.
[http://easylinux.info/wiki/Ubuntu#Hardware]("http://easylinux.info/wiki/Ubuntu#Hardware")

---

### Post by daller on 2006-05-20
I get this when I run "quake3":

Sys_Error: recursive error after: User Interface is version 3, expected 6

---

### Post by crane on 2006-05-21
[QUOTE=daller]I get this when I run "quake3":

Sys_Error: recursive error after: User Interface is version 3, expected 6[/QUOTE]

Hmmm, Do you have the latest point release? 
Do you have more than one install of quake 3?
Are you trying to run a mod?
 ( I ask this question because I have seen this error when a new mod is installed on an old or different point release.)
 Did you install Quake3 with sudo or as user.

Sorry for all the questions but hopefully we can get some more info and get you playing Quake3!

---

### Post by daller on 2006-05-21
It's the first time I install q3 on linux!

I downloaded this:

linuxq3apoint-1.32b-3.x86.run

But does 3 mean "user interface 3"? - And where do I get 6?

Ran it as root "sh linuxq3apoint-1.32b-3.x86.run"

Copied the pak0.pk3 file to the baseq3 folder!

Ran "quake3" - And got the error!

---

### Post by crane on 2006-05-21
I just noticed you are using dapper? ARe you running xgl server by chance?

---

### Post by daller on 2006-05-22
Nope...

---

### Post by ^Albe^ on 2007-10-12
hi to all,
i have played many times quale3 with ubuntu (7.04)
since the upgrade to Gutsy (the rc one), i have no audio in quake3!
any suggestion?
obv the audio seems to work with other apps

thx and regards

---

### Post by shmoolik on 2007-10-20
> **daller said:**
> It's the first time I install q3 on linux!

I downloaded this:

linuxq3apoint-1.32b-3.x86.run

But does 3 mean "user interface 3"? - And where do I get 6?

Ran it as root "sh linuxq3apoint-1.32b-3.x86.run"

Copied the pak0.pk3 file to the baseq3 folder!

Ran "quake3" - And got the error!

you should cp the : pak1.pk3, pak2.pk3, pak3.pk3 to the baseq3 folder.

---

