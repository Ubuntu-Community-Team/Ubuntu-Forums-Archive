---
title: "...A program won't start!"
date: 2005-11-15
forum: Desktop Environments
---

### Post by Burgresso on 2005-11-15
Hey all!

I got a make-or-brake, system-vital issue I was hoping to get help with (that's sarcasm :) ... )

When I click on planetpenguin-racer from the gnome menu, it does not start, and I can't figure it out. I installed from synaptic. Any advice? Thanks so much!

---

### Post by Remmelas on 2005-11-15
give it a shot from the command line and see if there is any useful error output

---

### Post by 23meg on 2005-11-15
Try typing "planetpenguin-racer" as a command in the terminal and paste any errors you get if any.

---

### Post by linkunderscore on 2005-11-15
try starting it in the terminal and post any errors you get riiiiight here -> []




edit: haha wow JINX!!!

---

### Post by Burgresso on 2005-11-16
Hey, thanks so much!...let's see what happens:

This is what I typed, straight up, after opening the terminal:
> [FONT="Courier New"]planetpenguin-racer[/FONT]
it got me this error:
> [FONT="Courier New"]bash: planetpenguin-racer: command not found[/FONT]

I then explored the short cut, noting the shortcut itself gives this command:
> /usr/games/ppracer

When I ran that comment, this is what I got:
> [FONT="Courier New"]PPRacer 0.3.1 --  [http://racer.planetpenguin.de](http://racer.planetpenguin.de)
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Success)
Segmentation fault[/FONT]


So what do you think?
:cool:

---

### Post by ACK!! on 2005-11-16
[QUOTE=Burgresso]Hey, thanks so much!...let's see what happens:

This is what I typed, straight up, after opening the terminal:

it got me this error:


I then explored the short cut, noting the shortcut itself gives this command:


When I ran that comment, this is what I got:


So what do you think?
:cool:[/QUOTE]

It looks from the error that GLX extension of X is missing.  This usually indicates you do not have hardware 3-D enabled.  

glxinfo from console should give you a hint run that in the terminal and then scroll up through the crap and see if it says you have hardware-enabled 3-D going on.

---

### Post by Burgresso on 2005-11-16
Hey Ack!!:

Thanks, I appreciate your input. I tried that, and this is what I got. I don't know what to make of it. :cool: 

> [FONT="Courier New"]name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault
[/FONT]

Interestingly, I've ran this program before. But Yesterday I tried to install a video card, and but I gave up. Ever since then, I can't use planetpenguin-racer. 

... Muchas gracias!

:)  :-({|=  :)

---

### Post by Burgresso on 2005-11-16
Okay, I fixed it!

I am not sure why exactly this worked, but if anyone can provide some clearer insight, I'm sure other users would appreciate it too.

As I mentioned, I tried to install a video card, and nvidia video card. In the process I downloaded the nvidia driver. I erased this, and reinstalled some packages in synaptic that seemed related to GLK. I restarted, and viola! Thanks everyone who showed interest to help.

Now I can play my favorite game again, as soon as i figure out how to get around planetpenguin's control bug...

---

### Post by ACK!! on 2005-11-16
[QUOTE=Burgresso]Okay, I fixed it!

I am not sure why exactly this worked, but if anyone can provide some clearer insight, I'm sure other users would appreciate it too.

As I mentioned, I tried to install a video card, and nvidia video card. In the process I downloaded the nvidia driver. I erased this, and reinstalled some packages in synaptic that seemed related to GLK. I restarted, and viola! Thanks everyone who showed interest to help.

Now I can play my favorite game again, as soon as i figure out how to get around planetpenguin's control bug...[/QUOTE]

Coooool.  Not that we provided the answer but at least we kept you guessing about the problem.  :D

---

### Post by E-werd on 2005-11-18
Hey, a couple days late but...

I have been having the same problem.  My video drivers are working fine.  Here is the glxinfo output:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
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
OpenGL renderer string: FIRE GL 9000 PRO DDR Athlon (3DNow!) (FireGL) (GNU_ICD)
OpenGL version string: 1.3.1014 (X4.3.0-8.18.8)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_ATI_element_array,
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap,
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
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None

```

Everything is in check there.  Now, running ppracer:

```
PPRacer 0.3.1 --  http://racer.planetpenguin.de
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.

*** ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Success)

```

Any ideas?

---

### Post by Suthern on 2007-03-06
And another echo from me: Same error! No "GLX is missing" errors, just ```
ppracer error: Couldn't initialize video: Couldn't find matching GLX visual (Success)
```

GLXINFO ```
$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 1.2 (2.0.6011 (8.28.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon
``` Note that my screen is NOT on the : 0 at all. I'm running BERYL and everything is fullyaccelerated. Other 3d programs run great. Some things are just confusing I guess.

---

