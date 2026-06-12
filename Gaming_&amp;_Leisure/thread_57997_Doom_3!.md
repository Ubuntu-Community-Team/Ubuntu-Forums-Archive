---
title: "Doom 3??!"
date: 2005-08-18
forum: Gaming &amp; Leisure
---

### Post by Muhammad on 2005-08-18
[quote=Doom 3 Installation Guide for Linux]The following files need to be copied from the win32 install CDs
to your base/ directory ( md5 sums provided below as reference )
by default, /usr/local/games/doom3/base

71b8d37b2444d3d86a36fd61783844fe  base/pak000.pk4
4bc4f3ba04ec2b4f4837be40e840a3c1  base/pak001.pk4
fa84069e9642ad9aa4b49624150cc345  base/pak002.pk4
f22d8464997924e4913e467e7d62d5fe  base/pak003.pk4
38561a3c73f93f2e6fd31abf1d4e9102  base/pak004.pk4

If you are also installing the Resurrection of Evil Expansion Pack,
you need to copy the following file to your d3xp/ directory
by default, /usr/local/games/doom3/d3xp

a883fef0fd10aadeb73d34c462ff865d  d3xp/pak000.pk4

Localization is not supported on Linux ( only english ), you should not copy over any of the zpak files.

Start the game with the command: doom3
Start the dedicated server with the command: doom3-dedicated

If installed, you can start the Expansion Pack directly from the command line with the command: doom3 +set fs_game d3xp
Or you can select it in the mods menu of the base game.[/quote]

OMGWTFBBQ

What's with all the numbers? I'm a newbie to this whole Linux thing...

---

### Post by Sam on 2005-08-18
These are md5 checksums. It's used to check the integrity of a file. Use the command
```
$ md5sum <file>
```
to get the md5 checksum of a file.

---

### Post by Muhammad on 2005-08-18
[QUOTE=Sam]These are md5 checksums. It's used to check the integrity of a file. Use the command
```
$ md5sum <file>
```
to get the md5 checksum of a file.[/QUOTE]
 OK thanks, I'll give it a try.

---

### Post by Muhammad on 2005-08-18
Well I guess I fail, Could you please give an example?

---

### Post by Sam on 2005-08-18
Example:

File to check: /home/username/file_to_check
Command: [FONT=monospace]md5sum /home/username/file_to_check[/FONT]
Output: [FONT=monospace]f53d20af66122b7ba7e3bb8850f936ae  /home/username/file_to_check[/FONT]


In your case, if you want to check the md5 checksums of the Doom 3 files do:
```
md5sum /usr/local/games/doom3/base/pak000.pk4 /usr/local/games/doom3/base/pak001.pk4 /usr/local/games/doom3/base/pak002.pk4 /usr/local/games/doom3/base/pak003.pk4 /usr/local/games/doom3/base/pak004.pk4 /usr/local/games/doom3/d3xp/pak000.pk4
```
And it should outputs:
```
71b8d37b2444d3d86a36fd61783844fe /usr/local/games/doom3/base/pak000.pk4
4bc4f3ba04ec2b4f4837be40e840a3c1 /usr/local/games/doom3/base/pak001.pk4
fa84069e9642ad9aa4b49624150cc345 /usr/local/games/doom3/base/pak002.pk4
f22d8464997924e4913e467e7d62d5fe /usr/local/games/doom3/base/pak003.pk4
38561a3c73f93f2e6fd31abf1d4e9102 /usr/local/games/doom3/base/pak004.pk4
a883fef0fd10aadeb73d34c462ff865d /usr/local/games/doom3/d3xp/pak000.pk4
```

If it's not the same numbers as this, you have not the files expected by Doom 3.

---

### Post by Muhammad on 2005-08-18
I don't know how to thank you enough, but I have one more silly question...

How do I run the game? XD

---

### Post by Muhammad on 2005-08-18
I doubt no one knows...

---

### Post by Brunellus on 2005-08-18
[QUOTE=Muhammad]I doubt no one knows...[/QUOTE]
 type doom3 in a terminal?

---

### Post by Muhammad on 2005-08-18
I did, and recieved this:

[quote=Terminal]muhammad@ubuntu:~$ doom3
bash: doom3: command not found
muhammad@ubuntu:~$
[/quote]

---

### Post by Muhammad on 2005-08-18
How do I launch this?

