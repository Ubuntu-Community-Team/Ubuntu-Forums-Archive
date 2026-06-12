---
title: "Curious Doom3 issue"
date: 2007-10-29
forum: Gaming &amp; Leisure
---

### Post by employeeno5 on 2007-10-29
I appear to have successfully installed Doom 3 in Ubuntu. I'm a new Ubuntu user, still in my first week, and I'm brand new to Linux. So far I've been getting down all the basics fine and seem to have things running well, and decided to try running doom 3. 
Everything appears to be installed correctly but when I go to run the game a small black window opens for a half-second before closing. And that's it. 
I ran the command through the terminal to see if it would shed any light on things. Like I said I'm new to Linux and I certainly no nothing about the details of how id makes a game, but it would appear to me that the game is shutting itself down before it can even start a simple cd-key screen or anything because it thinks that my system can't handle the game.
I've posted the dialog from the terminal at end of my message.

This game ran great in Windows xp. Not super-top quality but it handled the default graphics and sound terrifically and played fantastically. I'm wondering if anyone can shed any light on my problem or any possible solutions.

Thanks in advanced to anyone who takes the time to even look this over. I have to say that the level of support and helpfulness of this community is remarkable. I'm totally impressed and totally happy with my switch to Ubuntu so far. Hoping I can still shoot demons too. Thanks!

terminal dialog:

DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.0.16/255.255.255.0
------ Initializing File System ------
Loaded pk4 /media/sda2/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /media/sda2/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /media/sda2/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /media/sda2/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /media/sda2/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /media/sda2/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /media/sda2/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /media/sda2/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /media/sda2/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /media/sda2/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /media/sda2/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /media/sda2/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/broderick/.doom3/base
/media/sda2/doom3/base
/media/sda2/doom3/base/pak008.pk4 (3 files)
/media/sda2/doom3/base/pak007.pk4 (38 files)
/media/sda2/doom3/base/pak006.pk4 (48 files)
/media/sda2/doom3/base/pak005.pk4 (63 files)
/media/sda2/doom3/base/pak004.pk4 (5137 files)
/media/sda2/doom3/base/pak003.pk4 (4676 files)
/media/sda2/doom3/base/pak002.pk4 (6120 files)
/media/sda2/doom3/base/pak001.pk4 (8972 files)
/media/sda2/doom3/base/pak000.pk4 (2698 files)
/media/sda2/doom3/base/game03.pk4 (2 files)
/media/sda2/doom3/base/game02.pk4 (2 files)
/media/sda2/doom3/base/game01.pk4 (2 files)
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
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
XFree86-VidModeExtension not available
Xlib:  extension "XFree86-DGA" missing on display ":1.0".
Failed to detect DGA DirectVideo Mouse
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
GL_RENDERER: ATI Mobility Radeon X1300
GL_EXTENSIONS: GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.14a
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
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
X..GL_EXT_texture3D not found
X..GL_EXT_stencil_wrap not found
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
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

---

### Post by employeeno5 on 2007-10-29
So I think I discovered my problem. 
I had to install the xgl server to get all that fun compiz-fusion stuff to run. Apparently that doesn't allow my hardware to render 3D in certian other programs? I don't really quite understand it, but I know that once I un-installed the xgl server, both Doom3 and Google Earth (which also wasn't working) now run just fine. 


So I guess my new question is, is there any way around this? Is there any way for me temporarily disable the xgl server without removing and reinstalling it each time I want to do something that requires my 3d acceleration? Any programs that get around this virtually? 

Again, many thanks in advanced if you have any ideas.

---

### Post by frodon on 2007-11-12
You can run your game in another xserver, you will find the needed script there (advanced stuff section) :
[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

---

### Post by weblordpepe on 2007-11-12
Welcome to the world of ATi and Linux. You're suffering from what we in the community call 'sucky drivers'. I am in the same boat as you, but I have a 9600 graphics chip.

Basically, I don't use compiz and I use the restricted drivers provided by ATi. The Linux world is just sicky on ATi. On nVidia though, it's great. I can play movies on one part of the cube while Doom is on the other part of the cube.

Who says you can't game in Linux? :P

---

### Post by cold clock on 2008-01-13
> **employeeno5 said:**
> So I think I discovered my problem. 
I had to install the xgl server.
i think have the same problem as you had and i am a huge noob to linux how did you uninstall xgl server.

my situation is that i got a version of linux with loads of programs ready install and i guess it must have this xgl server on it. plz help:confused:

---

### Post by cooldude on 2008-01-13
you cannot play accelerated games with a composite window manager. Because that composite window manager is using the accelerated graphics card to give you all the cool effects. so trying to run a game over that the graphics card will overload. Best bet is to temporarily disable it. This is the way I do it.

Install gnome-compiz-manager

run the "compiz-tray-icon" program 

You will see a compiz symbol in your icon tray. Right click, select properties, unclick gleffects or what ever it says I cant remember. It will disable the xgl server. When you want to reenable, just click on the box.

---

