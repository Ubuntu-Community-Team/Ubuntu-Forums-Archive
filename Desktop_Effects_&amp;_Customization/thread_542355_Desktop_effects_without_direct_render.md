---
title: "Desktop effects without direct render"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by Dakunesu on 2007-09-03
Is it possable to use desktop effects, Beryl, Compiz, or any of that sort of stuff without direct render?

my cars is a 
intel(R) CGC 85815 Graphics controller

it says that it cant do direct render but it also says that the max resolution is 1024x798 but it can go much higher.

---

### Post by DjBones on 2007-09-03
well, since your card is intel im sure there is an easy fix because their drivers are open source.
although, in the meantime you can try out enlightenment (e17).. nice eye-candy, i use it on my computer that has an ATI card because it dislikes beryl/compiz/working

i'm a bit tentative, if you haven't used linux for very long, but you can always reconfigure your xorg.conf with the terminal command (as root)
*dpkg-reconfigure xserver-xorg*
and it will popup with a blue-screen that should run through a list of options and choices for your system.
although thats probably a bit hasty, im sure its much much easier than that considering its intel haha

---

### Post by Dakunesu on 2007-09-03
no i havent used linux for even a week but i have gotten qite got(when it comes to computers i can learn really fast)
That dpkg-reconfigure xserver-xorg actually screws up everything, ive already tryed it but i havet heard of enlightenment(that sentance sounds funny)

ive never really done much with the graphics card though and i really dont want to go and get a nvidia GFX card because of the cost.

---

### Post by DjBones on 2007-09-05
well, there are some pretty good howto's for e17 on the forums.. if the search doesn't bring any up it should be under the tutorials and tips

if for some odd reason you do get an nvidia card, you can use a application Envy to automatically install and configure your graphics drivers / xorg.. its actually pretty helpful for my comps that don't use integrated.
so what happens in the command line when you try to run compiz fusion?
i dont think i have direct rendering but it still works for me

((and a last note, what does it say in the terminal when you type 'glxinfo'?))

---

### Post by petit.padavoine on 2007-09-05
Use the restricted drivers manager to see if it suggests any drivers for your system.
Try installing the xserver-xorg-video-intel package, I think that's the latest intel drivers.
Reboot and see if you have direct rendering. If not, you might have to edit your /etc/X11/xorg.conf file (MAKE A BACKUP FIRST!) and replace the line which says "Driver" "i810" with "Driver" "intel".
Then reboot again, and see if you get direct rendering.

---

### Post by mysticmatrix on 2007-09-05
> **Dakunesu said:**
> Is it possable to use desktop effects, Beryl, Compiz, or any of that sort of stuff without direct render?

my cars is a 
intel(R) CGC 85815 Graphics controller

it says that it cant do direct render but it also says that the max resolution is 1024x798 but it can go much higher.

Beryl and Compiz support starts i845 onward while your IGP is i815. So I am pretty sure that Eye Candy won't run on your PC. Also, you can check out if your card supports 3D rendering. Only then you can hope that you can get direct rendering enabled.
Cheers

---

### Post by Dakunesu on 2007-09-06
well i dont think i have direct render because i cant even do some stuff in windows as well.

im kinda staying away from anything that changes xorg, the last time i tried it, it messed things up instead of helped like other people said

E16 is all i can get but it does good(i heard that E17 had been pre-alpha for 5 years or so) . i use e-gnome so i still have some shortcuts left.

thanks mysticmatrix now i understand what people mean by i845 and i815

i guess ill wait till i can get enough money to buy a graphics card like nvidia, 
thanks for you support guys and thanks for E!!!  now all thats left is wireless issues

the info from the glxinfo command is
name of display: :0.0
display: :0  screen: 0
direct rendering: No
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
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x43 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by Dakunesu on 2007-09-12
i solved the problem with help

i dropped my bit depth to 16 instead of 24 and i am using beryl because compiz-fusion is a pain

---

