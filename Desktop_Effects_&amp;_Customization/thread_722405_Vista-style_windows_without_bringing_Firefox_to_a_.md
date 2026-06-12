---
title: "Vista-style windows **without** bringing Firefox to a crawl"
date: 2008-03-12
forum: Desktop Effects &amp; Customization
---

### Post by sindyr on 2008-03-12
OK, I am running Emerald to get some Vista-looking effects going on - running the theme "vista_q" which makes the windows look exactly how I want.

But my Firefox is slow as crap now.  Not sure when it started, but even the action of switching from one tab to another takes 3-4 seconds each.  After doing some research, is seems that with Emerald turned off, Firefox goes back to its usual moderately perky self.

But I want BOTH!!  I recently made the switch to Ubuntu, in large part motivated by the idea that this OS would be highly customizable while serving my basic email and browsing needs.

At this point, I require a stylish interface.  Yes, I know that this is functionally irrelevant to using a computer, but I am in the camp that not only want functionality but style as well.  And to tell the truth, I find the style of Vista to be most pleasing.  Using emerald, I was able to get the style of Vista and the functionality of Ubuntu.  Now something has changed - I don't know what or when - but lots of people running Emerald are now experiencing unendurable lag in Firefox even when they are only switching tabs!  Lag that goes away when Emerald is deactivated.

Let's assume the goal is to be able to browse the web with a tabbed browser while still having a Vista-like transparent window border on all applications' windows.  (we can assume that because it is in fact my goal)

These are the only solutions I can imagine:

1) Hope that someone finds a fix to the whole firefox not performing well while emerald is running.  In the meanwhile, wait.

I am NOT a good waiter.  And no one has found a fix yet.  My educated guess is, that this problem will not be fixed at least until Gran Paradiso goes live.  Well, as I mentioned, I am not a good waiter, and I need java to work in my browser, something I was having problems with when I tried the beta of Gran Paradiso.  So using the beta seems to be out, and waiting, again, is out.

2) Use different drivers??  I am using the nvidia-glx-new.  These are the only drivers I have found that permit the advanced desktop effects to even be enabled, so I am not sure what other drivers I could or should try.  For the record, I am running a Dell M1330 XPS with 2GB Ram, 2.5GHz CPU, 8400M NVidia Graphics.

3) Use a different windows decorator apart from Emerald that gives me the nice Vista transparent window edges without slowing down Firefox.  I tried the gtk-decorator and could not see how to use it in place of emerald and still get Vista-like windows.  Is this possible, or is gtk-decorator too basic?

4) Use a different tabbed browser?  Are there any other tabbed broswers compatible with flash and java, installable into Ubuntu?

5) Pitch Ubuntu into the trash and go back to using Vista, which is still installed on my system on a different partition.

I am depending on all of you to prevent me from having to consider option #5!  Linus strength has always been its weakness as well - that there is no central place, no tech support number to call to get issues like this resolved.  However, many linux advocates tout the free and decentralized support of the linux community as superior to any commercial support options.

Well, lets put that to the test right here and now.  I have I think an eminently reasonable goal - that of non-lagged tabbed browsing with stylish translucent/transparent window borders on all windows.  Vista at least accomplishes that much.

Can Ubuntu?  Not eventually, but today?

How?

