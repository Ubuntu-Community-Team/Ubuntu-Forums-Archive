---
title: "Anyone have luck with Minecraft on Intel drivers?"
date: 2012-01-29
forum: Gaming &amp; Leisure
---

### Post by Rotten194 on 2012-01-29
I have an Intel i7 in a laptop, which up until recently played Minecraft very well. On Windows, it can run it at around 20 fps, not perfect but playable. Same with Linux, slightly slower but still not bad, until recently. I updated to the newer drivers with the update utility and now get 3-5 fps, most of the time spent rendering. It really sucks since I was working on some mods and while I have been able to release a few small ones, testing any other ones is nigh-on impossible when I can't even scroll through the items menu.

Anyone have luck with other drivers? Should I try backdating?

Details:

```
jon@ubuntu: glxinfo | grep renderer
OpenGL renderer string: Software Rasterizer

```

Software rasterizer sounds bad, but I can't find any way to get it on the hardware...

```
jon@ubuntu: lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

I've tried Optifine, does nothing (the issue seems to be with drawing everything, not specific fancy effects).

Thanks for any help, it's really appreciated.

---

### Post by regor210 on 2012-01-30
For checking the Intel video heres how to do that.

Will show you what driver is in uses.
$ lspci -vmk | grep -A 8 -B 2 VGA


3d and speed test.
$ sudo apt-get install mesa-utils
$ glxgears

When I run glxgears on my old Dell p4, Intel video I'm getting about
60.000 FPS
useing the i915 driver.

May show how much video ram your Intel video has. As not all BIOS's will tell you.
$ lspci -v | less



 And there's always this.
--------------------------------------------------------
There are 3 things that may improve your performance.

1st check your computers BIOS and see if you can increase your graphics shared memory.

2nd In Minecraft goto Options > Video settings and make

Graphics Fast
Smooth Lighting OFF
Performance Max FPS
Clouds off

Then play with 
Render Distance 
Far = slow, more lag
Tiny = fast, less lag

Then and try
Particles minimal

3rd if you have 2 or more Gigs of system ram you can make more memory available to Minecraft
by launching it with

$ java -Xms1024M -Xmx1024M -jar .minecraft/minecraft.jar

The 1024M in this command makes 1 Gig available to Minecraft. The default is .5 Gig.
---------------------------
Last are you using sun-java?

Sun-java works best with Minecraft.

You can check to see what java you are using with 
$ sudo update-alternatives --config java

OpenJDK comes with Ubuntu by default.

---

### Post by Dlambert on 2012-01-30
Yes, I play minecraft on my GM45 on a dell inspiron 1545, I turned down some of the settings for it to run smoother. GoodLuck! Maybe update the MESA driver?

---

### Post by Rotten194 on 2012-01-30
> **regor210 said:**
> For checking the Intel video heres how to do that.

Will show you what driver is in uses.
$ lspci -vmk | grep -A 8 -B 2 VGA


3d and speed test.
$ sudo apt-get install mesa-utils
$ glxgears

When I run glxgears on my old Dell p4, Intel video I'm getting about
60.000 FPS
useing the i915 driver.

May show how much video ram your Intel video has. As not all BIOS's will tell you.
$ lspci -v | less



 And there's always this.
--------------------------------------------------------
There are 3 things that may improve your performance.

1st check your computers BIOS and see if you can increase your graphics shared memory.

2nd In Minecraft goto Options > Video settings and make

Graphics Fast
Smooth Lighting OFF
Performance Max FPS
Clouds off

Then play with 
Render Distance 
Far = slow, more lag
Tiny = fast, less lag

Then and try
Particles minimal

3rd if you have 2 or more Gigs of system ram you can make more memory available to Minecraft
by launching it with

$ java -Xms1024M -Xmx1024M -jar .minecraft/minecraft.jar

The 1024M in this command makes 1 Gig available to Minecraft. The default is .5 Gig.
---------------------------
Last are you using sun-java?

Sun-java works best with Minecraft.

You can check to see what java you are using with 
$ sudo update-alternatives --config java

OpenJDK comes with Ubuntu by default.

```
jon@ubuntu: lspci -vmk | grep -A 8 -B 2 VGA                                 (0)

Device:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	2nd Generation Core Processor Family Integrated Graphics Controller
SVendor:	Toshiba America Info Systems
SDevice:	Device fc30
Rev:	09
Driver:	i915
Module:	i915

