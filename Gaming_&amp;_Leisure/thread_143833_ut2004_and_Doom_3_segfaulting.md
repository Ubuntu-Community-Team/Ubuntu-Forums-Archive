---
title: "ut2004 and Doom 3 segfaulting"
date: 2006-03-13
forum: Gaming &amp; Leisure
---

### Post by sorcererx84 on 2006-03-13
Ut2004 and Doom 3 Demo both used to run OK but now both are crashing with a segmentation fault.

I can play ut for a minute or so and then it crashes with the following message:
```
$ ut2004
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Signal: SIGSEGV [segmentation fault]
Aborting.


Crash information will be saved to your logfile.

```

Doom 3 demo doesn`t run at all:
```
$ doom3-demo
DOOM 1.1.1282 linux-x86 Oct  4 2004 08:27:55
Hostname: localhost.localdomain
Alias: localhost
Alias: gecko2
IP: 127.0.0.1
------ Initializing File System ------
Loaded pk4 /home/hendrik/doom3-demo/demo/demo00.pk4 with checksum 0x93fac1e4
Current search path:
/home/hendrik/.doom3-demo/demo
/home/hendrik/doom3-demo/demo
/home/hendrik/doom3-demo/demo/demo00.pk4 (12234 files)
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
execing autoexec.cfg
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
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: Mesa GLX Indirect
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
----------- OSS Sound Initialization -----------
opened sound device '/dev/dsp'
/dev/dsp - bit rate: 16, channels: 2, frequency: 44100
WARNING: mmap 32768 bytes on device /dev/dsp failed: Input/output error

close sound device
WARNING: sound subsystem disabled

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
idRenderSystem::Shutdown()

