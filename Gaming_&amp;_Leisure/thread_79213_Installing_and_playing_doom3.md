---
title: "Installing and playing doom3"
date: 2005-10-19
forum: Gaming &amp; Leisure
---

### Post by floyd27 on 2005-10-19
I installed the game and tried to run it but i get an error...

roderick@ubuntu:~$ sudo doom3
DOOM 1.1.1286 linux-x86 Nov 24 2004 17:56:04
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntu
local IP: 127.0.0.1
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0x7dafc4d4
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x16cf3b8a
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Current search path:
/home/roderick/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg
roderick@ubuntu:~$

Can someone help...First time running a gmae on linux...:)

---

### Post by red_plague on 2005-10-24
Can't help much there(don't have doom3 and my glxgears=50), but it seems that the game is missing some config file: default.cfg
 See in the manual or in the README's  if they say anything about creating a config file in $HOME.
 Your system should be able to play doom3 with no problem, so it's a config thing.

---

### Post by Staesys on 2005-10-24
Everything I've researched says it either has something to do with the video card drivers or a no cd crack/patch. One person said that reinstalling their (latest update) video card drivers fixed it.

I have Doom 3 for windows, I just haven't tried installing it on Linux yet. Sounds like a project...  I have the Linux native UT2004 Demo installed though and it works just fine.

---

### Post by Staesys on 2005-10-24
Well, I just installed it. I downloaded the Linux files and copied over my pak files from my XP machine. It runs, although I have to start it out with **doom3 +set s_driver oss** or the sound is crap.

I have major performance issues though. I've set everything to it's lowest setting, but still the frame rate sucks. My video card is the same one I used to have in my XP box and it ran just fine under windows. The only real difference here is that this machine is running Linux, is .93 GHz slower and has only 256MB of RAM, where as the XP box has 1GB of RAM.

Any one have an idea of how to speed this game up?

---

### Post by .jon on 2005-10-24
I have a problem with my Doom3 install as well. Maybe I don't have the correct opengl or drivers installed. 

EDIT: Installed ATI Drivers, and it did not fix the problem. 

```

jon@ubuntu:~$ doom3
DOOM 1.1.1282 linux-x86 Oct  4 2004 08:21:14
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntu
IP: 127.0.0.1
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0x7dafc4d4
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x16cf3b8a
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Current search path:
/home/jon/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
/proc/cpuinfo CPU frequency: 2079.89 MHz
guessing video ram ( use +set sys_videoRam to force ) ..
guess failed, return default low-end VRAM setting ( 64MB VRAM )
Detected
        2.08 GHz CPU
        1008 MB of System memory
        64 MB of Video memory on an optimal video architecture

This system qualifies for Low quality.
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5151 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5151 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
dlopen(libGL.so.1)
Open X display
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 8 Alpha bits, 16 depth, 8 stencil display.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
GL_RENDERER: Mesa GLX Indirect
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
----------- OSS Sound Initialization -----------
opened sound device '/dev/dsp'
/dev/dsp - bit rate: 16, channels: 2, frequency: 44100
------------------------------------------------
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
---------- R_Exp_Init -----------
Disabled at compile time.
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/test.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_VERTEX_PROGRAM_ARB not availableglprogs/bumpyEnvironment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/shadow.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/R200_interaction.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_bumpAndLight.vp: GL_VERTEX_PROGRAM_ARB not availableglprogs/nv20_diffuseColor.vp: GL_VERTEX_PROGRAM_ARB not availableglprogs/nv20_specularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseAndSpecularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- OSS Sound Shutdown -----------
unmap dma sound buffer
close sound device
------------------------------------------
idRenderSystem::Shutdown()

```

---

### Post by Staesys on 2005-10-25
Just for comparison, I just installed Quake 3 Arena and I'm running it at 1024x768 with all the defaults turned on and it's like glass.

---

### Post by Staesys on 2005-10-25
> signal caught: Segmentation fault

I think this is the real problem, and why it is shutting down on you.

It appears that it's the sound driver that's doing the damage. Try starting Doom 3 with this 

**doom3 +set s_driver oss** 

and see if that fixes it.

---

### Post by Staesys on 2005-10-25
On my computer, depending on what is happening in the game, my FPS can range from a high of 56fps to a low of 5fps. The average fps I get is somewhere in the 10-15 fps range. This basically means the game is unplayable. I'm using the linux native install files from id Software also. I've played Doom 3 on my XP box and the frame rate was much very good/fast. I found a decent tweak guide at [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54") but it hasn't helped much. Perhaps when I upgrade to 512MB RAM?

Anyone have any ideas?

---

### Post by floyd27 on 2005-10-25
the linux ATI drivers are garbage...
I get chopy play with a 9700 pro.......

I doubt any more ram wil help the situation...

---

### Post by .jon on 2005-10-25
[QUOTE=Staesys]
**doom3 +set s_driver oss** 
[/QUOTE]

That did not solve the problem, but thanks for the suggestion.

---

### Post by .jon on 2005-10-25
I got it working finally. It had to do with setting the ATI drivers up correctly. That only took about 2 hours to do, but I learned some more about linux in the process. This is my first linux install. I also got UT2004 working right.

EDIT: Actually the sound does not work, even when I run with the OSS emulation. I'm working on that now and will update. It doesn't work in UT2004 either. The sound does work in gaim however.

EDIT2: Sound works now. I switched to onboard sound and updated drivers.

---

