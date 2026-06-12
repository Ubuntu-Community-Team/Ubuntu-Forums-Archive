---
title: "Compiz cube rotation only on two faces"
date: 2007-11-30
forum: Desktop Effects &amp; Customization
---

### Post by tufftugg on 2007-11-30
Hi
  Compiz was working great, and I could rotate to all 4 sides. Now it will only rotate to the first and third face when rotated. Its' like when rotating from face one, it bypasses face two on the cube.Here is some info about my laptop if that helps:


tuff@tuff:~$ glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

tuff@tuff:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

 Thank you for helping

---

### Post by Ice_cone on 2007-11-30
Are you rotating using the wheel on your mouse?
try using Ctrl + Alt + ->

---

### Post by tufftugg on 2007-11-30
I am using the center controller on my laptop, located between the right and left keys on the touchpad. I can drag a window from face to face and it works o.k.. When dragging a window, it goes from face 1 then 2 then 3 then 4 and back to face one with no problem.

---

### Post by santiagoward2000 on 2007-11-30
> **tufftugg said:**
> Hi
  Compiz was working great, and I could rotate to all 4 sides. Now it will only rotate to the first and third face when rotated. Its' like when rotating from face one, it bypasses face two on the cube.

 Thank you for helping

HI!
This is quite simple! All you need to do is install **compizconfig-settings-manager**, open it, go to **General Options**, and under the **Desktop Size** tab, set the **Horizontal Virtual Size** to the number you want (4 if you want to get a cube).
If there's any problem just ask!

---

### Post by tufftugg on 2007-11-30
I have it set at 4 and it was working on all four, but now it bypasses 2 & 4 when rotating the cube using the center key on my touchpad. And it was working using the center key on my touchpad.

---

### Post by cynicalliberal on 2007-12-01
I originally replied to say that I had the same problem; however, after tinkering I found that the "Rotate Cube" and "Desktop Wall" plugins had the same key bindings for viewport switching on my computer. I just disabled "Desktop Wall" and it solved my problem. If you have them both enabled you might want to try that out, or change the key bindings for one of them.

---

### Post by firebush on 2007-12-05
> I originally replied to say that I had the same problem; however, after tinkering 
> I found that the "Rotate Cube" and "Desktop Wall" plugins had the same key bindings 
> for viewport switching on my computer. I just disabled "Desktop Wall" and it solved 
> my problem. If you have them both enabled you might want to try that out, or change 
> the key bindings for one of them.

I must have a similar problem to this.  I noticed, as a type of work-around, that if I configure my rotation preference under the Gnome Compiz Preferences (which I access via System>Preferences>GL Desktop), I get the desired rotation when I "flip on pointer".  I'm able to put my pointer to the right, and it goes to the workspace I'd expect.

So, compiz *is* able to rotate correctly, but I think that something else must be interfering when I try to rotate with ctrl+alt+direction.  I don't think I have Desktop Wall installed...

Anyone else have ideas as to what may be interfering with the rotation?

Thanks!

---

