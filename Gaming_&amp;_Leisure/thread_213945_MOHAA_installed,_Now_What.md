---
title: "MOHAA installed, Now What?"
date: 2006-07-12
forum: Gaming &amp; Leisure
---

### Post by EpicCrusadr on 2006-07-12
I am new to all things Linux, but I have to say that I am very impressed by Ubuntu. At the moment, I am trying to get Medal of Honor: Allied Assault installed natively using the installer found here:

[http://www.icculus.org/~ravage/mohaa/](http://www.icculus.org/~ravage/mohaa/)

The install seems to go fine, no errors and such (that I know of!). Then I can't figure out what to do next! :confused:  How do I run the game after it's installed?! Should there be a shortcut in the applications menu? When I run the file "mohaa" in the install directory some text pops up in the terminal, but vanishes again before I get a chance to read any of it. Any thoughts on my issue (or idiocy!) would be appreciated!

Thanks!

---

### Post by Sandlst on 2006-07-12
Open a terminal, then hit: Edit-Current Profile-Title and Command, at the bottom you can specify to leave the terminal open in the 'When Command Exits' section.  Try running the game again after this, it is probably giving you an error of some sort.

---

### Post by EpicCrusadr on 2006-07-12
Thanks for your help. This is what shows up in the terminal window:

--- Common Initialization ---
Medal of Honor Allied Assault 1.11 linux-i386 Sep  3 2004
----- FS_Startup -----
Current search path:
/home/anil/.mohaa/main
/home/anil/mohaa/main
/home/anil/mohaa/main/pak6.pk3 (104 files)
/home/anil/mohaa/main/pak5.pk3 (259 files)
/home/anil/mohaa/main/pak4.pk3 (593 files)
/home/anil/mohaa/main/pak3.pk3 (669 files)
/home/anil/mohaa/main/pak2.pk3 (4722 files)
/home/anil/mohaa/main/pak1.pk3 (772 files)
/home/anil/mohaa/main/pak0.pk3 (11175 files)

----------------------
18294 files in pk3 files
execing default.cfg
execing menu.cfg
couldn't exec newconfig.cfg
Config: unnamedsoldier.cfg
STUB: wtf in unix/linux_general_extras.c line 95.
STUB: wtf in unix/linux_general_extras.c line 101.
couldn't exec configs/unnamedsoldier.cfg
couldn't exec localized.cfg
execing autoexec.cfg
Unknown command "fov"
couldn't exec custom.cfg
You are now setup for easy mode.
----- Client Initialization -----
Called FadeSound with: 0.000000
----- Initializing Renderer ----
----- R_Init -----
...loading libGL.so: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).
SDL_GetError() reports "Could not load OpenGL library".
failed
...loading libMesaVoodooGL.so.3.1: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).SDL_GetError() reports "Could not load OpenGL library".
failed
ASSERT: [qcommon/common.c:406] GLimp_Init() - could not load OpenGL subsystem
 (fyi)
----- CL_Shutdown -----
-----------------------
Error: GLimp_Init() - could not load OpenGL subsystem

---

### Post by vem0m on 2006-07-13
do u have 3d acceleration active? as my Quake 3 did that when i was messing around with it without 3d acceleration active might check it

---

### Post by EpicCrusadr on 2006-07-13
I think I do... I typed the commands:

glxinfo |grep rendering
direct rendering: Yes

And the gears flowed smoothly when I typed:

glxgears

I don't know what's going on! ](*,) 

Here are some of my hardware specs. 

Pentium M 1.86 Ghz (Centrino)

1024Mb RAM 

