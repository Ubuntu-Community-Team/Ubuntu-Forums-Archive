---
title: "Gaming inquiries"
date: 2007-11-25
forum: Gaming &amp; Leisure
---

### Post by branfordlax on 2007-11-25
Hello, I just recently switched from Windows XP to Ubuntu.  I love it so far, but I have been trying to use Wine for the last few days to install/run my favorite games, Guild Wars and Battlefield 2142.  I've done some research and discovered that there is much debate over Wine and Cedega, another Windows emulator.  I've read that Cedega is better overall because it is geared towards GAMES, but I've also read that Wine is better for World of Warcraft (which I don't play), etc., etc.  As mentioned earlier in my post, I just want to run Guild Wars and Battlefield 2142.  Which emulator should I use?

Edit: So far, I've installed Guild Wars with Wine, but whenever I run it the login menu takes FOREVER to load and is mostly unresponsive.
       I have tried installing Battlefield 2142, but the installation itself was very long and I'm pretty sure it stalled or something.  I didn't complete the installation, I cancelled it...

---

### Post by brennydoogles on 2007-11-25
> **branfordlax said:**
> Hello, I just recently switched from Windows XP to Ubuntu.  I love it so far, but I have been trying to use Wine for the last few days to install/run my favorite games, Guild Wars and Battlefield 2142.  I've done some research and discovered that there is much debate over Wine and Cedega, another Windows emulator.  I've read that Cedega is better overall because it is geared towards GAMES, but I've also read that Wine is better for World of Warcraft (which I don't play), etc., etc.  As mentioned earlier in my post, I just want to run Guild Wars and Battlefield 2142.  Which emulator should I use?

Edit: So far, I've installed Guild Wars with Wine, but whenever I run it the login menu takes FOREVER to load and is mostly unresponsive.
       I have tried installing Battlefield 2142, but the installation itself was very long and I'm pretty sure it stalled or something.  I didn't complete the installation, I cancelled it...

ok, a brief look at the wine app DB has given me these results....

Guild wars- [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)

Battlefield 2142- [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6637](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6637)

Hope that helps!!

---

### Post by KhaaL on 2007-11-25
Cedega is indeed more geared towards games and to make running the games hassle free (no copying of dll's to your wine system32 folder and such). However:
1. cedega costs money
2. cedega is based on wine (and dosen't contribute back to the FOSS community).

Besides wine is making awesome strides in getting DX compability working - I even think it has gone past cedega in (though im not sure). Those reasons are enough for me to choose wine over cedega.

There's a upcoming project named wine-doors that will make installation of apps more userfriendly. let's give them support and wish them success in their mission!

And by the way, look in appdb for the games and apps you want running in wine. I can't stress enough that it's the place where you can see how to set up your games, send bug reports and follow progress and even vote for the game and app you wish to have working!

---

### Post by Vadi on 2007-11-25
Also take a look around for native linux games. Just like there are windows games that don't run on linux natively, there are linux games that don't run on windows and such you didn't hear much about them :)

---

### Post by MonkeyBoy on 2007-11-25
Vadi makes a very good point.  There are some really good games to play that are native for linux.  

If you need windows games running I recommend wine.  Recently I tried cedega for a few months and found it not too good.  It has a nice gui and can configure games automatically but beyond that it is pretty annoying.  I tried to run Guild Wars with it and kept getting an error.  When I checked the cedega forums lot of complaints had been made about this error but nobody had solved it.  When installing Guild Wars with wine I had no problems though.  There was a lot of support in this forum and the winedb.

---

### Post by branfordlax on 2007-11-25
Okay, I'm going to try re-installing Wine and Guild Wars.  I'll try installing Battlefield too, and I'll post the results later.

---

### Post by branfordlax on 2007-11-25
(Sorry for the double post)

I have re-installed Wine and tried to run Guild Wars, but it is still INCREDIBLY slow, I have not even been able to log in yet.  I still have no tried to install Battlefield.

Update:  My brother has the same exact machine as I do (HP laptop) and Guild Wars runs fine on his machine.  Note:  When I had XP, Guild Wars and Battlefield ran fine...

---

### Post by Vadi on 2007-11-25
Hm.

Try doing this in the terminal: **glxinfo | grep direct rendering**, what does it say?

---

### Post by Vadi on 2007-11-25
Also, looking at the appdb entry, there's apparently a bug about it being slow:

[http://bugs.winehq.org/show_bug.cgi?id=9263](http://bugs.winehq.org/show_bug.cgi?id=9263)

---

### Post by branfordlax on 2007-11-25
This is what the terminal reads:

"corey@corey-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_gpu_program_parameters, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x57 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon"

Also, I don't really understand the link you posted...?

---

### Post by Vadi on 2007-11-25
Okay, so you do have direct rendering.

The link is a reported bug about guild wars and wine. If you'll read the page title, it says "Guild Wars terribly slow", which is the same issue you have.

If you read the ongoing conversation about the bug, same page, they say different things they tired to do. You might want to chip in and say that you have the same issue also, and report what graphics card are you using.

---

### Post by branfordlax on 2007-11-28
Oh yeah, I see now.  Thank you very much.

---