Here are some reference threads:
[http://forum.compiz-fusion.org/showthread.php?p=51062](http://forum.compiz-fusion.org/showthread.php?p=51062)
[http://www.nvnews.net/vbulletin/showthread.php?t=96778](http://www.nvnews.net/vbulletin/showthread.php?t=96778)
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/190228](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/190228)

-Sindyr

---

### Post by sindyr on 2008-03-12
No responses or help.  Very educational.

Some one once said to me "Free software is only free if your time has no value."  I don't want to think that they are right, but no one here has yet proved them wrong...

---

### Post by PinkFloyd102489 on 2008-03-12
5 hours wait is nothing. It's free help, so dont complain. I still have active threads that I started from months ago that havent been answered. Eventually found the answer myself.



The only type of window manager that can do transparent compositing currently is Emerald. If you want transparent, use Emerald. Hopefully the new compositing Metacity that was just released will support some type of transparency soon.

---

### Post by andradx on 2008-03-12
I'm using gnome-xgl which can enable some cool efects, like the ones you have on Vista  windows poping in and out fashionably while not consuming that much resources and firefox not being lagged.
From what I've read you are using Emerald to customize your desktop environment and whatsoever. Never worked with it but I assume there is an alternative to making windows transparent.

You can perform a couple of changes in the colours of your panel (that's the only thing I know how to do this way) [read this]("http://ubuntuforums.org/showthread.php?t=476496")
But I guess that's not the thing you want, as for the part of the transparent windows I can't help you in that issue.

This one comes out of the blue, have you tried using a browser like swiftweasel and seen if it still lags?

I'm getting the impression that on the beggining of my reply I would be helpful, now I'm not that sure but anyway, if you choose #5 lights are out.

---

### Post by PinkFloyd102489 on 2008-03-12
I use the Subvista theme, which is a transparent light blue color, from GnomeLook.org on my P3 450Mhz 448 MB RAM. It runs fairly well, considering the age of the technology.

---

### Post by konungursvia on 2008-03-12
I'm using the same emerald theme as you, and Firefox, with no problem. You may have an older graphics card. However, I'd do this: search for posts on optimizing and speeding up firefox. It is highly configurable, and you can definitely change its memory usage and other attributes to get speed out of it, independently of your emerald theme.

---

### Post by sindyr on 2008-03-12
> **PinkFloyd102489 said:**
> 5 hours wait is nothing. It's free help, so dont complain. I still have active threads that I started from months ago that havent been answered. Eventually found the answer myself.
Yeah, you're kind of making my point for me (grin) - at least I am keeping my sense of the sublime and ridiculous - my sense of humor, that is...
> The only type of window manager that can do transparent compositing currently is Emerald. If you want transparent, use Emerald. Hopefully the new compositing Metacity that was just released will support some type of transparency soon.
Yup.  I was sort of guessing that it would be Emerald or nothing.  So its (possibly) all about the wait - for a better firefox or a better Emerald...

I figure I will probably give it at least until Firefox 3 comes out.

---

### Post by sindyr on 2008-03-12
> **andradx said:**
> I'm using gnome-xgl which can enable some cool efects, like the ones you have on Vista  windows poping in and out fashionably while not consuming that much resources and firefox not being lagged.
From what I've read you are using Emerald to customize your desktop environment and whatsoever. Never worked with it but I assume there is an alternative to making windows transparent.

You can perform a couple of changes in the colours of your panel (that's the only thing I know how to do this way) [read this]("http://ubuntuforums.org/showthread.php?t=476496")
But I guess that's not the thing you want, as for the part of the transparent windows I can't help you in that issue.
Yeah, I guess from the other poster, Emerald may be the only way to get the effects, and truthfully, I am not looking to have to surrender that effect.
> This one comes out of the blue, have you tried using a browser like swiftweasel and seen if it still lags?

I'm getting the impression that on the beggining of my reply I would be helpful, now I'm not that sure but anyway, if you choose #5 lights are out.
You are trying to be helpful, and that's worth something.

Can I install swiftweasel without at all disturbing or affecting my install of Firefox?  Are they two completely seperate programs?

---

### Post by sindyr on 2008-03-12
> **konungursvia said:**
> I'm using the same emerald theme as you, and Firefox, with no problem. You may have an older graphics card. However, I'd do this: search for posts on optimizing and speeding up firefox. It is highly configurable, and you can definitely change its memory usage and other attributes to get speed out of it, independently of your emerald theme.

As I said, my specs are:
```

2) Use different drivers?? I am using the nvidia-glx-new. These are the only drivers I have found that permit the advanced desktop effects to even be enabled, so I am not sure what other drivers I could or should try. For the record, I am running a Dell M1330 XPS with 2GB Ram, 2.5GHz CPU, 8400M NVidia Graphics.
```
..that is, a brand spanking new 8400M.

I would be up for optimizing firefox - what tweaks would you suggest to speed up the time it takes to switch which is the foreground tab?  For example, I have 7-10 tabs up, and I click on another tab (one that is already loaded in) and it takes 2-3 seconds for the switch to take place.

For what it's worth, my buddy who is also running emerald and firefox is not having this issue - although he is using a GeForce 7 series graphics card.  I have heard that the issue is affecting people with GeForce 8 series cards who use both Emerald and Firefox.

---

### Post by sindyr on 2008-03-12
> **PinkFloyd102489 said:**
> I use the Subvista theme, which is a transparent light blue color, from GnomeLook.org on my P3 450Mhz 448 MB RAM. It runs fairly well, considering the age of the technology.
Is subvista an emerald theme?  Because if it is, I can attest that my problem happens no matter what theme in emerald I use.

On the other hand, is subvista is a non emerald theme for some other manager, let me know - especially if it accomplishes window-border transparency.

---

### Post by smah77 on 2008-03-13
Raowrr!  Try epiphany instead of firefox.

---

### Post by ThaRabbit on 2008-03-13
> **sindyr said:**
> As I said, my specs are:
```

2) Use different drivers?? I am using the nvidia-glx-new. These are the only drivers I have found that permit the advanced desktop effects to even be enabled, so I am not sure what other drivers I could or should try. For the record, I am running a Dell M1330 XPS with 2GB Ram, 2.5GHz CPU, 8400M NVidia Graphics.
```
..that is, a brand spanking new 8400M.

I would be up for optimizing firefox - what tweaks would you suggest to speed up the time it takes to switch which is the foreground tab?  For example, I have 7-10 tabs up, and I click on another tab (one that is already loaded in) and it takes 2-3 seconds for the switch to take place.

For what it's worth, my buddy who is also running emerald and firefox is not having this issue - although he is using a GeForce 7 series graphics card.  I have heard that the issue is affecting people with GeForce 8 series cards who use both Emerald and Firefox.

Try to manually install the latest drivers from nVdia. They will enable you to use compiz and they have better support for the spanky new cards ;)

---

### Post by andradx on 2008-03-13
Don't know if installing iceweasel will affect firefox, my guess is no.

Sorry I meant Iceweasel not swift.
You can also try using galeon for the same purpose as you're using firefox

---

### Post by PinkFloyd102489 on 2008-03-13
Subvista from GnomeLook is an Emerald theme.


I actually just switched mine from Subvista to DivinorumCyanMagenta. No change in speed and looks awesome.

---

### Post by sindyr on 2008-03-20
Just wanted to report back - I have tried Iceweasel, Epiphany, Galeon, and a few others, and can report that in those browsers also I am experiencing the same horrible browser performance.

However, all those browsers (including firefox) are based on the gecko core code, right?

Waitasec, I just downloaded Opera, and it seems much faster to switch between loaded tabs...  but I prefer Firefox with its plugins...

What now?

---

### Post by IsawSp4rks on 2008-03-20
How about checking if your machine is correctly configured in the first place?

Most people offer their xorg.config for appraisal.  That's generally a good place to start.

How many displays are you using?

---

### Post by sindyr on 2008-03-20
one display, a laptop.

in terms of my xorg, I will include that, but know that I used envy to set up my video drivers, and it worked fine.  before that I was using the restricted nvidia drivers.  In both cases I was having the same issues with firefox switching tabs slowly while emerald was enabled.  (and others are also expereincing the same issues)  And once again - no problem in Opera.

Here is my xorg.conf:

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8400M GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8400M GS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1280"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by IsawSp4rks on 2008-03-20
I know it's a laptop.  You already stated what you're using.  You didn't quote your display count and there have been issues with dual display and nvidia-glx-new performance in X, with and without compiz-fusion desktop effects enabled.

Your .config looks reasonably ok, if not a little messy and probably reflective of multiple driver installs using Envy mixed with inexperienced user modification.

This doesn't make sense:-

[B]SubSection "Display"
Modes "1280x1280"
EndSubSection[/B]

no such thing as an LCD that has that res on your laptop. **1280x800** is what it should be.  That could be confusing compiz (which IS actually enabled as Emerald won't load without it)

**Option "AddARGBVisuals" "True" ** - this also might help

Last of all, I would recommend asking your friend who has Firefox working well with that Emerald theme to offer his xorg.config so you can compare his to yours, specifically the Option entries in the "Device" section.  

Also, please post the output of glxinfo 

[SIZE="1"]PS : Your attitude isn't the nicest I've seen here either, please act with a little more self respect and try not to be so demanding.  [/SIZE]

---

### Post by sindyr on 2008-03-20
> **IsawSp4rks said:**
> I know it's a laptop.  You already stated what you're using.  You didn't quote your display count and there have been issues with dual display and nvidia-glx-new performance in X, with and without compiz-fusion desktop effects enabled.

Ah, OK - just the one LCD display.

> Your .config looks reasonably ok, if not a little messy and probably reflective of multiple driver installs using Envy mixed with inexperienced user modification.

This doesn't make sense:-

[B]SubSection "Display"
Modes "1280x1280"
EndSubSection[/B]

no such thing as an LCD that has that res on your laptop. **1280x800** is what it should be.  That could be confusing compiz (which IS actually enabled as Emerald won't load without it)

I went in and manually edited that line to 1280x800 and CTRL-ALT-Backspaced.  Thanks for the catch.

> **Option "AddARGBVisuals" "True" ** - this also might help

Pardon my confusion -  are you saying the fact that I already have that line in there is helpful, or that I should changed that line somehow?  It looks like I have it in there exactly as you typed it - perhaps it should be moved into the Display SubSection?  Confused what it is you are saying here.

> Last of all, I would recommend asking your friend who has Firefox working well with that Emerald theme to offer his xorg.config so you can compare his to yours, specifically the Option entries in the "Device" section.  

An excellent idea I should have thought of.  Will do.

> Also, please post the output of glxinfo 

Here it is:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8400M GS/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_bindable_uniform, GL_EXT_depth_bounds_test, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXTX_framebuffer_mixed_formats, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color, 
    GL_NV_depth_buffer_float, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc, 
    GL_NV_texture_env_combine4, GL_NV_texture_expand_normal, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_NV_vertex_program2, GL_NV_vertex_program2_option, 
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x31 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x32 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x33 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x35 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x37 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x38 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x39 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3b 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3d 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x42 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x49 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x4c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x4e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x4f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x54 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x56 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x57 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x60 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x61 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x63 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x64 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x65 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x66 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x67 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x68 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x69 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x6a 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x6b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x6c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x6d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x6e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x6f 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x70 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x71 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x72 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon

> [SIZE="1"]PS : Your attitude isn't the nicest I've seen here either, please act with a little more self respect and try not to be so demanding.  [/SIZE]

Sorry, my initial post at the top of the thread I submitted a couple of weeks ago or more, and that was not my only help thread I felt was getting ignored.  Still, I was being snarky and snitty and I apologize, and have calmed down since.

Thanks for the help.

---

### Post by knowledge_is_power on 2008-03-20
you could try disabling smooth scroll.
also, try some other browsers?
iceweasel, opera??

---

### Post by sindyr on 2008-03-20
> **knowledge_is_power said:**
> you could try disabling smooth scroll.
also, try some other browsers?
iceweasel, opera??

Lol, *this* is the reason I was getting snarky before - as I has already stated not four posts up:
> Just wanted to report back - I have tried Iceweasel, Epiphany, Galeon, and a few others, and can report that in those browsers also I am experiencing the same horrible browser performance.

However, all those browsers (including firefox) are based on the gecko core code, right?

Waitasec, I just downloaded Opera, and it seems much faster to switch between loaded tabs... but I prefer Firefox with its plugins...

What now?

So YES, I have.  Would still like a fix for Firefox. ;)

I *will* try disabling smooth scroll and see if that has any effect, will report back.

EDIT: General.SmoothScroll is already set to FALSE.

---

### Post by IsawSp4rks on 2008-03-20
> **sindyr said:**
> Pardon my confusion -  are you saying the fact that I already have that line in there is helpful, or that I should changed that line somehow?  It looks like I have it in there exactly as you typed it - perhaps it should be moved into the Display SubSection?  Confused what it is you are saying here.
.

Actually the other ARGB entry,** Option "AddARGBGLXVisuals" "True"** should be moved to the Device section, I don't think it's doing much where it is.  Your .config is a little hard to read so excuse the confusion.

---

### Post by sindyr on 2008-03-21
I moved it - still no further effect.

---

### Post by sindyr on 2008-03-21
Did the glxinfo that you guys asked for help?

---

### Post by sindyr on 2008-03-22
For what it's worth, I am still interested in getting to the bottom of this - and I hope that the glxinfo that was asked for and that I posted will lead to the answer to this problem.

However, Opera does not have this problem, and after using it for several days now, I am beginning to think it is a superior browser anyways.  So in the meanwhile, while I wait days or weeks for the next bout of replies to this post, I am using Opera, but I still hope to be helped to get to the bottom of the root issue.

Thanks.

---

### Post by sindyr on 2008-03-25
So I guess I am gonna assume that this thread is dead and whatever reason I was asked to do the glxinfo, may not go forward.

Can someone email me @ [email]benn@4efix.com[/email] if theres any further to be done, as I am not going to keep monitoring this thread after no action for a week.

Thanks.

---

