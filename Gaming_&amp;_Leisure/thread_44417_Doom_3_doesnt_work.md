---
title: "Doom 3 doesnt work"
date: 2005-06-26
forum: Gaming &amp; Leisure
---

### Post by DarkManX4lf on 2005-06-26
i downloaded the doom3 demo and i installed it fine but when i try to run it, in the terminal it says this


```
 

DOOM 1.1.1286 linux-x86 Nov 28 2004 20:09:31
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntu
local IP: 127.0.0.1
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3-demo/demo/demo00.pk4 with checksum 0xfe75bbef
Current search path:
/root/.doom3-demo/demo
/usr/local/games/doom3-demo/demo
/usr/local/games/doom3-demo/demo/demo00.pk4 (12234 files)
game DLL: 0x0 in pak: 0x0
file system initialized.
--------------------------------------

Running in restricted demo mode.

----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5151 strings read from strings/english.lang
Couldn't open journal files
couldn't exec editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5151 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "XFree86-DGA" missing on display ":0.0".
Failed to detect DGA DirectVideo Mouse
Free86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 8 Alpha bits, 16 depth, 8 stencil display.
GL_RENDERER: Mesa GLX Indirect
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
dlopen(libasound.so.2: cannot open shared object file: No such file or directory) failed:\uffffU
H\uffffU
@N\uffff

Alsa is not available
----------- Alsa Shutdown ------------
--------------------------------------
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother./dev/dsp - bit rate: 16, channels: 2, frequency: 44100
allocated a mix buffer of 16384 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
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
---------- R_Exp_Init -----------
Disabled at compile time.
---------------------------------
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
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()


```

i got my ati drivers installed fine i think and i get around 4000fps in glxgears....


anyone got any ideas on what i did wrong?

---

### Post by DarkManX4lf on 2005-06-26
also i wanted to ask if i buy the retail versions of doom3 and unreal tournament, can i j ust buy the windows versions? do they have linux installers on the windows disks?

---

### Post by tristan on 2005-06-26
[QUOTE=DarkManX4lf]also i wanted to ask if i buy the retail versions of doom3 and unreal tournament, can i j ust buy the windows versions? do they have linux installers on the windows disks?[/QUOTE]

Can't help you with your 1st post sorry...

You can only buy Doom3 as a windows version, which doesn't contain a linux installer. You need to download the linux Doom3 installer [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/), install it  and then manually copy the pak files from your Doom3 CDs to your linux box. It's not too difficult.

---

### Post by RadixLecti on 2005-06-29
I had the same problem.
I made sure I had all the .pak-files copied to the correct folder (/usr/local/games/doom3/base in my case, I think), and then ran the linux installer again. Not sure why that would work, though.

My biggest gripe was that I had to restart X every time I had played, the desktop was grossly enlarged. ;)

---

### Post by DarkManX4lf on 2005-06-29
i dont know what it is...i borrowed the retail version from a friend and it says the same error... i tried the demo version and it says the same error...maybe its the ati drivers?

---

### Post by songochain on 2005-07-13
I've the same problem and i've installed ati drivers correctly. I think it's a problem with ubuntu amd64 (maybe doing a symbolic link to this libraries it can fix our problem)
[Here]("http://songochain.eresmas.com/doom3") is my error

---

### Post by DarkManX4lf on 2005-07-13
sorry i have not updated this problem but i have it fixed, i installed the ati 8.14.13 drivers (located on their website) and it installed it and now doom3 runs fine.d


follw the first post on this thread

[http://ubuntuforums.org/showthread.php?t=32495&highlight=ATI+8.14.13](http://ubuntuforums.org/showthread.php?t=32495&highlight=ATI+8.14.13)

and then post number 85, those two will help you.

---

### Post by songochain on 2005-07-13
I've installed 8.14.13 driver, did u do any symbolic link?

---

### Post by DarkManX4lf on 2005-07-13
what do you mean by symbolic link ?  and did you follow post #85 in the thread ive given  you ?

---

### Post by songochain on 2005-07-13
I mean with to do ln -s .... to link some libraries
Yes I saw that post but i havent any problem loading fglrx module, i've 3D acceleration. With hoary i had the same problem with doom3 so i think that it's a problem with amd64 and some libraries
Thanks

---

### Post by Zeroedout on 2005-07-13
[QUOTE=DarkManX4lf]also i wanted to ask if i buy the retail versions of doom3 and unreal tournament, can i j ust buy the windows versions? do they have linux installers on the windows disks?[/QUOTE]

I have the retail version of UT2004 and yes, it does come with a linux installer, works, flawlessly too. With the help of [http://liflg.org/](http://liflg.org/) patching to the latest, and installing mods is extremly easy.

---

