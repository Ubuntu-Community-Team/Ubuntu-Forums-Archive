---
title: "no drivers under my hardware profile"
date: 2009-03-12
forum: General Help
---

### Post by bilmas on 2009-03-12
when i go to system>administration>hardware drivers it searches for available drivers and then shows that there are no drivers in the list.  "No proprietary drivers are in use on this system'

my sound works and obviously i have a display but i feel like that because there is no driver there for a video card is why i can't really watch flash videos very well anymore...

to be sure how can i make sure ubuntu recognizes all of my devices?

i am using version 8.10

thanks!
david

---

### Post by taurus on 2009-03-12
You have to install flash plugin (and others) before you can use it.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

Which video card do you have anyway?

```
lspci | grep VGA
```

---

### Post by bilmas on 2009-03-12
oops i went to the synaptic package manager and selected some ati radeon drivers that weren't selected (my video card) and now the computer won't boot properly.  the monitor goes blank and it says 'device not supported'

can i fix this using the ubuntu disc?

---

### Post by Yellow Pasque on 2009-03-12
You should be able to fix it by booting to recovery mode (press Esc after your computer POST's to access the GRUB menu). Choose the option "xfix" (or something like that).

---

### Post by bilmas on 2009-03-12
i chose xfix but i am still having the same problem

yikes

---

### Post by taurus on 2009-03-12
Boot into recovery mode and get to root shell.  Then at the prompt, reconfigure your X server again.

```
dpkg-reconfigure xserver-xorg
exit
```

---

### Post by bilmas on 2009-03-12
edit: went through the reconfiguration and i am still stuck at no support for the monitor

---

### Post by taurus on 2009-03-12
You mean it won't even let you get into a shell (prompt) from the recovery mode?

---

### Post by bilmas on 2009-03-12
i got to the shell prompt and entered the code and followed the prompts to configure everything and when it was all done and went back to the prompt i typed 'exit' but all it did was bring me back to a blank monitor

briefly it showed david-desktop login: but in text, not graphical and then the monitor went blank

---

### Post by UbuntuNerd on 2009-03-12
try to hit "alt+f7" to get back to your desktop to see if it work

---

### Post by bilmas on 2009-03-12
i don't think it is giving me any video card support at all.  my monitor isn't reading anything off the computer.  i can only assume that it is at the login screen right now

---

### Post by bilmas on 2009-03-12
pressing alt+f7 doesn't do anything

eep

am i going to have to start from scratch?

---

### Post by Yellow Pasque on 2009-03-12
Can you be more specific about what you installed? Just installing a video driver module shouldn't change your system (unless you installed the proprietary ATI/fglrx driver, which will overwrite libGL with its custom version).

If you did install fglrx, the terminal fix would be:
```
sudo apt-get purge xorg-driver-fglrx
sudo apt-get --reinstall install libgl1-mesa-glx
```

---

### Post by bilmas on 2009-03-12
that worked!

thank you sooo much!

---

### Post by bilmas on 2009-03-12
i still have no list of drivers but at least i have my computer back and running

---

### Post by philinux on 2009-03-12
```
lspci | grep VGA
```

This will show your vid card.

---

### Post by bilmas on 2009-03-12
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]

```

---

### Post by philinux on 2009-03-12
Ok so whats does

```
glxinfo
```

report.

---

### Post by bilmas on 2009-03-12
```
16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x6c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x6e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x70  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x71  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x72  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x73  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x74  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x75  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x76  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x77  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x78  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x79  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```

---

### Post by philinux on 2009-03-12
Sorry. you have to scroll back to get the important but this will save the bother.

```
glxinfo | grep "direct rendering"
```

Hopefully the answer is yes.

and this.

glxinfo | grep vendor

---

### Post by bilmas on 2009-03-12
```
david@david-desktop:~$ glxinfo | grep "direct rendering"
direct rendering: Yes
david@david-desktop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

```

---

### Post by philinux on 2009-03-12
Ok so you've got direct rendering which is good and means you can have desktop effects i.e.compiz. system>prefs> Appearance > visual effects. Try extra. 

Have you installed compizconfig-settings-manager if not install it from synaptic or terminal. you'llthen be able to get all the cube effects going.

---

### Post by Yellow Pasque on 2009-03-12
The System -> Adminstration -> Hardware Drivers utility only lists proprietary drivers. Ideally, it **should** be empty. Your video card is way too old to use ATI's proprietary drivers.

As philinux suggested, check the output of glxinfo to make sure your direct rendering is kosher. Better yet, post output of:
```
LIBGL_DEBUG=verbose glxinfo
```

---

### Post by bilmas on 2009-03-12
```
name of display: :0.0
display: :0  screen: 0
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6b 32 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x6c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x6e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x70  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x71  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x72  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x73  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x74  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x75  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x76  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x77  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x78  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x79  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

---

### Post by Yellow Pasque on 2009-03-12
If you're running Compiz/desktop effects, then the output above is okay. .

---

### Post by bilmas on 2009-03-16
> **philinux said:**
> Ok so you've got direct rendering which is good and means you can have desktop effects i.e.compiz. system>prefs> Appearance > visual effects. Try extra. 

Have you installed compizconfig-settings-manager if not install it from synaptic or terminal. you'llthen be able to get all the cube effects going.

cube effects wasn't what i had trouble with
when i scroll websites the scrolling is choppy.  using xubuntu i didn't have this problem even running the gnome desktop but i'd prefer to stick with ubuntu

---

### Post by Yellow Pasque on 2009-03-16
What version of xubuntu were you running? Unfortunately, the slowdown on your machine might be due to increasing hardware requirements (i.e. software bloat). Your hardware's not exactly the latest and greatest...

---

### Post by sgissinger on 2009-03-16
Hey guys, I saw you were talking about ati's proprietary drivers. I'm running hardy with my ati 7500 which was fully supported under gusty. It appears this card was blacklisted somehow so I'd like to know if any of you knows where I could get some drivers for this ati mobility radeon 7500.
Thanks

---

### Post by bilmas on 2009-03-16
> **Temüjin said:**
> What version of xubuntu were you running? Unfortunately, the slowdown on your machine might be due to increasing hardware requirements (i.e. software bloat). Your hardware's not exactly the latest and greatest...

8.10 just like ubuntu

the scrolling is the only issue i continue to have...
would buying a faster video card help me any?

what about ram?

---

### Post by bilmas on 2009-03-16
i also had no issues with smooth scrolling under windows xp which must use more resources than ubuntu

---