Intel Integrated Graphics 915 (I know it's not the best but it should be able to run this game) 8) 

Running Ubuntu Dapper 

Thanks!

---

### Post by jinx099 on 2006-07-13
run glxgears again with the -printfps option and let us know about how many FPS you geton that.  Sometimes glxgears can be decieving.

---

### Post by vem0m on 2006-07-13
try typing glxinfo and tell me what it says as it still from log output seeming to be using mesa instead of nvidia drivers for ur card and from that i am presuming u have an nvida card right?

---

### Post by EpicCrusadr on 2006-07-13
Here is the output from glxgears:

anil@ubuntu:~$ glxgears -printfps
3928 frames in 5.0 seconds = 785.522 FPS
6973 frames in 5.0 seconds = 1394.393 FPS
4423 frames in 5.0 seconds = 884.512 FPS
3892 frames in 5.0 seconds = 778.371 FPS
3882 frames in 5.0 seconds = 776.266 FPS
3885 frames in 5.0 seconds = 776.991 FPS
3883 frames in 5.0 seconds = 776.478 FPS
3885 frames in 5.0 seconds = 776.876 FPS
7530 frames in 5.0 seconds = 1505.862 FPS
8211 frames in 5.0 seconds = 1642.133 FPS
7679 frames in 5.0 seconds = 1535.642 FPS
8640 frames in 5.0 seconds = 1727.895 FPS
8318 frames in 5.0 seconds = 1663.464 FPS
8483 frames in 5.0 seconds = 1696.457 FPS
8277 frames in 5.0 seconds = 1655.295 FPS
8615 frames in 5.0 seconds = 1722.992 FPS

The frames/second seemed to jump up for some reason (processor stepping?) so I tried it a second time. The second time it stayed around 800 fps.

Here is glxinfo:

anil@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

@ ven0m I actually have integrated graphics (intel 915) NOT nvidia

---

### Post by vem0m on 2006-07-14
well either way it is using mesa drivers u might look on the net and see if u can find linux driver for that chip

also would reccommend to play any games get a real GFX card I prefer and recommend ATi :)

---

### Post by EpicCrusadr on 2006-07-14
I have drivers for my chipset installed.

This is what my xorg.conf says:

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"

Though it is not the same as in this post:

