---
title: "make games and stuff run faster"
date: 2006-11-12
forum: Gaming &amp; Leisure
---

### Post by Fittersman on 2006-11-12
how can i make my games and stuff run faster?

i dont know if you need this or not but here is my glxinfo

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

---

### Post by slimdog360 on 2006-11-12
get a new graphics card. If your looking to go cheap, you could probably get something in the Nivida 6000 series range for not too much money. 

I wouldnt bother overclocking anything.

---

### Post by reiki on 2006-11-13
You can get a 512MB nVidia 7300GT for about $120 and I can tell you (because I use one) that they work great and the graphics are stunning. Granted, it's not the highest end, but at that price it's tough to justify spending close to $300 on a graphics card that's better.

---

### Post by BLTicklemonster on 2006-11-13
My Nvidia mx400 pci mount 32 meg video card outperformed my ati radeon 9200se 128 meg agp card in linux, so don't worry about migrating up from high end radeon to low end nvidia if you ever have to. (not sure what card you have, just making a ruge gesture towards radeon here, work with me)

---

### Post by qrm on 2006-11-13
buy nvidia, better performance and less hassling, ATI programmers write c*ap not drivers

---

### Post by Mr_HeNtAi on 2006-11-13
I personally think that ATis driver support has been getting better and better. I can run plenty of games under linux with an ATi x1400. Including UT2004, Quake4, and Wolf:ET.

---

### Post by curvedinfinity on 2006-11-13
> **reiki said:**
> You can get a 512MB nVidia 7300GT for about $120 and I can tell you (because I use one) that they work great and the graphics are stunning. Granted, it's not the highest end, but at that price it's tough to justify spending close to $300 on a graphics card that's better.
:\ Can you still return your 7300? $120 is way too much for that card. [It should cost around $70-$80]("http://www.newegg.com/Product/Product.asp?Item=N82E16814130052") -- But while you are at it, the 7600 GS in many benchmarks almost doubles the scores of the 7300 -- [and it costs only around $10 more.]("http://www.newegg.com/Product/Product.asp?Item=N82E16814143054")

Hope this helps!

---

### Post by Mr_HeNtAi on 2006-11-13
> **curvedinfinity said:**
> :\ Can you still return your 7300? $120 is way too much for that card. [It should cost around $70-$80]("http://www.newegg.com/Product/Product.asp?Item=N82E16814130052") -- But while you are at it, the 7600 GS in many benchmarks almost doubles the scores of the 7300 -- [and it costs only around $10 more.]("http://www.newegg.com/Product/Product.asp?Item=N82E16814143054")

Hope this helps!

The card you linked only has 256mbs of ram not 512mb like his card. However, the 7300gt 512mb version is $99.99 after rebate with an initial cost of $119.99 as seen [HERE]("http://www.newegg.com/Product/Product.asp?Item=N82E16814130024")

Not that I think the extra 256mb of ram is worth it for most games. But, if you play games with large textures like Doom3 and Quake4 then you amy want the extra.

---

### Post by reiki on 2006-11-13
> **Mr_HeNtAi said:**
> The card you linked only has 256mbs of ram not 512mb like his card. However, the 7300gt 512mb version is $99.99 after rebate with an initial cost of $119.99 as seen [HERE]("http://www.newegg.com/Product/Product.asp?Item=N82E16814130024")

Not that I think the extra 256mb of ram is worth it for most games. But, if you play games with large textures like Doom3 and Quake4 then you amy want the extra.

Actually that's where I got it and you're right about the rebate. I forgot about that. So after rebate and for under $100 you can get a pretty decent card. Again... not the highest end, but regardless of what teh numbers say, I get performance from it that satisfies what I do. (80fps in WoW in openGL standing at the great forge in Iron Forge flight path). 

And I think that's an important consideration for many. It's not always about getting the absolute best on the market (and usually paying a pretty high price for it). Sometimes it's about getting something that satisfies a particular set of parameters. In my case, cutting the graphics card budget from $300 to $120 enabled me the option of simply saving that money or putting it into something else. I built my whole box for about $750 to replace an aging pentium 3 1GHz machine with a 128meg graphics card.

And while the new box ain't the hottest gaming rig... it doesn't NEED to be since I only play one game! :)  It does everything else I need and I'm ok with that.

This ain't no slam against anybody. Hard to "converse" sometimes in type.

***********
Asus P5LD2, PentiumD 930, 2 GB Ballistix, 512 nVidia 7300GT, Aero Cool Zero DBA 620W PSU (135mm fan), Thermaltake Swing case (black, w/a pair of 120mm fans), Seagate 160 SATA (x2).

---

### Post by curvedinfinity on 2006-11-14
Hehe, my fault about that price reference. -- Here is my system, which cost $600 four months ago:

Pentium D 805 (running at 3.4 GHz w/ a quiet HSF)
1 GB DDR2 667 (overclocked %30)
7600 GT 256 w/ passive cooling
2x80 GB SATA3 Hitachis running in RAID 0
All in a tool-less coolermaster case w/ 1x120mm,2x80mm fans, all silent

In more ways than one, it really burns! (hehe -- my little office is by far the warmest room in the house) -- but at least you don't hear it! :)

The processor still has plenty of room left to overclock too, as I have run it for many hours (and never a problem) at 3.5 GHz with the stock voltages. By raising the voltages, I am sure it would go to 3.7 GHz or higher, but I think doing that is bad mojo.

I play Quake 4 on high settings at 1280x1024 w/ 4x FSAA and it rarely drops below the 60 FPS cap. A real bargain if you ask me.

---

### Post by reiki on 2006-11-14
I know what you mean about warm. My rig was fully enclosed in the pedestal of an oak rolltop desk. I think you could bake bread in there! So I took it out and now it's in the footwell. Still plenty of room, but I keep an eye on temps and fan speeds because I really like it to run quietly. I'm not so fanatic about it that I'll go water cooled. I'm just not ready for that yet. When I built my system several months ago I was going to build a pentium 4 system on a board that could handle a dual core later. A P4 3GHz chip was only FOUR DOLLARS less than the PentiumD 930 (also 3GHz) so that one was kind of a no brainer.

I notice while playing WoW I can sometimes get the CPU temp up to 55C or 56C. Especially if I have a browser open on another desktop or something. This is with the stock intel cooler which I had heard horror stories about but quite frankly I don't think it's doing a bad job. I'm considering getting one of [these](http://www.aerocool.us/p-cooler/the-dominator/the-dominator.html). Holy cow! It's got a 140mm fan!  hehehe. Should be able to keep me a bit cooler and that fan should run pretty quiet. AND probably cool the northbridge and ram just because it's so darned big! :)

---

