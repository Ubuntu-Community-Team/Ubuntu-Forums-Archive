---
title: "Doom 3 choppy on good hardware"
date: 2009-10-29
forum: Gaming &amp; Leisure
---

### Post by ShadowTek on 2009-10-29
I installed Doom 3 from the Windows CDs using doom3-linux-1.3.1.1304.x86.run from ID's website. The game will run, but it's choppy, even on low video settings. I set the audio to use OSS, and that helped a little, but it's still intolerable.

Can someone suggest something to improve the FPS?

This is a bit silly, considering that I'm using an e7500 2.92GHz Core2 Duo with a 9600GT and 4GBs of DDR2.

I also using Karmic with the proprietary nVidia drivers.

---

### Post by RichardLinx on 2009-10-29
Have you tried disabling compositing effects (ie. Compiz) before running the game?

---

### Post by joeelmex on 2009-10-29
I disabled all effects and play with them off to avoid any issues.  I just leave them off now.  The other thing I do is I removed the ubuntu nvidia drivers and download the latest one from Nvidia.com .  I saw some improvement on fps also doing that.

---

### Post by ShadowTek on 2009-10-29
I've set "Visual Effects" to "None".

I've uninstalled the proprietary nVidia drivers from the package manager, rebooted to CLI, and installed driver 190.42 from nVidia's site.

I've tried "nice -n19 doom3", "sudo nice -n19 doom3", nice -n-20 doom3", and "sudo nice -n-20 doom3".

Nothing is making a difference; it's still choppy, and I even have it set to the lowest resolution setting. :/

Any other ideas?

---

### Post by ShadowTek on 2009-11-01
I decided to try different operating systems. I installed Debian Lenny 64bit, went through the lengthy process of installing the nVidia driver's the "Debian way", and was finally greeted with a seg-fault when I tried to run doom3. I then tried installing Gentoo, patiently working my way through the whole guided, manual-install process. But I hit a brick wall when the kernel wouldn't compile. I then tried Ubuntu 9.10 32bit, as I was using 64bit before, and I finally managed to get doom3 to run smoothly.

Apparently, OSS sound is the only reasonable option with doom3, as ALSA crackles and pops intolerably. The odd thing that I discovered is that trying to use OSS is that using surround-sound will result in jerky video. So, it seems that the only real option for running doom3 on Linux is to only use OSS in stereo.

I'm not sure if that was the only problem with my Ubuntu 9.10 64bit, or if it was something else. I tried to go back and test, as I still have that partition intact, but I apparently screwed up the video drivers so bad while poking around that I can't even get the recovery console to load.

I wish I could get surround-sound to work without causing the video to lag. :/

---

### Post by Brebs on 2009-11-01
Sounds like a bug with ALSA. Does this work:

```
speaker-test -D surround51 -c 6 -t wav
```

