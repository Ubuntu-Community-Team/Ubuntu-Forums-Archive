---
title: "please help, slow screensavers"
date: 2006-09-23
forum: Desktop Environments
---

### Post by solo88 on 2006-09-23
I followed this how to to get the mesa info to go away and to get what appears to be 3d acceleration:

[http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26)

This allowed me to get the right stuff to appear with fglrxinfo and to get glxgears to run smoothly (1700 fps in the small window and about 70 fps in full screen), but my screensavers were still runnnig at what appears to be about 1 fps.

then I added the dynamic link for the dri modules like this:

sudo ln -s /usr/lib/dri/ /usr/lib/xorg/modules/dri

Adding the link didn't appear to do anything.  Is their something else that I need to do?  I have also checked to make sure that LibGL.so.1 points to LibGL.so.1.2, which is where it should according to the stuff I have read at this forum.

i have an ATI card (9200), but it appears to be running normally except for the screensavers.  Am I missing something?

thanks in advance for your help.

---

### Post by orb9220 on 2006-09-23
glxgears -printfps 

in a term if you recieve framerates in the 1000+ rates then 3d is setup right.

---

### Post by solo88 on 2006-09-24
should the 1000+ fps be in full screen mode or in the little window that pops up when you first run it?  I get right at 1700 when it's in the little window.

I had the screensavers working correctly at one point, but then I had to re-install due to problems that I had trying to install xgl/compiz.  And, I don't remember the exact steps that I followed to get them to run smoothly

---

### Post by solo88 on 2006-09-25
any help on this one?  I am still having the problem with the screensavers and now that I am running several applications, I am starting to see some lag when dragging / resizing windows.

---

### Post by crispy_420 on 2006-09-25
how bout posting you xorg.conf?

I have an ATI 9800 Pro 128MB running just fine but it should be set up similar right?

---

### Post by solo88 on 2006-09-26
Here is my xorg.conf:

let me know if you see anything that needs to be changed.

---

### Post by solo88 on 2006-09-26
trying again... had to change the extension.  :-)

---

### Post by markster23 on 2006-09-29
hey... i'm having some problems with OpenGL and mesa... i'm kinda newb so bare with me ;) my screensavers are REALLY slow on screen, although they preview normally... they were working just fine before i installed some mesa package or library i think... i'm not sure, but now they're super slow... umm... i ran glxgears and this is what it gave me...

```

root@molly-desktop:~# glxgears -printfps
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
root@molly-desktop:~# glxgears -printfps -info
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
root@molly-desktop:~# glxgears -info

ERROR!  sizeof(I830DRIRec) does not match passed size from device driver
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (1.5 Mesa 6.4.1)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATIX_texture_env_combine3 GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays
591 frames in 5.7 seconds = 103.678 FPS
1368 frames in 5.3 seconds = 256.342 FPS
1596 frames in 5.2 seconds = 307.028 FPS
1482 frames in 5.0 seconds = 293.982 FPS
1596 frames in 5.2 seconds = 304.031 FPS
1596 frames in 5.2 seconds = 306.253 FPS
1596 frames in 5.2 seconds = 305.992 FPS
1482 frames in 5.0 seconds = 294.611 FPS
1482 frames in 5.1 seconds = 292.761 FPS

```

my video card is intel onboard 82865G graphics... can anybody help ?? i've tried everything i can think of... ](*,)

mark

---

### Post by solo88 on 2006-10-02
been away for a little while and no response on this one... anyone able to help?

My screensavers are still extremely slow, but everything else seems to work properly.  any suggestions?

thanks

---