```

---

### Post by BradChandler on 2006-03-14
The doom3 demo crashes a lot for me. Sometimes I can play for a while before it crashes, sometimes I can only play for a few seconds. There doesn't seem to be a pattern to how or when it crashes. I'm not sure if it's a hardware or software problem, but what is your hardware like? I've got an AMD 4200 X2 and a 7800GT. If it's a hardware problem, I thought it might have something to do with the dual core cpu or the video card. 

Aside from doom3, I haven't had any problems with this computer.

---

### Post by sorcererx84 on 2006-03-14
I have an Amilo M 7440G 1.6 Ghz laptop with i915 integrated graphics. I have installed the 20060107 DRI snapshots for i915 and direct rendering is working. I think it is related to software because I have played both of them previously on the same computer.

---

### Post by ubernoob on 2006-04-09
I had the same problem as you with doom 3.
WARNING: vertex array range in virtual memory (SLOW) indicates that your graphic drivers aren't installed / configured correctly.

"glxinfo | grep rendering" will probably give you "direct rendering: No"

---

### Post by cayalee on 2006-04-09
no, mine comes back as rendering yes. i have these sigsev errors on ut2003 and on americas army. everything is installed correctly and running, just randomly crashes with signal 11 sigsev. warsow (another 3d fps game) works fine.. quite baffled

---

### Post by ubernoob on 2006-04-09
what does glxgears -printfps give?

---

### Post by sorcererx84 on 2006-04-10
Installing libsdl1.2debian-alsa fixes the Doom 3 segfault. It is a problem on many debian-based distributions.
I looked for an ut2004 segfault bug in [icculus.org bugzilla]("https://bugzilla.icculus.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=Unreal+Tournament+2004&content=") and there is a bunch of them there.

To ubernoob: How did you fix the WARNING: vertex array range in virtual memory (SLOW) error?

---

### Post by ubernoob on 2006-04-10
i had installed xgl which made my nvidia drivers not support direct rendering. I disabled xgl and installed nvidia drivers all over again. That fixed my problem. I guess your problem might be something with the graphical drivers. check:
glxgears -printfps
glxinfo | grep rendering

and tell us what the output gives.

---

### Post by Jedeye on 2006-04-10
[QUOTE=ubernoob]i had installed xgl which made my nvidia drivers not support direct rendering. I disabled xgl and installed nvidia drivers all over again. That fixed my problem. I guess your problem might be something with the graphical drivers. check:
glxgears -printfps
glxinfo | grep rendering

and tell us what the output gives.[/QUOTE]
Is there a easy way to enable and disable xgl?

---

### Post by ubernoob on 2006-04-10
If you do this, you will lose all unsaved data (since you are restarting the x-server) You might want to log out before doing this:

disabling:

ctrl + alt + f1
sudo mv /etc/gdm/gdm.conf-custom /root/
sudo /etc/init.d/gdm restart

enabling:

ctrl + alt + f1
sudo mv /root/gdm.conf-custom /etc/gdm/
sudo /etc/init.d/gdm restart

---

### Post by cayalee on 2006-04-10
mine gives direct rendering as yes and fps as 1121.
still get the sigsev on americas army and ut2003
not using xgl, just plain ubuntu on gnome.
eve if i disable gdesklets and amarok from running in background it still crashes out sigsev

---

### Post by sorcererx84 on 2006-04-11
I have direct rendering enabled, glxgears gives about 1200 fps.

---

### Post by Ferrat on 2006-04-11
Here is a great thread that might help you guys to get the render right =)

[http://www.ubuntuforums.org/showthread.php?t=143283&highlight=install+xgl+ati](http://www.ubuntuforums.org/showthread.php?t=143283&highlight=install+xgl+ati)

---

### Post by Jedeye on 2006-04-11
[QUOTE=ubernoob]If you do this, you will lose all unsaved data (since you are restarting the x-server) You might want to log out before doing this:

disabling:

ctrl + alt + f1
sudo mv /etc/gdm/gdm.conf-custom /root/
sudo /etc/init.d/gdm restart

enabling:

ctrl + alt + f1
sudo mv /root/gdm.conf-custom /etc/gdm/
sudo /etc/init.d/gdm restart[/QUOTE]

Thanks! that worked like a charm!!!! Now I can run Quake 4 when I want, and have xgl when I want!

---

### Post by ubernoob on 2006-04-14
direct rendering: yes and glxgears around 1000? Then i would have had another look at the drivers.

Mine glxgears gives around 7700... What kind of drivers do you use? And what kind of graphical card? Nvidia or Ati?

Edit: And do you use Dapper or Breezy? Changing to dapper might help.

---

### Post by sorcererx84 on 2006-04-15
I am using i915gm with 20060107 snapshots and Breezy.

---

### Post by ubernoob on 2006-04-15
[QUOTE=sorcererx84]I am using i915gm with 20060107 snapshots and Breezy.[/QUOTE]

Isn't that a motherboard? And if you are using the onboard graphics, no wonder you don't get it to work. The onboard graphics are meant for desktop use, not for gaming. [this test]("http://www.motherboards.org/reviews/motherboards/1576_4.html") shows that you will get 3 FPS in doom3 (in windows). So you can't blame this on linux.

 I would suggest buying a nvidia graphic card.

---

### Post by ravenpi on 2010-01-19
It turns out that the problem lies with the order in which the 32-bit X libraries are looked for on 64-bit systems.  I don't quite understand all the mechanics, but -- AND THIS WILL NOT WORK FOR XFree86 INSTALLS (vs. X.org installs, which is what Ubuntu has had by default for some years now) -- here's what I've done to get it going.  Fairly simple, really; just add
export LIBGL_DRIVERS_DIR=/usr/lib32/dri
to the doom3 wrapper script found at /usr/local/games/doom3/doom3.  

Note that you'll need to edit this as root, e.g., 
sudo gedit /usr/local/games/doom3/doom3
Additionally, add it just below the lines that start with hashes.  My current file looks like this:

#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/doom3/"
export LIBGL_DRIVERS_DIR=/usr/lib32/dri
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
exec ./doom.x86 "$@"

---

