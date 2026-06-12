---
title: "Doom 3 is busted"
date: 2006-05-25
forum: Gaming &amp; Leisure
---

### Post by Phil_McCrackin on 2006-05-25
Just installed Doom 3. Followed the the directions on the doom3 front page to the letter. Everything seemed to go just fine but when I run it, I get this...
```
theadmin@scab:~$ doom3
DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.10.106/255.255.255.0
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
/home/theadmin/.doom3/base
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
Using 4/4/4 Color bits, 8 Alpha bits, 16 depth, 8 stencil display.
GL_RENDERER: Mesa GLX Indirect
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.10
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

```

I have searched the forums and found a few threads with similar issues but no resolution. I have had zero success in installing any game and it's a bit frustrating.

I have checked xorg.conf and everything seems to be in order. I have very freshly installed NVIDIA drivers declared properly. 

Any ideas? Anyone?
Thanks in advance, 
-Phil

AMD 64FX-55
2x NVIDIA 6800GTs in SLI
Biostar TForce nf4

---

### Post by sorcererx84 on 2006-05-25
I had the same problem when I was using Breezy. Install libsdl1.2debian-alsa.

---

### Post by minisori on 2006-05-25
Seem you dont have the 3D aceleration working properly.

Try to run in a terminal glxinfo and post the result here.

---

### Post by Phil_McCrackin on 2006-05-25
I actuall already have libsdl1.2debian-alsa installed.

Oh! By the way I am using Dapper Drake Beta 2 now (need to change that in my pro)

here are the results from glxinfo:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x25 16 tc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x26 16 tc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x27 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x29 16 dc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x2a 16 dc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None

```

Thank you for looking at this!

---

### Post by sorcererx84 on 2006-05-25
I tried it now and also get a segfault in Dapper.

---

### Post by minisori on 2006-05-25
You dont have any 3d acleration. You should instal de nvidia-glx drivers in the repos. If im not missing anything this should be enought:

$ sudo apt-get linux-restrcited-modules-`uname -r` nvidia-glx nvidia-kernel-common

If every was ok then you have to run:
$ sudo nvidia-glx-config enable
This will change your xorg.conf, so next time you restart it will use the new driver.

NOTE: make a copy of your /etc/X11/xorg.conf before, just in case you have any problem.

---

### Post by Phil_McCrackin on 2006-05-25
after I enter: $ sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx nvidia-kernel-common


edit: noticed install was missing from code above

now I get:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-restricted-modules-2.6.15-23-386nvidia-glx

---

### Post by minisori on 2006-05-25
[QUOTE=Phil_McCrackin]after I enter: $ sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx nvidia-kernel-common


edit: noticed install was missing from code above
[/QUOTE]

Right i forgot it, this is the right one as you wrote:
$ sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx nvidia-kernel-common

> now I get:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-restricted-modules-2.6.15-23-386nvidia-glx

Notice the output, you wrote it together. You must install these packages:
linux-restricted-modules-`uname -r`
nvidia-glx
nvidia-kernel-common

---

### Post by Phil_McCrackin on 2006-05-25
actually, I did get them installed. for some reason my edit didn't take. anyway after I rebooted the x server failed to start. Everything in xorg looks okay. Is there some info that might help. There is so much I can't type it all out (well I could, but I don't know what's relevant) and I can't copy and paste from recovery.

---

### Post by minisori on 2006-05-25
Did you run this?

$ sudo nvidia-glx-config enable

Also check if the nvidia module is loaded:
$ lsmod | grep nvidia

You should get something like this:
agpgart                37072  2 nvidia,via_agp

If not then try:
$ sudo modprobe nvidia

Now you would get something like that after do lsmod | grep nvidia if everything when ok. If so then open the file "/etc/modules" and check there is a line wich sais nvidia, if not add it at the end.

Also check in the xorg.conf in section "Device", it says Driver "nvidia" instead of Driver "nv";

Restart the xserver or do sudo X :1 -ac to open another x and cross your fingers :P

You can post the messages you get from the xserver log wich are refered to nvidia.

---

### Post by Phil_McCrackin on 2006-05-25
Well, after running what you asked, it seems I have a couple of problems. First, which is not really a suprize, 
(WW) No matching Device section for instance (BusID PCI:5:0:0) found
-this card was not listed after install of breezy or dapper and my video after boot would switch to the card in slot 4 (which 5 is where is should be). so I added the card (which is the exact same card as in slot 4) and, presto! I have video out of the correct port. I had noticed an error on boot to do with PCI something, but it runs so fast I could not see it. However, I do not think this is why xserver failed

Error: API mismatch: the NVIDIA kernel module has the version 1.0-8756, but this X module has the version 1.0-8762. Please make sure that the kernel module and all NVIDIA driver components have the same version.

THIS is why x server is not working here (I think). It would seem it's not always the most auspicious thing to have the very LATEST driver-lol. Well, I wouldn't have a clue as to how to install the 8762 driver from command. I'm sitting here looking at the driver on the windows site from my  *cough* XP *cough* laptop. 

everything else that you said to check seems kosher. So how do I get out of this mess?:neutral:
How do I download something from a site from the command line. If I can do that, I can install the driver.


Thanks again for all your help and patience.

---

### Post by minisori on 2006-05-26
[QUOTE=Phil_McCrackin]Error: API mismatch: the NVIDIA kernel module has the version 1.0-8756, but this X module has the version 1.0-8762. Please make sure that the kernel module and all NVIDIA driver components have the same version.[/QUOTE]

Yes that is the thing you have to use both the same version.

Linux restricted modules and nvidia glx from repos, both have the version 1.0-8756, you should not have problem if installing both from repos, if those drives detect your card and all that

---

### Post by leech on 2006-05-26
This is actually pretty easy to do.  Firstly, you could either download the newest driver (which it sounds like you already did) for linux, either from within Windows and then read your ntfs partition from within Linux.  If you installed from Dapper Beta 2, it should be in /media/hdxx (where xx is your hard drive and partition number, for example if you have two hard drives and your windows drive is on your second drive, first partition, it'll be hdb1.  Or if your windows drive is on your first drive second partition it's hda2.  Unless you have multiple hard drives/partitions then it should just be the only hd folder in /media.)

Or you can use ```
wget ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8762/NVIDIA-Linux-x86-1.0-8762-pkg1.run[/code

or [code] wget ftp://download.nvidia.com/XFree86/Linux-x86_64/NVIDIA-Linux-x86_64-1.0-8762-pkg2.run
```

Then make sure your kernel headers are set up right ```
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-headers-'uname-r' /usr/src/linux
```

Then just ```
 sh NVIDIA-Linux-x86-1.0-8762-pkg1.run
``` or the 64 bit one if you're running that.  Then after that, do as the previous advice stated and make sure the "nv" is changed to "nvidia" in xorg.conf

Leech

---

### Post by minisori on 2006-05-26
Yeah, just seem you have messed both versions, using the restricted modules from repos and the x driver from nvidia.

---