See [thread](http://www.fedoraforum.org/forum/showthread.php?p=1083991#post1083991) for a bit of debugging info.

---

### Post by ShadowTek on 2009-11-02
I only have a 4.0 speaker system, but they did work properly in the test.

Debug output is here:
[http://www.alsa-project.org/db/?f=a5fed3867d153d8d69acc71bf74d342afdf5d9da](http://www.alsa-project.org/db/?f=a5fed3867d153d8d69acc71bf74d342afdf5d9da)

---

### Post by Brebs on 2009-11-02
Try tweaking ALSA for Doom3, e.g. I have in ~/.asoundrc

```
pcm.doom3 {
    type plug
    slave.pcm {
        type dmix
        ipc_key 1093  # Must be unique
        ipc_key_add_uid false
        ipc_perm 0660
        slave {
            pcm "hw:0,0"
            rate 44100
            channels 2
            period_time 0
            period_size 1024
            buffer_time 0
            # Doom 3 wants buffer_size 8192
            # In ~/.doom3/base/autoexec.cfg
            # And ~/.quake4/q4base/autoexec.cfg
            # seta s_alsa_pcm "doom3"
            buffer_size 8192
        }
    }
}
```

And in ~/.doom3/base/autoexec.cfg

```
seta s_driver "alsa"
seta s_alsa_pcm "doom3"

```

There is also the additional channel mixup problem below, for you to merge in:

```
# Channels are wrong way around in doom! This fixes them.
# http://www.linuxforen.de/forums/archive/index.php/t-206470.html
# http://forums.seriouszone.com/showthread.php?t=49869&page=10
# http://forums.gentoo.org/viewtopic-p-4173170.html#4173170
pcm.doom-surround51 {
    slave.pcm surround51
    slave.channels 6
    type route
    ttable.0.0 1
    ttable.1.1 1
    ttable.2.4 1
    ttable.3.5 1
    ttable.4.2 1
    ttable.5.3 1
}
```

---

### Post by joeelmex on 2009-11-02
I run Doom3 fine with AlSA but I am still running 9.04 64 bit.  Thats very odd with what you saw, in your situation.  Was it a clean install or upgrade?

---

### Post by ShadowTek on 2009-11-02
I didn't test it for very long, but the clicks and pops weren't noticeable. The big problem that I noticed is you can't hear certain sounds from the rear speakers very well. For instance, I can hear the thrusts from the transport engine just fine at the start of the game, but I can just *barely* hear the soldier's voice if I turn my back on him. Simply turning up the volume woudn't work, since all the other sounds would be too lound. 

> And in ~/.doom3/base/autoexec.cfg
That didn't set a_alsa_pcm. I tried to set it manually in-game, but it didn't make any noticeable difference, and the variable was reset after rebooting doom3.

> I run Doom3 fine with AlSA but I am still running 9.04 64 bit. Thats very odd with what you saw, in your situation. Was it a clean install or upgrade?
It was a clean install of the beta.

---

### Post by Brebs on 2009-11-02
> **ShadowTek said:**
> I can just *barely* hear the soldier's voice if I turn my back on him
This is because the surround channels are wrong in Doom - see the links in my post above, and use ~/.asoundrc to fix it.


> That didn't set a_alsa_pcm
What? It's s_alsa_pcm. Use seta ("set always") instead of set if you like.

---

### Post by ShadowTek on 2009-11-02
> It's s_alsa_pcmOh, I guess it was a typo.

What is .asoundrc supposed to look like when the 2 components you showed are "merged? I don't think I'm doing it correctly since nothing has changed.

If I try to set s_alsa_ocm to "doom-surround51", it fails with when the buffer size isn't specified. If I copy the buffer size over to doom-surround51, doom3's sound fails by saying that doom-surround51 is an invalid argument.

---

### Post by Brebs on 2009-11-02
Try this:

```
pcm.doom3-surround51 {
	slave.pcm doom3
	slave.channels 6
	type route
	ttable.0.0 1
	ttable.1.1 1
	ttable.2.4 1
	ttable.3.5 1
	ttable.4.2 1
	ttable.5.3 1
}


pcm.doom3 {
	type plug
	slave.pcm {
		type dmix
		ipc_key 1093  # Must be unique
		ipc_key_add_uid false
		ipc_perm 0660
		slave {
			pcm "hw:0,0"
			rate 44100
			period_time 0
			period_size 1024
			buffer_time 0
			# Doom 3 wants buffer_size 8192
			# In ~/.doom3/base/autoexec.cfg
			# And ~/.quake4/q4base/autoexec.cfg
			# seta s_alsa_pcm "doom3"
			buffer_size 8192
		}
	}
}

```

And in autoexec.cfg
```
seta s_numberOfSpeakers "6"
seta s_driver "alsa"
seta s_alsa_pcm "doom3-surround51"
```

---

### Post by ShadowTek on 2009-11-02
I finally got the sound to work. I think the problem was that the .asoundrc file was corrupted in some way. I created a new file with vim, and that seemed to solve *that* problem.

Now, I have the sound working, but the problem with now being able to hear the soldier right behind me is still exactly the same as before. I can be right in the guy's face, turn my back to him, and his voice is extremely distant in the rear speakers.

Got any other ideas?

Here's my most recent terminal output:
```
~$ doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 192.168.1.2/255.255.255.0
found interface tun0 - 10.10.12.82/255.255.255.255
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
/home/shadowtek/.doom3/base
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
execing autoexec.cfg
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
Free86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce 9600 GT/PCI/SSE2
GL_EXTENSIONS: GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_instanced GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_framebuffer_object GL_ARB_geometry_shader4 GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NV_vertex_buffer_unified_memory GL_NV_shader_buffer_load GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.20
opened Alsa PCM device doom3-surround51 for playback
device buffer size: 6144 frames ( 73728 bytes )
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
copy gamex86.so to /home/shadowtek/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Jan 16 2007
Initializing event system
...473 event definitions
Initializing class hierarchy
...142 classes, 382184 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 1600 MHz
Compiled 'removeInitialSplineAngles': 1374.7 ms
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
pid: 3914
4032 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
found XNVCtrl extension 1.18
512 MB Video Memory
Async thread started
guid set to u1TC6/B1Cko
--------- Game Map Shutdown ----------
--------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------
shutdown terminal support

```

---

### Post by Brebs on 2009-11-02
Your ~/.asoundrc is badly formatted:
```
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:36:0:Unexpected char
ALSA lib conf.c:2850:(snd_config_hook_load) /home/shadowtek/.asoundrc may be old or corrupted: consider to remove or fix it

```
Replace it with exactly what I posted.

---

### Post by ShadowTek on 2009-11-02
I did. See my last post that I edited.

---

### Post by ShadowTek on 2009-11-03
Now that I understand the format of ttable, I tried to swap my channels in every possible way. I found that your speaker remaps are correct by assigning 1 channel to all speakers, starting the game, and testing the output. The weird thing is that I can get each channel to work when I do it like that, but when I try to go back to mapping all channels at once using the script you gave, I get the same deadness in the rear speakers.

This works:

    ```

    ttable.0.0 1
    ttable.0.1 1
    ttable.0.2 1
    ttable.0.3 1
```This works:
```
    ttable.1.0 1
    ttable.1.1 1
    ttable.1.2 1
    ttable.1.3 1

```This works:
```
    ttable.4.0 1
    ttable.4.1 1
    ttable.4.2 1
    ttable.4.3 1 
```And this works:
    ```

    ttable.5.0 1
    ttable.5.1 1
    ttable.5.2 1
    ttable.5.3 1 
```But this is dysfunctional:
```
    ttable.0.0 1
    ttable.1.1 1
    ttable.4.2 1
    ttable.5.3 1 
```WTF is goin on here?

---

### Post by seanj on 2010-02-10
The sound problem should be fixed by turning off surround sound with in-game options.

---

### Post by ShadowTek on 2010-02-10
How will turning off surround sound in the in-game options result in the successful playback of surround sound in the game?

---

### Post by bigseb on 2010-03-24
Very Interesting...

Unfortuneately I don't how yet how to apply this. Say, for example, in reply#8. What do I do with all after 'Code:'? Use the terminal? Not sure.

Incidentally, I have my speakers set to stereo. As I mentioned in the other thread this jerkiness in the sound is only there during the cut scenes. If I stand still during this time it clears up after a few seconds.

---

### Post by ShadowTek on 2010-03-24
Here's a explanation of what acoundrc is.
[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

---

### Post by bigseb on 2010-03-28
Ok... I've gone through this thread over and over and I still don't know how to use all this. Same goes for the link for asoundrc.They speak about stuff that isn't even there. 

Both doom and quake have choppy sound. Help.

And please don't just tell me to google it. When I do that it just brings up more things I don't understand.

---

### Post by ShadowTek on 2010-03-28
I didn't have an asoundrc file in my $HOME dir either. Just create a file with that name, copy into it what was posted earlier, and save it. ALSA will use it if it's there.

Did you also try using OSS sound in Doom3 to see if there is a difference?

---

### Post by bigseb on 2010-03-29
> **ShadowTek said:**
> I didn't have an asoundrc file in my $HOME dir either. Just create a file with that name, copy into it what was posted earlier, and save it. ALSA will use it if it's there.

Did you also try using OSS sound in Doom3 to see if there is a difference?

Just changed it to OSS, will try once I get my headphones back from my daughter.

Re asoundrc file: that link you gave says to create the asoundrc file in home. Then it says:

 "You should replace the name of the card (card0) with something useful, e.g. the one you are using in your /etc/modules.conf file (e.g. cmipci)." 

Well the folder modules isn't there so I didn't know where to go from there. Should I create the asoundrc file anyway?

---

### Post by bigseb on 2010-03-30
No change :(

---

### Post by ShadowTek on 2010-03-30
> **bigseb said:**
> "You should replace the name of the card (card0) with something useful, e.g. the one you are using in your /etc/modules.conf file (e.g. cmipci)."

I *think* that only matters if you have multiple sound cards.

If you only have one sound card (or integrated audio chip), it *will* be "card0".

Anyway, I didn't fool with any of that. I just added exactly what Brebs posted, and that was successfully detected and used by ALSA.

---

### Post by bigseb on 2010-03-31
Thanks shadowtek. I will try once i get a chance.

---

### Post by bigseb on 2010-04-02
> **ShadowTek said:**
> I *think* that only matters if you have multiple sound cards.

If you only have one sound card (or integrated audio chip), it *will* be "card0".

Anyway, I didn't fool with any of that. I just added exactly what Brebs posted, and that was successfully detected and used by ALSA.

I did what you suggested and Doom 3 seems to work perfectly (only played one level). Quake 4 is still stuttering though... :(

---