```

```
jon@ubuntu: glxgears -info                                                (255)
GL_RENDERER   = Software Rasterizer
GL_VERSION    = 2.1 Mesa 8.0-devel
GL_VENDOR     = Mesa Project
GL_EXTENSIONS = GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_MESA_resize_buffers GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_S3_s3tc GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_compression_s3tc GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_NV_vertex_program GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_NV_fragment_program GL_NV_point_sprite GL_NV_vertex_program1_1 GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_depth_bounds_test GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_rectangle GL_ATI_texture_compression_3dc GL_EXT_pixel_buffer_object GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_rgtc GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_NV_fragment_program_option GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_ATI_texture_mirror_once GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_array GL_EXT_texture_compression_latc GL_EXT_texture_sRGB_decode GL_MESA_texture_array GL_ARB_copy_buffer GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_EXT_provoking_vertex GL_ARB_robustness GL_ARB_texture_storage 
2781 frames in 5.0 seconds = 556.172 FPS

```

I am using sun-java (6, 7 crashes since it doesn't like the native libs that come with lwjgl). I have tried launching Minecraft with everything from 500mb to 2 gb and the performance is still terribad, though with 2gb it is better. Like I said, video settings don't help very much. 

I'll try increasing the shared graphics memory. Give me a bit to reboot.

---

### Post by regor210 on 2012-01-30
That is some fine hardware you have there. It looks to be running ok. The problem may be Minecraft.
Did you try going into your home folder and renaming .minecraft then starting Minecraft to reinstall it.

For some reason Minecraft on my kids computer started lagging after a Minecraft update. Reinstalling Minecraft using Alloc's bash script got it going. But when you reinstall you lose your mods. 

[http://ubuntuforums.org/showthread.php?t=1726735](http://ubuntuforums.org/showthread.php?t=1726735)

**lwjgl** as in sticky keys? I have been using this work around. 

One more thing about integrated Intel graphics.

Minecraft Linux sometimes suffers from sticky keys, When it happens with Intel graphics the mouse loses its lock and will not lock back in without logging out.

I fix this by changing Ubuntu or Lubuntu keyboard setting 

in Lubuntu 
Repeat delay 400
Repeat interval 30 

works for me.

In Ubuntu press Print Scrn to take a picture of your setting then make the 
Delay a little longer
Speed a little slower

should do the trick.

---

### Post by Rotten194 on 2012-01-30
> **regor210 said:**
> That is some fine hardware you have there. It looks to be running ok. The problem may be Minecraft.
Did you try going into your home folder and renaming .minecraft then starting Minecraft to reinstall it.

For some reason Minecraft on my kids computer started lagging after a Minecraft update. Reinstalling Minecraft using Alloc's bash script got it going. But when you reinstall you lose your mods. 

[http://ubuntuforums.org/showthread.php?t=1726735](http://ubuntuforums.org/showthread.php?t=1726735)

**lwjgl** as in sticky keys? I have been using this work around. 

One more thing about integrated Intel graphics.

Minecraft Linux sometimes suffers from sticky keys, When it happens with Intel graphics the mouse loses its lock and will not lock back in without logging out.

I fix this by changing Ubuntu or Lubuntu keyboard setting 

in Lubuntu 
Repeat delay 400
Repeat interval 30 

works for me.

In Ubuntu press Print Scrn to take a picture of your setting then make the 
Delay a little longer
Speed a little slower

should do the trick.

I can't use that script since I'm running from MCP, not normal Minecraft, but I did do the keys thing. Thanks. Still get 5 fps though :\

---

### Post by regor210 on 2012-01-30
Do you have problems with other games that use 3D drivers?

What do you get when you run your Minecraft Coder Pack in a terminal?

If you see a bunch of these input errors

Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers


Try and run this
$ sudo chmod go=u /dev/input/event*

Then run MCP

---

### Post by Rotten194 on 2012-02-07
> **regor210 said:**
> Do you have problems with other games that use 3D drivers?

What do you get when you run your Minecraft Coder Pack in a terminal?

If you see a bunch of these input errors

Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers


Try and run this
$ sudo chmod go=u /dev/input/event*

Then run MCP

HOLY FECAL MATTER (not sure if family-friendly forum...)!!

Don't know if this was your fix or just a driver update, but I just started Minecraft after doing this and it's a solid 18 fps! Dayum! Thank you thank you thank you!

---

