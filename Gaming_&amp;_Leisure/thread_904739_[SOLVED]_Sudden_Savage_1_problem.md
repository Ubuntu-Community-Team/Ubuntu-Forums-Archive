---
title: "[SOLVED] Sudden Savage 1 problem"
date: 2008-08-29
forum: Gaming &amp; Leisure
---

### Post by Naiki Muliaina on 2008-08-29
Ive been playing Savage one for a while now. Havent made any big changes to my main box in a wee while. Last night, Savage 1 just started closing when i opened it. Id get the initializing screen, then as the main screen appears it just closes.

Anyone else been having this problem?

---

### Post by Crafty Kisses on 2008-08-29
Have you checked your error logs?

---

### Post by Naiki Muliaina on 2008-08-29
An error!

```
[ 4821.300891] silverback.bin[6567]: segfault at 48204454 eip b7880949 esp 9edfcfe8 error 4
```

Whats it mean? hehe

---

### Post by Crafty Kisses on 2008-08-29
Post the results of this command > glxinfo

---

### Post by Naiki Muliaina on 2008-08-29
It said lotsa stuff!

```
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7412 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x85 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  8 1 Ncon

```

Lotsa lotsa stuff hehe

---

### Post by Crafty Kisses on 2008-08-29
My advice is running the game in the Terminal so when it crashes you get a error message, then post it here. :)

---

### Post by Naiki Muliaina on 2008-08-29
Tried that, when Savage closes, so does terminal. Annoying eh? hehe ^^

---

### Post by eragon100 on 2008-08-30
I have **exactly** the same problem. Whenever I start savage, the login screen appears, and then *bang it chrashes, the desktop appears, and the computer is frozen, I need to press ctr-alt-backspace. When I run it in terminal, it says: segmentation fault :(

However, I know the problem, and the solution, I just can't apply it :(

The problem is described on the download section of newerth here: [http://www.newerth.com/?id=downloads&op=displayDownload&category=1&file=SFE-Standalone.tar.gz]("http://www.newerth.com/?id=downloads&op=displayDownload&category=1&file=SFE-Standalone.tar.gz")

qoute:

"Seems the version of libpng in the 'libs' directory doesn't match up with the version expected by silverback. If you don't have libpng 1.2.8 installed on your system, silverback will fail to load. I downloaded & built a local copy of it, and copied the lib files/symlinks into 'libs' and all is well.

This was on a Fedora Core 8 system, with libpng 1.2.22. The version included in 'libs' is 1.2.15. Silverback stricly expects 1.2.8.

Just noting this in case anyone else has problems. Cheers!"

I just checked in synaptic, and the version installed on my system is 
1.2.15-beta5.3. Problem found!

I have the source code for 1.2.8 in the attached archive (only 375 kb or something like that) but I can't compile it because it doesn't come with a configure script. It says you have to move the appropiate makefiles from the "scripts" folder to the main folder, and then type make.

Could someone please do that for linux i386 and post the resulting library and simlink as attachments so I can put them in the savage "libs" folder to solve the problem as described in the quote from newerth above?

---

### Post by Naiki Muliaina on 2008-08-30
Found a semi solution. I disable my network as Savage loads, once it comes up with the main screen i reconect my network and it works.

Ill try what you said next time i go to play :)

---

### Post by eragon100 on 2008-08-30
> **Naiki Muliaina said:**
> Found a semi solution. I disable my network as Savage loads, once it comes up with the main screen i reconect my network and it works.

Ill try what you said next time i go to play :)

It doesn't work for me, it goes starts up correctly but it chrashes as soon as I try to join a game. Could someone please compile the code from the attachment at my post above (for linux 32-bit), and upload the compiled library and symlink as attachments so I can fix the poblem? Thanx.

---

### Post by eragon100 on 2008-08-30
problem solved (completely).

I found the library source code with configure script. (attachment)

Download archive to your desktop and extract it, then use the following commands in a terminal:

sudo apt-get build-essential

cd /Desktop/libpng-1.2.8-config

./configure --prefix=SAVAGE_1_DIRECTORY/LIBS (in my case, the command is:

./configure --prefix=/home/eragon/Desktop/games/SFE-Standalone/libs

after that:

make

make install


Now it should run perfectly, have fun playing ! :wink:

---

### Post by Naiki Muliaina on 2008-08-30
Thanks for the replys guys, my problem just fixed itself.... *shrugs* dunno what that was about hehe. Either way, its working fine again, with no 'Nais destructive terminal bashing' intervension needed.

Thanks again for replying though!

---

