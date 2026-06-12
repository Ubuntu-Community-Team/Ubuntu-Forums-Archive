---
title: "HowTo : Install DOOM 3"
date: 2008-08-19
forum: Gaming &amp; Leisure
---

### Post by linuxguymarshall on 2008-08-19
This is just a simple guide on how to install DOOM 3 in Ubuntu (GNOME Desktop environment). This guide was written for the average user who hates the terminal. Terminal users can easily adapt this to use in the terminal. 

If I made errors or if you have troubles just post and I will try to help.

[LIST]
[*]Open up your internet browser of choice.
[*]Go to this URL : **[ftp://ftp.idsoftware.com/idstuff/doom3/linux/](ftp://ftp.idsoftware.com/idstuff/doom3/linux/)**
[*]Download the latest DOOM 3 file (doom3-linux-1.3.1.1304.x86.run at time of writing)
[*]Open up Terminal or Konsole or whatever you may use.
[*]Type '**cd ~/Desktop**' or wherever you have downloaded your file
[*]Now type '**dir**' and see if the DOOM 3 file appears.
[*]If it does then type '**sudo sh doom3-linux-x.x.x.x.x86.run**'  replace the x's with the version numbers
[*]Now the installer will load
[*]Accept the license agreement if you dare
[*]Continue on until it asks for the install path
[*]When it asks for the install path replace the default with '/home/<username>/doom3'  
[*]In the next field, the link field, replace the default with '/home/<username>/
[*]If you plan to play online go ahead and click 'Install PunkBuster'
[*]Click 'Begin Install' 


[*]Once the install is complete get your DOOM 3 CD's ready

[*]Place CD #1 in your drive
[*]**NOTE : You may want to run nautilus as root if you do not know how to do this through the terminal. To do that open a terminal and type 'gksudo nautilus'**

[*]Open up the CD in Nautilus. 
[*] Go to the cd directory '/Setup/Data/base/'
[*]Right click the file 'pak002.pk4' and select 'Copy...'
[*]Paste this file in your '~/doom3/base/'  directory
[*]Eject CD #1

[*]Place Cd #2 in your drive
[*]Go to the cd directory '/Setup/Data/base/' and copy all the files to '~/doom3/base/' and do the game process for CD #3
[*]Eject CD 3 and play DOOM 3
[/LIST]


**I HAVE CREATED A GUIDE AND SOME SCRIPTS FOR INSTALLING THIS EASILY ON MY SITE [HERE]("http://sites.google.com/site/linuxguymarshall/doom-3") **

---

### Post by linuxguymarshall on 2008-08-19
Some people asked me some questions and here are a few answers :

Q.Can I play with Windows, OS X users?
A.Yes, we just did this at a LAN party the other day

Q.How can I update?
A.There is an update/patch button on the main menu.

Q.How can I install mods?
A.Drop them in the ~/DOOM3 directory

---

### Post by linuxguymarshall on 2008-08-26
Hey, im going to be working on a shell script to make this a bit easier. If anyone wants to contribute just tell me. I have know idea how to write a shell script but im learning.

---

### Post by Crafty Kisses on 2008-08-26
Nice tutorial, will be good for the future. :)

---

### Post by linuxguymarshall on 2008-08-27
There are install scripts available now! Read the bottom of the first post for info

---

### Post by Dan_Dranath999 on 2008-09-23
you got mods working with 8.04? i haven't. (Used to play them fine on Gutsy, tho...)

---

### Post by crazyfuturamanoob on 2008-10-26
For some reason I got two doom3 shortcuts in my Applications->Games.
Both have exactly same name. Which one to use?
Edit: Another was for some "dedicated" thing. What is that?

And now when I type in my serial, it refuses it!! What now? :P

---

### Post by Sockerdrickan on 2008-10-26
the dedicated starts a server

---

### Post by crazyfuturamanoob on 2008-10-26
But it refuses my serial :O My doom version is 1.3.1.1304

Edit: Installed 1.1 linux client. It doesn't even ask the serial. :)

---

### Post by slick666 on 2008-12-08
Nice tutorial,

I think I got it all working with the exception of the video. The problem is I'm using a cheap wide-screen monitor. My settings are currently:
1440x900@50Hz