doom3-linux-1.3.1302.x86.run

---

### Post by Brunellus on 2005-08-18
[QUOTE=Muhammad]How do I launch this?

doom3-linux-1.3.1302.x86.run[/QUOTE]
 $./doom3-linux-1.3.1302.x86.run

---

### Post by Muhammad on 2005-08-18
[QUOTE=Brunellus]$./doom3-linux-1.3.1302.x86.run[/QUOTE]
 > muhammad@ubuntu:~$ doom3
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.30.77/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0xf07eb555
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
/home/muhammad/.doom3/base
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
/usr/local/games/doom3/base/game00.pk4 (2 files)
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
couldn't exec DoomConfig.cfg
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
Using 8/8/8 Color bits, 8 Alpha bits, 16 depth, 8 stencil display.
GL_RENDERER: Mesa GLX Indirect
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.8
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 15052 frames ( 60208 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
X..GL_ARB_texture_compression not found
X..GL_EXT_texture_filter_anisotropic not found
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
X..GL_NV_register_combiners not found
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
X..GL_ARB_vertex_buffer_object not found
X..GL_ARB_vertex_program not found
X..GL_ARB_fragment_program not found
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Not available.
----- R_ReloadARBPrograms -----
glprogs/test.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/test.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/shadow.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/R200_interaction.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_bumpAndLight.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_specularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseAndSpecularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()


What the...?

---

### Post by h4ck on 2005-10-13
Try sh nameofthatfile 

:D

---

### Post by dcarpenter on 2005-10-13
if the the file is in your home directory type

sh nameoffile.run

if its on your Desktop:

sh /home/YOURNAME/Desktop/nameoffile.run

---

### Post by mjreged on 2005-10-14
Ok eveyone, why is that noone wants to in full explain what's going on to this guy who wants to run DOOM 3.   I have an idea for you;  when i installed amd64 ubuntu and ati drivers ( that actually worked Yey ) ,  then decided to run doom3 and got the same output that is posted here, i found out that doom3 does not configure itself nicely with the sound system we might have, so some kind of kill esd command has to be used,, etc... etc... ,,,   and on top of that i have native 64 bit drivers i would have to move some libs into lib32 folder, etc.... i decided to quit at that point... Instead i installed Unreal Tournament 2004 to make sure that my system can in fact run games ,,, and guess what it worked without a single problem,, sound, graphics, all worked ....    Doom 3 should have been configured  better for linux users, just like the UT2004 is...

---

### Post by dcarpenter on 2005-10-14
I have both UT2004 and Doom3 installed and both worked right out of the box.  Just installed and played, no config necessary.
My system:

radeon9800xt with 8.16.20 drivers in synaptic
soundblaster audigy 2

Doom3's performance was sub par at best but thats to be expected from the semi crap ati drivers.  UT2004 performed awesome.

---

### Post by elasticwings on 2005-10-14
If it is an executable file then you can just do ./doom3-linux-1.3.1302.x86.run

If that doesn't work then the file may not be executable.
Do a chmod +x doom3-linux-1.3.1302.x86.run

---

### Post by crane on 2005-10-14
[QUOTE=elasticwings]If it is an executable file then you can just do ./doom3-linux-1.3.1302.x86.run

If that doesn't work then the file may not be executable.
Do a chmod +x doom3-linux-1.3.1302.x86.run[/QUOTE]

This is the install file right.
If you plan on installing in your home directory the just execute it as a user. 
If you copied  all the pack files to /usr/local/games/doom3 then it would be best to run this program as root. It will install everything to /usr/local/games/doom3 by default. When it is through installing it will ask if you want to play. Click no. (it's not a good idea to run games as root)
Then just type doom3 in the terminal window. It will run the game as a user and create a hidden file in your home directory called .doom3 . This file will hold all your configs.

---

### Post by ubernoob on 2006-04-09
I had the same problem as you with doom 3.
WARNING: vertex array range in virtual memory (SLOW) indicates that your graphic drivers aren't installed / configured correctly.

"glxinfo | grep rendering" will probably give you "direct rendering: No"

---

### Post by phalab on 2006-07-07
Please have a look here:

[http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)

note the part where it talks about the 24bpp desktop. I changed this, and it worked for me. There are some notes on sound too.

Regards,
Alex

---

