---
title: "Does Anyone enable XGL(ATI driver) successfully?"
date: 2006-06-15
forum: Desktop Environments
---

### Post by aubrey on 2006-06-15
I installed ubuntu from 6.06 dapper desktop release. 
I have tried almostly all the methods on the  forum to make XGL work on my laptop.
( DELL LATITUDE D610)
=======================================
aubrey@ubuntu-dapper:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5814 (8.25.18)
=======================================
However, none of the methods work on my side. The big headache is,
When I installed and enabled everything and reboot, the system will halt when log into gnome(before I enter username and password).

I really appreciate any suggestions!

---

### Post by grigpi on 2006-06-15
I have xgl working with fglrx drivers. Try here : [https://wiki.ubuntu.com/CompositeManager/Xgl]("https://wiki.ubuntu.com/CompositeManager/Xgl")
Method A worked for me. All other methods gave me the same result as yours.
Good luck!

---

### Post by stiankarlsen on 2006-06-15
I got XGL working [like this]("http://justpretending.net/wp/2006/06/12/ubuntu-users-enable-xgl-on-dapper-drake/"), just a couple simple steps, 20 second job, tops..

---

### Post by rabidphage on 2006-06-15
[QUOTE=stiankarlsen]I got XGL working [like this]("http://justpretending.net/wp/2006/06/12/ubuntu-users-enable-xgl-on-dapper-drake/"), just a couple simple steps, 20 second job, tops..[/QUOTE]

Awesome.. never knew xgl/compiz was soooooo easy... 
the best part is, i don't see no significant increase in cpu usage. my pentium m 1.73 ghz is almost always running at 800 mhz.. bet vista wont beat that.. 
there are slight glitches.. not anything to complain about though..
no wonder bill gates decided to retire..
BTW i'm on ATI radeon x300

---

### Post by stiankarlsen on 2006-06-16
yeah. pretty easy huh

Like you say, there are still some minor bugs, but this is after all beta software.

No way vista can keep up with this..

---

### Post by bvanaerde on 2006-06-16
[QUOTE=stiankarlsen]Like you say, there are still some minor bugs[/QUOTE]
Do you also have this bug? Both the shutdown & suspend buttons are gone.
Apart from that, it works really great here (ATI Mobility Radeon 9700)

---

### Post by stiankarlsen on 2006-06-16
Yeah, I have that bug, kind of annoying really.

Also, I've "lost" the border around the VLC player, and the thing that really bugs me, is that when you press alt+backspace at the same time, the computers logs out to the login screen, and i have no idea how to fix/remove that. the shortcuts says that "Log out" isnt bound to anything, but every freakin time im sitting writing something, i frequently use the backspace and alt key for capital letters, and then bom, im logged out, not able to recover my work.

---

### Post by Trance Gemini on 2006-06-16
[QUOTE=stiankarlsen]Yeah, I have that bug, kind of annoying really.

Also, I've "lost" the border around the VLC player, and the thing that really bugs me, is that when you press alt+backspace at the same time, the computers logs out to the login screen, and i have no idea how to fix/remove that. the shortcuts says that "Log out" isnt bound to anything, but every freakin time im sitting writing something, i frequently use the backspace and alt key for capital letters, and then bom, im logged out, not able to recover my work.[/QUOTE]

I have seen here on this forum the solution for this bug. 
Try searching something like  "xgl backspace" and look thru the results. Hope that you find a solution!

---

### Post by dominikroblek on 2006-06-16
[QUOTE=aubrey]I installed ubuntu from 6.06 dapper desktop release. 
I have tried almostly all the methods on the  forum to make XGL work on my laptop.
( DELL LATITUDE D610)
=======================================
aubrey@ubuntu-dapper:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5814 (8.25.18)
=======================================
However, none of the methods work on my side. The big headache is,
When I installed and enabled everything and reboot, the system will halt when log into gnome(before I enter username and password).

I really appreciate any suggestions![/QUOTE]

I enabled FGLRX driver successfully. I roughly followed the rules for Dapper described on [BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI").

I executed the following commands:

sudo apt-get update 
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial

After executing the command "sudo aticonfig --initial" I had to manually tidy /etc/X11/xorg.conf file, since the command corrupted the file a little bit.

Then I executed "sudo aticonfig --overlay-type=Xv" command which further modified xorg.conf a little bit.

I attached my final version of xorg.conf for details.

Finally I had to copy the old /usr/lib/libGl.so.1.2 over the current one. Look [here]("http://ubuntuforums.org/showthread.php?t=185033") for details.

After rebooting and exectuing the "fglrxinfo" command I got the following output and everything appeared to work fine:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18 )

--
Dominik

---

### Post by aubrey on 2006-06-16
[QUOTE=grigpi]I have xgl working with fglrx drivers. Try here : [https://wiki.ubuntu.com/CompositeManager/Xgl]("https://wiki.ubuntu.com/CompositeManager/Xgl")
Method A worked for me. All other methods gave me the same result as yours.
Good luck![/QUOTE]
I have to say I didn't enable it successfully yet. I can see the script was implemented.  
However, when I switch the workspace, I can't see the three-dimensional graphics.

I‘ve tried the all methods all of you pointed to me, but none of them works for me.

fgl driver should be OK.
==========================================
aubrey@ubuntu-dapper:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5814 (8.25.18)
===========================================

glxinfo should be ok
===========================================
aubrey@ubuntu-dapper:~$ glxinfo
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
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5814 (8.25.18)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
===============================================

I used the xorg.conf dominikroblek attached.
So, now, what did I miss? Can anyone tell me how to debug it? Or how to confirm things one by one?

I won't give up...........

Many thanks to your suggestions

---

### Post by aubrey on 2006-06-16
From the methods I've tried, I found XGL didn't work for me. 
if I change the file /etc/gdm/gdm.conf-custom:
===========================================
[servers] 
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
===============================================

Then I can not log in. The system hang before enter the username and password.

If I implement the script stiankarlsen pointed, it seems XGL run for a moment and exit somehow. So I can not see the three-dimensional graph effects.

How to debug XGL manually?

Thanks a lot.

---

### Post by stiankarlsen on 2006-06-17
[QUOTE=Trance Gemini]I have seen here on this forum the solution for this bug. 
Try searching something like  "xgl backspace" and look thru the results. Hope that you find a solution![/QUOTE]

Thanks, I found a couple of threads on the issue, and it looks promising, will try it in a few days when i get back home.

---