When doom3 starts the screen states "Unable to Display Frequency". I can hear the heart beat, I'm sure it's working but I need to be able to specify the resolution and frequency at the command line.

any ideas?

---

### Post by linuxguymarshall on 2008-12-09
> **slick666 said:**
> Nice tutorial,

I think I got it all working with the exception of the video. The problem is I'm using a cheap wide-screen monitor. My settings are currently:
1440x900@50Hz

When doom3 starts the screen states "Unable to Display Frequency". I can hear the heart beat, I'm sure it's working but I need to be able to specify the resolution and frequency at the command line.

any ideas?


I have the same problem with my HDTV in my room. The problem is that your widescreen monitor (16:9) is not going to be able to play DOOM (4:3) without some tweaks. 

Check out 
/home/[your username]/doom3/base/

and find the 'DoomConfig.cfg' file. Find where it says "Fullscreen" or something like that. It will be a 1 or a 0. Change it to the opposite one then run doom 3. It will start in windowed mode but change your settings to widescreen there. Or try and find a "widescreen" or "resolution" setting. I would help more but im on a WinBlows machine ATM and I don't think the config files are the same.

---

### Post by slick666 on 2008-12-09
Thanks man thats just what I was looking for.

Once I got it into windowed mode I referenced this site on how to set it up for widescreen.
[http://doom.freakygaming.com/pc/action/doom_3/tutorials/running_doom_3_in_widescreen.html]("http://doom.freakygaming.com/pc/action/doom_3/tutorials/running_doom_3_in_widescreen.html")

it's pretty simple. The only thing that wasn't clear is that all the "commands he was talking about had to be intered through the doom 3 console. press the key with the "`" and "~" on it to get the console once the game starts.

---

### Post by linuxguymarshall on 2008-12-09
good to know I can help

---

### Post by slick666 on 2008-12-10
Ok, Everything is working but the game freezes at random points. Any ideas?

---

### Post by linuxguymarshall on 2008-12-10
Do they have anything in common? A particular 3D model? Shader? Does it crash at the same point every time?

---

### Post by Polygon on 2008-12-10
your scripts are confusing and don't seem to work

i extracted it to my desktop
ran script 1, it downloaded some file, then asked me to enter my password, i did, and then it asked me to put in disk 1
then it just asked me to put in disk 2 without doing anything, and then i put in disk 2 and it just keeps asking for it...

> 
mark@Humboldti:~/Desktop/DOOM 3 Installers$ sh doom3_install1.sh 
¨DOWNLOADING DOOM 3 INSTALLER¨
--2008-12-10 18:06:32--  [ftp://ftp.idsoftware.com/idstuff/doom3/linux/doom3-linux-1.3.1.1304.x86.run](ftp://ftp.idsoftware.com/idstuff/doom3/linux/doom3-linux-1.3.1.1304.x86.run)
           => `doom3-linux-1.3.1.1304.x86.run.1'
Resolving ftp.idsoftware.com... 192.246.40.185
Connecting to ftp.idsoftware.com|192.246.40.185|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /idstuff/doom3/linux ... done.
==> SIZE doom3-linux-1.3.1.1304.x86.run ... 21145838
==> PASV ... done.    ==> RETR doom3-linux-1.3.1.1304.x86.run ... done.
Length: 21145838 (20M)

100%[======================================>] 21,145,838  51.6K/s   in 6m 17s  

2008-12-10 18:12:50 (54.7 KB/s) - `doom3-linux-1.3.1.1304.x86.run.1' saved [21145838]

¨INSTALLER DOWNLOADED¨



¨YOU WILL NEED TO TYPE YOUR PASSWORD¨
sh: Can't open doom3-linux-1.3.1.1304.x86.run
¨INSTALLER RUNNING¨
¨Place DOOM 3 cd 1 inside primary drive then begin script 2 after done installing¨
mark@Humboldti:~/Desktop/DOOM 3 Installers$ sh doom3_install2.sh 
cp: cannot create regular file `/home/mark/doom3/base': No such file or directory


---

### Post by slick666 on 2008-12-10
It's only crashed twice on me out of two time so I can't nail down anything specific. is there a way to put doom in debug mode so I can search through some log?

---

### Post by linuxguymarshall on 2008-12-11
> **slick666 said:**
> It's only crashed twice on me out of two time so I can't nail down anything specific. is there a way to put doom in debug mode so I can search through some log?


You could run it in a terminal.

---

### Post by linuxguymarshall on 2008-12-11
> **Polygon said:**
> your scripts are confusing and don't seem to work

i extracted it to my desktop
ran script 1, it downloaded some file, then asked me to enter my password, i did, and then it asked me to put in disk 1
then it just asked me to put in disk 2 without doing anything, and then i put in disk 2 and it just keeps asking for it...


It probably means that your disc drives are not where I set them to be. Just change the drive location in the script

---

### Post by slick666 on 2008-12-11
Ok, this time I ran it in a terminal piping the output of that terminal to a file. This time it failed in almost exactly the same spot. I don't know what it's called but when starting the game it's a hallway where the lights turn off and walls on the right blink and beep. you go to the end and turn left and there is a stairway up with a single swinging light. some monsters come out at this time and it's right around here where the system freezes. The ONLY way I've been able to get out is Ctrl+Alt+Backspace and restart X. Here is the log file.
```
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.111/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/yolanda/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
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
Free86-VidModeExtension Activated at 1440x900
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: unknown board/AGP/SSE2
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.17a
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
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
...using GL_NV_register_combiners
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using EXT_depth_bounds_test
---------- R_NV20_Init ----------
---------------------------------
----------- R200_Init -----------
Not available.
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
copy gamex86.so to /home/yolanda/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Jan 16 2007
Initializing event system
...473 event definitions
Initializing class hierarchy
...142 classes, 382184 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 2998.55 MHz
Compiled 'removeInitialSplineAngles': 2867.9 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67875, 1357500 bytes
   Functions: 2109, 250532 bytes
   Variables: 147376 bytes
    Mem used: 2479288 bytes
 Static data: 2277552 bytes
   Allocated: 3284544 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
Opening IP socket: localhost:-1
--- Common Initialization Complete ---
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 6652
1008 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
found XNVCtrl extension 1.17
256 MB Video Memory
Async thread started
guid set to JvYltgnGbLw
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
--------- Game Map Shutdown ----------
--------------------------------------
reloading guis/mainmenu.gui.
reloading guis/restart.gui.
reloading guis/gameover.gui.
reloading guis/msg.gui.
reloading guis/takeNotes.gui.
reloading guis/intro.gui.
reloading guis/netmenu.gui.
--------- Map Initialization ---------
Map: game/mc_underground
glprogs/heatHaze.vfp
glprogs/heatHaze.vfp
glprogs/heatHazeWithMask.vfp
glprogs/heatHazeWithMask.vfp
------- Game Map Init SaveGame -------
collision data:
   721 models
 69250 vertices (1623 KB)
128065 edges (4502 KB)
 55477 polygons (3881 KB)
  5639 brushes (777 KB)
 24881 nodes (680 KB)
100541 polygon refs (785 KB)
 26540 brush refs (207 KB)
 38026 internal edges
  4376 sharp edges
     0 contained polygons removed
     0 polygons merged
 12457 KB total memory used
869 msec to load collision data.
map bounds are (6152.0, 5344.0, 2560.0)
max clip sector is (192.3, 334.0, 320.0)
    4 KB passage memory used to build PVS
    3 msec to calculate PVS
   58 areas
  134 portals
    9 areas visible on average
  464 bytes PVS data
[Load AAS]
loading maps/game/mc_underground.aas48
done.
[Load AAS]
loading maps/game/mc_underground.aas96
[Load AAS]
loading maps/game/mc_underground.aas_guardian
[Load AAS]
loading maps/game/mc_underground.aas_mancubus
[Load AAS]
loading maps/game/mc_underground.aas_sabaoth
[Load AAS]
loading maps/game/mc_underground.aas_cyberdemon
glprogs/heatHazeWithMaskAndVertex.vfp
glprogs/heatHazeWithMaskAndVertex.vfp
removed 4 degenerate triangles
WARNING: Couldn't load sound 'guisounds.wav' using default
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
loaded collision model models/mapobjects/cpu/comrack.lwo
loaded collision model models/mapobjects/utility/binplug/binplug_c.lwo
loaded collision model models/mapobjects/doors/techdoor1/techdr1rt.lwo
loaded collision model models/mapobjects/doors/techdoor1/techdr1lft.lwo
loaded collision model models/mapobjects/doors/delelev/delelevrt.lwo
loaded collision model models/mapobjects/doors/delelev/delelevlf.lwo
loaded collision model models/mapobjects/elevators/elevator.lwo
loaded collision model models/mapobjects/signs/marquee/marquee.lwo
loaded collision model models/mapobjects/swinglights/swinglight_long_wbulbs_bulb.ase
loaded collision model models/mapobjects/swinglights/swinglight1c.lwo
loaded collision model models/mapobjects/mc_underground/mcucave.ASE
loaded collision model models/mapobjects/guiobjects/techdrpanel1/techdrpanel1.lwo
loaded collision model models/mapobjects/doors/techdoor1/techdr1frame.lwo
loaded collision model models/mapobjects/airlock/airlockcomp.lwo
loaded collision model models/mapobjects/mc_underground/outside/mc_ug_out.lwo
loaded collision model models/mapobjects/lights/klaxon/klaxon.lwo
loaded collision model models/mapobjects/guiobjects/mc_constand/mc_constand.lwo
loaded collision model models/mapobjects/skmachines/skcube.lwo
loaded collision model models/mapobjects/lab/mfscomp/mfscompcell.lwo
loaded collision model models/mapobjects/com/joint/joint.lwo
loaded collision model models/mapobjects/doors/techdoor2/techdr2rt.lwo
loaded collision model models/mapobjects/doors/techdoor2/techdr2lft.lwo
loaded collision model models/mapobjects/delta1/warfoot/warfoot.lwo
loaded collision model models/mapobjects/elevators/elevator_door.lwo
loaded collision model models/mapobjects/filler/toolchest.lwo
loaded collision model models/mapobjects/healthgui/healthgui.lwo
loaded collision model models/mapobjects/mcity/mc_underarm/underarmbase.lwo
loaded collision model models/mapobjects/mcity/mc_underarm/underarmarm.lwo
loaded collision model models/mapobjects/mcity/mc_underarm/underarmhand.lwo
loaded collision model models/mapobjects/mcity/mc_underarm/underarmfingers.lwo
loaded collision model models/mapobjects/cpu/serverplate.lwo
loaded collision model models/mapobjects/cpu/cpufloorinsert2.lwo
loaded collision model models/mapobjects/utility/trapbra/trapbra.lwo
loaded collision model models/mapobjects/doors/techdoor2/techdr2frame.lwo
loaded collision model models/mapobjects/matt_test/mc_underthing1.ASE
loaded collision model models/mapobjects/airlock/airlockvertlock.lwo
loaded collision model models/mapobjects/airlock/airlockbrace.lwo
loaded collision model models/mapobjects/airlock/airlockdoor.lwo
loaded collision model models/mapobjects/airlock/airlockdoorgui.lwo
loaded collision model models/mapobjects/shipping_crates/shipping_crates.lwo
loaded collision model models/mapobjects/airlock/airlockhallgui.lwo
loaded collision model models/mapobjects/com/modconsole3.lwo
loaded collision model models/mapobjects/com/modconsole2.lwo
loaded collision model models/mapobjects/com/modconsole6.lwo
loaded collision model models/mapobjects/com/modconsole1.lwo
loaded collision model models/mapobjects/utility/binplug/binplug_o.lwo
loaded collision model models/mapobjects/utility/tecknob2/tecknob2.lwo
loaded collision model models/mapobjects/cpu/cpuoverdoor.lwo
loaded collision model models/mapobjects/mc_underground/outside/mc_ug_out2.lwo
loaded collision model models/mapobjects/caves/crane/cranecomp.lwo
loaded collision model models/mapobjects/mc_underground/mcucave_b.ASE
loaded collision model models/mapobjects/mc_underground/mcucave_c.ASE
loaded collision model models/mapobjects/storagecab/wallcabinet/wallcabinetdoor.lwo
loaded collision model models/mapobjects/storagecab/pegmount/pegmount.lwo
loaded collision model models/mapobjects/com/platguistand/platguistand.lwo
loaded collision model models/mapobjects/mcity/deskcomp/deskcomp.lwo
loaded collision model models/mapobjects/filler/lunchbag.lwo
loaded collision model models/mapobjects/shelf/shelf.lwo
loaded collision model models/mapobjects/monitors/hangingmonitor.lwo
loaded collision model models/mapobjects/mc_underground/outside/mc_ug_out3.lwo
WARNING: underground_cin_player_1 has no AAS file
--------------------------------------
----- idRenderModelManagerLocal::EndLevelLoad -----
    1 models purged from previous level,  1293 models kept.
---------------------------------------------------
----- idImageManager::EndLevelLoad -----
WARNING: Non-portable: path contains uppercase characters: base/dds/makeIntensity/lights
WARNING: Non-portable: path contains uppercase characters: base/dds/makeIntensity/lights
WARNING: Non-portable: path contains uppercase characters: base/dds/makeIntensity/lights
WARNING: Non-portable: path contains uppercase characters: base/dds/makeIntensity/lights
    0 purged from previous
  158 kept from previous

 1900 new loaded
all images loaded in  22.5 seconds
----------------------------------------
----- idSoundCache::EndLevelLoad -----
26131k referenced
  935k purged
----------------------------------------
sound: found efxs/mc_underground.efx
-----------------------------------
 41971 msec to load game/mc_underground
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
idRenderWorld::GenerateAllInteractions, msec = 102, staticAllocCount = 0.
interactionTable size: 4066152 bytes
41929 interaction take 4696048 bytes
------------- Warnings ---------------
during game/mc_underground...
WARNING: Couldn't load sound 'guisounds.wav' using default
WARNING: Non-portable: path contains uppercase characters: base/dds/makeIntensity/lights
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
3 warnings
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
Posix_QueEvent: overflow
loaded collision model models/weapons/shell1/mshell_lo.lwo
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
WARNING: Non-portable: path contains uppercase characters: base/sound/VO/video
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
loaded collision model models/mapobjects/fuel_barrel/exp_barrel2c.lwo
loaded collision model models/mapobjects/fuel_barrel/exp_barrel2b.lwo
WARNING: 'player1' telefragged 'moveable_chair2_1'
WARNING: pak000.pk4/script/map_mc_underground.script(1944): Thread 'map_mc_underground::after_invasion': teleported 'crane_main' which has the pushing mover 'func_static_199' bound to it

WARNING: pak000.pk4/script/map_mc_underground.script(1944): Thread 'map_mc_underground::after_invasion': teleported 'crane_main' which has the pushing mover 'crane_carrier' bound to it

snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
loaded collision model models/gibs/head_pork.lwo
loaded collision model models/gibs/torso_pork.lwo
loaded collision model models/gibs/rup_arm_pork.lwo
loaded collision model models/gibs/left_waist_pork.lwo
loaded collision model models/gibs/lup_leg_pork.lwo
loaded collision model models/gibs/rup_leg_pork.lwo
loaded collision model models/gibs/rup2_leg_pork.lwo
loaded collision model models/gibs/pelvis_pork.lwo
loaded collision model models/gibs/skull_pork.lwo
snd_pcm_writei 4096 frames failed: Broken pipe
preparing audio device for output
loaded collision model models/weapons/shell1/sshell_bigger.lwo
loaded collision model models/items/flashlight/flashlight2_world.lwo
loaded collision model models/weapons/shotgun/w_shotgun2.lwo
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
--------- Game Map Shutdown ----------
WARNING: idClipModel::FreeTraceModel: tried to free uncached trace model
--------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()

```

Let me know what you think

---

### Post by linuxguymarshall on 2008-12-12
disable compiz and turn all graphics to low. would type more but the wii browser is not made for a lot of typing

---

### Post by slick666 on 2008-12-14
Compiz is off but I'm off and traveling for th holidays. I will have a chance to try those in a couple for weeks.

---

### Post by Polygon on 2008-12-14
> **linuxguymarshall said:**
> It probably means that your disc drives are not where I set them to be. Just change the drive location in the script

and how do you do this? the script never asks for a drive location. not to mention my dvd drive is at the default place, /dev/sdc0

---

### Post by Brebs on 2008-12-15
I'd suggest writing an installer script like my [Quake 4 installer](http://fedoraforum.org/forum/showthread.php?t=189064) ;)

> **Polygon said:**
> /dev/sdc0
That is the device. It is *not* a mount point. Mount points should be in /mnt/ or /media/. You will probably have a default entry for it in /etc/fstab.

---

### Post by linuxguymarshall on 2008-12-15
> **Brebs said:**
> I'd suggest writing an installer script like my [Quake 4 installer]("http://fedoraforum.org/forum/showthread.php?t=189064") ;)


That is the device. It is *not* a mount point. Mount points should be in /mnt/ or /media/. You will probably have a default entry for it in /etc/fstab.


I dont have time now but I will give it a look in a few minutes

---

### Post by linuxguymarshall on 2008-12-15
> **Polygon said:**
> and how do you do this? the script never asks for a drive location. not to mention my dvd drive is at the default place, /dev/sdc0


The script should not ask for a location. All the script is is a set of commands for the terminal open it up in vim (or gedit, loser)  and edit the script. It's released under the MIT License so rip it up and redistribute if you want.

---

### Post by Gosujii-sama on 2009-01-07
This has nothing to do with the actual installation of doom 3. However since I used the files you specifyed I want to make it compatible with any and all changes made by them (if it matters). After setup of doom 3 everything runs fine, however after downloading "Last Man Standing 4.0" mod and unziping to the doom 3 directory then booting doom it's rejecting the mod it will close out doom and act like it's trying to restart but then just dies. I'm not even sure where to begin on why it doesn't work as you yourself said in your post mods work with it...
Also like to mention on launcher it put my doom 3 in "Other" and there ARE 2 icons for it however one doesn't work (assuming its the dedicated server which I don't care about).

