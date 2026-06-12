---
title: "total annihilation springs"
date: 2006-11-11
forum: Gaming &amp; Leisure
---

### Post by Fittersman on 2006-11-11
how do i install total annihilation springs?

i went to their website but it gives me a .exe file.

where do i get the linux version?

---

### Post by Perfect Storm on 2006-11-12
[http://taspring.clan-sy.com/phpbb/viewtopic.php?t=3409](http://taspring.clan-sy.com/phpbb/viewtopic.php?t=3409)

---

### Post by MaximB on 2006-11-12
and there is a script installation also : 
[http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#How_to_recompile_Spring_for_a_di](http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#How_to_recompile_Spring_for_a_di)

AI - you should add it to....this one works great.

---

### Post by Perfect Storm on 2006-11-12
Which version does it contains?

---

### Post by Perfect Storm on 2006-11-12
Oh, well I'm checking it out, though I did manage to compile the latest. I might add the easy way to the howto as compiling it requires alot if you are a newbie.

---

### Post by Perfect Storm on 2006-11-12
Okay, howto added:
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=176&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=176&Itemid=63)

---

### Post by MaximB on 2006-11-12
good guide - and I think it would be a good idea to explain more about the "spring-setup" command, you can add more mods,maps,AI there and change the options...very useful.

---

### Post by Perfect Storm on 2006-11-12
will do.

---

### Post by Fittersman on 2006-11-12
what if im running on edgy?

i noticed that this part had dapper in it

## TaSpring Game
deb [ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/](ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/) /

---

### Post by Perfect Storm on 2006-11-12
Works well on edgy as well, I have tested it ;)

---

### Post by MaximB on 2006-11-12
but I don't get one thing...if we have TA-Spring that runs without any outside software (like the original TA discs)...why we need the other TA remakes who asks for files from the original TA ?

---

### Post by Fittersman on 2006-11-12
my total annihilation springs game runs extreamly slowly how do i fix that?

---

### Post by Perfect Storm on 2006-11-12
[quote=from taspring requirements]You will most certainly need a 3D graphics card to run TA Spring, which will probably require at least a GeForce 3 (note that a GeForce 4 MX is not better than a GeForce 3) and the latest driver supported. Minimum CPU requirements are a little more complex. A more powerful CPU will have the capability to support larger maps and a greater maximum unit limit. A 1 GHz CPU should be able to support an estimated 500 units. The needed memory will also vary with unit count and mapsize, but 512 MB should be enough.[/quote]

Perhaps a better graphic card.

---

### Post by Fittersman on 2006-11-12
isnt the radeon 7500 good enough?

if not how do i uninstall ta springs?

---

### Post by Perfect Storm on 2006-11-12
I'm not sure what's that in GF power, but it could be their driver that makes the knot. Is  the 3D acc. driver for you card properly set up?

---

### Post by Fittersman on 2006-11-13
well if this answers your question here is what i get when i type in glxinfo in the terminal:

```
cleippi@cleippi-desktop:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```


if that doesnt answer your questions tell me what i should do to get the answers

---

### Post by HAARP on 2006-11-13
fbo's repository is outdated and not being maintained at the moment. If you want an easy way to get Spring, use it, but you won't get the latest version or a lobby.

---

### Post by cong06 on 2007-05-27
I'm a bit new to command prompt in Ubuntu, but I sorta figured the [installation guide]("http://fbo.no-ip.org/cgi-bin/twiki/view/Linux/DebSpring#How_to_recompile_Spring_for_a_di") would be straight forward. Unfortunately, I got almost the whole way through, and couldn't figure it out.

I followed it exactly. (except instead of xxx, I used 0.74b3, since that's the code for the latest version)

I kept getting stuck at: 

> ... install the package ...

root@host > dpkg -i /opt/spring/spring-release_xxx_386.deb 

In which I would get:
> cong06@Lappy:/opt/spring/spring-release-0.74b3$ sudo dpkg -i /opt/spring/spring-release_0.74b3_386.deb
Password:
dpkg: error processing /opt/spring/spring-release_0.74b3_386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /opt/spring/spring-release_0.74b3_386.deb


I noticed at this directory, that I had a "spring-release_0.74b3-1+999sid_i386.deb" instead, so I tried that:
> cong06@Lappy:/$ sudo dpkg -i /opt/spring/spring-release_0.74b3-1+999sid_i386.deb
(Reading database ... 114735 files and directories currently installed.)
Preparing to replace spring-release 0.74b3-1+999sid (using .../spring-release_0.74b3-1+999sid_i386.deb) ...
Unpacking replacement spring-release ...
dpkg: dependency problems prevent configuration of spring-release:
 spring-release depends on spring-scripts (>= 3.0-1); however:
  Package spring-scripts is not installed.
 spring-release depends on spring-data-nonfree; however:
  Package spring-data-nonfree is not installed.
dpkg: error processing spring-release (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 spring-release


Does anyone know where I should go from here?

---

### Post by cong06 on 2007-05-28
the thread: [http://ubuntuforums.org/showthread.php?t=203448](http://ubuntuforums.org/showthread.php?t=203448)
Has much better instructions for installing TASpring. (or at least it worked when I tried it that way)

---