[http://ubuntuforums.org/showpost.php?p=1206016&postcount=3](http://ubuntuforums.org/showpost.php?p=1206016&postcount=3)

I think I might still be using a generic driver. 

When I try to view my xorg.conf using the terminal I get this and a blank gedit window pops up.

anil@ubuntu:~$ gksudo gedit /ect/X11/xorg.conf

(gedit:16168): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


(I'm sure i typed in my password correctly) I can still see my xorg.conf by going through directories graphically, but it is read-only.

Sorry I'm such a newbie! I don't know what to do. :(

---

### Post by jharris on 2006-07-14
> **EpicCrusadr said:**
> Thanks for your help. This is what shows up in the terminal window:

--- Common Initialization ---
Medal of Honor Allied Assault 1.11 linux-i386 Sep  3 2004
----- FS_Startup -----
Current search path:
/home/anil/.mohaa/main
/home/anil/mohaa/main
/home/anil/mohaa/main/pak6.pk3 (104 files)
/home/anil/mohaa/main/pak5.pk3 (259 files)
/home/anil/mohaa/main/pak4.pk3 (593 files)
/home/anil/mohaa/main/pak3.pk3 (669 files)
/home/anil/mohaa/main/pak2.pk3 (4722 files)
/home/anil/mohaa/main/pak1.pk3 (772 files)
/home/anil/mohaa/main/pak0.pk3 (11175 files)

----------------------
18294 files in pk3 files
execing default.cfg
execing menu.cfg
couldn't exec newconfig.cfg
Config: unnamedsoldier.cfg
STUB: wtf in unix/linux_general_extras.c line 95.
STUB: wtf in unix/linux_general_extras.c line 101.
couldn't exec configs/unnamedsoldier.cfg
couldn't exec localized.cfg
execing autoexec.cfg
Unknown command "fov"
couldn't exec custom.cfg
You are now setup for easy mode.
----- Client Initialization -----
Called FadeSound with: 0.000000
----- Initializing Renderer ----
----- R_Init -----
...loading libGL.so: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).
SDL_GetError() reports "Could not load OpenGL library".
failed
...loading libMesaVoodooGL.so.3.1: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).SDL_GetError() reports "Could not load OpenGL library".
failed
ASSERT: [qcommon/common.c:406] GLimp_Init() - could not load OpenGL subsystem
 (fyi)
----- CL_Shutdown -----
-----------------------
Error: GLimp_Init() - could not load OpenGL subsystem
I received the same error when installing MOHAA. However, Doom 3, ET and all my other games all work fine. I can post my output if required and yes, my Nvidia drivers are installed correctly. If anyone could help I'd be most appreciative.

---

### Post by vem0m on 2006-07-14
do u guys have the SDL and GL libs installed also, yes u are still using generic drivers u need to find linux one off the net but i would still recommend a new video card to do anykind of gamming on linux.

---

### Post by LKRaider on 2006-07-14
Check the contents of this folder:
```
ls /usr/lib/ |grep GL
```

and try renaming the following files:
```
mv /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.bak
mv /usr/lib/libGLcore.so.1 /usr/lib/libGLcore.so.1.bak
```

Then try running the game again.

If still doesn't work, try this folder:
```
ls /usr/lib/tls
```

if there is anything there, try renaming them to .bak (or moving them to another folder).

---

### Post by EpicCrusadr on 2006-07-14
It is not possible for me to get a dedicated graphics card, as I am using a laptop :( , but if I could, I would.

Apparently, I dont have the "/usr/lib/tls" directory nor the "/usr/lib/libGLcore.so.1" (That could be a problem). 

I tried doing what you said and MOHAA still gave me the error, but now neverputt doesn't work! ](*,)  I changed it back and it works again. :) 

3d games like Briquolo and neverputt work like a charm, but for some reason MOHAA doesn't want to!

Thanks again for all your help! The Ubuntu Forums are a really great resource, and the only reason that is true is because of all the great people who contribute! :-D

---

### Post by vem0m on 2006-07-14
hmmmmm well sux to be u :P

---

### Post by EpicCrusadr on 2006-07-19
Is anyone else having problems like this?

---

### Post by Sandlst on 2006-07-19
I don't know enough to be much help, but i noticed in your previous post about getting a blank xorg.conf, you were misspelling the path....should be ```
sudo gedit /[COLOR="Red"]etc[/COLOR]/X11/xorg.conf
``` Also, have you tried just using sudo instead of gksudo?  I ran into your same error using gksudo, but plain sudo works here, maybe theres some special setup you have?

---

### Post by EpicCrusadr on 2006-07-20
thanks for the tip Sandlst. I can't believe I didn't catch that!

---

### Post by Matt Danger on 2006-10-27
> **jharris said:**
> I received the same error when installing MOHAA. However, Doom 3, ET and all my other games all work fine. I can post my output if required and yes, my Nvidia drivers are installed correctly. If anyone could help I'd be most appreciative.

> **EpicCrusadr said:**
> Thanks for your help. This is what shows up in the terminal window:

--- Common Initialization ---
Medal of Honor Allied Assault 1.11 linux-i386 Sep  3 2004
----- FS_Startup -----
Current search path:
/home/anil/.mohaa/main
/home/anil/mohaa/main
/home/anil/mohaa/main/pak6.pk3 (104 files)
/home/anil/mohaa/main/pak5.pk3 (259 files)
/home/anil/mohaa/main/pak4.pk3 (593 files)
/home/anil/mohaa/main/pak3.pk3 (669 files)
/home/anil/mohaa/main/pak2.pk3 (4722 files)
/home/anil/mohaa/main/pak1.pk3 (772 files)
/home/anil/mohaa/main/pak0.pk3 (11175 files)

----------------------
18294 files in pk3 files
execing default.cfg
execing menu.cfg
couldn't exec newconfig.cfg
Config: unnamedsoldier.cfg
STUB: wtf in unix/linux_general_extras.c line 95.
STUB: wtf in unix/linux_general_extras.c line 101.
couldn't exec configs/unnamedsoldier.cfg
couldn't exec localized.cfg
execing autoexec.cfg
Unknown command "fov"
couldn't exec custom.cfg
You are now setup for easy mode.
----- Client Initialization -----
Called FadeSound with: 0.000000
----- Initializing Renderer ----
----- R_Init -----
...loading libGL.so: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).
SDL_GetError() reports "Could not load OpenGL library".
failed
...loading libMesaVoodooGL.so.3.1: SDL: SDL_GL_LoadLibrary() failed! rc == (-1).SDL_GetError() reports "Could not load OpenGL library".
failed
ASSERT: [qcommon/common.c:406] GLimp_Init() - could not load OpenGL subsystem
 (fyi)
----- CL_Shutdown -----
-----------------------
Error: GLimp_Init() - could not load OpenGL subsystem
Try
```
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
```

I'm not sure the ramification's of this but it gets the game to load at least.

---

### Post by peterson23 on 2006-10-28
i agree with epiccrusadr

---

### Post by Malac on 2007-01-03
> **Matt Danger said:**
> Try
```
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
```I'm not sure the ramification's of this but it gets the game to load at least.
Instead of making a hard link just change the launch command for mohaa to this, it worked for me.
```
[COLOR=DimGray]*<path to where file is>*[/COLOR]/mohaa +set r_gldriver libGL.so.1
```Hope this helps.

---

### Post by Ajaxus on 2008-04-19
I know this is an old thread, but thought I would share my experience here for 'those who will follow'.

If you get these messages all is well, I repeat, all is well - simply pop the MOHAA disk 1 into your DVD/CDRom drive and run mohaa_lnx from your mohaa directory! Worked for me.:lolflag:

Ajaxus

---