Using ubuntu hardy if that makes a difference cards all installed nvidia high enough to run doom 3 so thats not it. All I can figure is it's and issue between the doom 3 setup from those files vs and the mod itself (as I've always noticed the mod had issues even on winblows) between crashing and such.

---

### Post by wootah on 2009-01-07
Anyone have problems with the serial? Everytime I use the serial, it states that it is an invalid serial ...

---

### Post by Gosujii-sama on 2009-01-08
The serial is sent via doom 3 program itself to id softwares key server. Yours won't work due to it's not a store bought doom 3. You probably downloaded a copy of doom 3 trial and want to unlock it or some other such thing. If it's a valid key off your jewel case or a copy bought online insure the key is correct case sensitive blah blah blah. Other things I could suggest before thinking to hard is insure you followed the steps in the tutorial given by this nice kid to the letter. Personally I did it by hand without the shell scripts he wrote. Try that stuff and let me know what happens. Also make sure your connected to the internet when you fire off the key.

---

### Post by wootah on 2009-01-10
> **Gosujii-sama said:**
> The serial is sent via doom 3 program itself to id softwares key server. Yours won't work due to it's not a store bought doom 3. You probably downloaded a copy of doom 3 trial and want to unlock it or some other such thing. If it's a valid key off your jewel case or a copy bought online insure the key is correct case sensitive blah blah blah. Other things I could suggest before thinking to hard is insure you followed the steps in the tutorial given by this nice kid to the letter. Personally I did it by hand without the shell scripts he wrote. Try that stuff and let me know what happens. Also make sure your **connected to the internet** when you fire off the key.
Well isn't that just great. :(

---

### Post by sankster2001 on 2009-01-17
umm i have a small problem with the scripts it runs downloads the file then terminal just closes, even a manual install refuses to work just pops out with a .setup23667 not found error please help i am pulling my hair out trying to get this to work. thanks

---

### Post by wootah on 2009-01-20
> **sankster2001 said:**
> umm i have a small problem with the scripts it runs downloads the file then terminal just closes, even a manual install refuses to work just pops out with a .setup23667 not found error please help i am pulling my hair out trying to get this to work. thanks
Did you try redownloading the script?

---

