---
title: "Wine problems - cannot run games."
date: 2005-12-01
forum: Gaming &amp; Leisure
---

### Post by Barts_706 on 2005-12-01
Hi,

I have recently installed Ubuntu and one of the first things I did was to install Wine.

I started by downloading the current version source (0.92) and compiling it. There were some issues with the compilation, but I managed to solve them thanks to google. In order to compile it I had to do it with gcc-3.4 instead of gcc-4.0. 

Unfortunately it did not work. It always printed out the following error :

> 
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.


Apparently (google again) I am not the only one with this problem and this is something a lot of people experience. So my first question is :
[B]
- Did anyone succeeded in compiling and/or installing newest Wine under Breezy, and if so then how?[/B]

I then uninstalled (make uninstall) Wine and tried to get one through apt-get. It installed pretty old version of Wine (20050725 if I remember well). This version theoretically installs and runs, but I did not manage to force it to run neither Max Payne nor Unreal Tournament nor Deus Ex nor darkplaces mod for Quake. I did manage to play this games with Wine version 20050927 under Mandriva, so I am quite disappointed now. I have NVidia drivers up and running, so the problem is elsewhere. Therefore my second question is :

**- Does anyone has any suggestions as how to make the older version work? Or which other Wine version should I install (and where to get it) in order to play Windows games under my new Ubuntu?**

I will be grateful for any suggestions on either of the two questions.


Remark 1 : It's 32 bit version of Ubuntu, so the Wine problems with 64bits Ubuntu do not concern me.

Remark 2 : Please do not suggest Cedega or Crossover Office. I don't have the means to pay for them and am against piracy, so Wine is my tool

---

### Post by Miguel on 2005-12-01
Hi Bart,

First, I must admit that I haven't used wine. As such, I can't help you with the compilation. I was also surprised to see that you can actually play games via Wine. I really thought that wine didn't translate DirectX calls.

But there is a workaround to your second question. The wine you find in the actual repositories is pretty old (some 2 months older than the Mandriva release). However, the wine developers have wine 0.9 (don't know if 0.92 is also available) packaged in debs ready for Ubuntu, in a small repository. 

So, you should only put a line in your sources.list, apt-get update and apt-get install wine. After that, you could disable that wine repositroy. The instructions should be on the wine site. 

If you are having trouble with the wine repository, don't be shy to ask. I'll be glad to help you as far as I can.

---

### Post by Miguel on 2005-12-01
I have just checked, and Wine 0.92 is available as a deb. Maybe this link will help

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Barts_706 on 2005-12-01
Thank you very much Miguel, I don't know how it happened that I missed the repository on winehq.  *ashamed*

I am in the process of installing it right now and in another 10 minutes or so will post the results, hopefully favorable..

---

### Post by akiro.yamamoto on 2005-12-01
This is the repository:
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
This is the site:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by akiro.yamamoto on 2005-12-01
too late :smile:

---

### Post by Barts_706 on 2005-12-01
Well, thank you both (yup, too late akiro, but I appreciate it nevertheless), and indeed it allowed me to install new Wine. 

Yet it still has some serious issues. 

I tried to run DarkPlaces mod for Quake, and this error comes up :

> barts@DigitalFortress:/media/sda1/Games/Quake1$ wine darkplaces.exe
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  748
  Current serial number in output stream:  759


and then program crashes.

I also tried to run Unreal Tournament, and I can see loader, the loading time is extremely long, and than the application freezes with black screen. Wine output is as follows :

> err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_LINEPATTERN (0000000a) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_MONOENABLE (0000000b) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_ROP2 (0000000c) value : 0000000d !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_PLANEMASK (0000000d) value : ffffffff !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_LASTPIXEL (00000010) value : 00000001 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_ZVISIBLE (0000001e) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_EDGEANTIALIAS (00000028) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_RANGEFOGENABLE (00000030) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_EXTENTS (0000008a) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_VERTEXBLEND (00000097) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_EXTENTS (0000008a) value : 00000000 !


And I have seen both of this games running on Mandriva 2005 LE around september this year with pretty recent wine release at that time, otherwise I would already have given up.

So if you have any suggestions as to what I might be doing wrong, please let me know.

Regards,

Barts

---

### Post by Barts_706 on 2005-12-01
I would also like to attach the result of glxinfo, maybe someone can see some hint in it, personally I think everything is okay. The drivers are 7667, so not the latest, but enough for my GeForce4Mo (7676 were supposed to be pretty buggy for older cards). The results of glxgears @ 24bpp are around 2000FPS which is more or less standart value for my laptop. Should you need any other info, let me know.

> name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.3
GLX extensions:
    GLX_ARB_get_proc_address, GLX_EXT_import_context, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 440 Go/AGP/SSE2
OpenGL version string: 1.4 (1.5.3 NVIDIA 76.67)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shared_texture_palette,
    GL_EXT_stencil_wrap, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square, GL_NV_fog_distance,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection,
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod,
    GL_SUN_multi_draw_arrays, GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess


---

### Post by akiro.yamamoto on 2005-12-01
This may seem a silly question but do you have your card set up for 3d accelration?
Try this:
CODE:
glxgears -info
in a terminal..

---

### Post by akiro.yamamoto on 2005-12-01
Since you seem to have a Nvidia card see the links in my sig to help set it up properly.

---

### Post by akiro.yamamoto on 2005-12-01
Did you configure wine for Direct3D rendering  as Hardware instead of Software?
[ALT]+[TAB]
winecfg
Graphics Tab
Vertex Shader

---

### Post by Barts_706 on 2005-12-01
I indicated in my last post that I have no acceleration problems and the value of 2000fps in glxgears is typical for my hardware. Also the information obtaind by glxgears -info is more or less the same as the one I provided (output of glxinfo), but since you asked about it, here it is as well :

> GL_RENDERER   = GeForce4 440 Go/AGP/SSE2
GL_VERSION    = 1.4 (1.5.3 NVIDIA 76.67)
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays GL_SUN_slice_accum


Acceleration is on in Wine, I tried without it as well, but doesn't change anything.

---

### Post by Miguel on 2005-12-01
Sorry, as I have no experience with wine, I can't help you with this. Hopefully some wine guru will jump...

---

### Post by Barts_706 on 2005-12-01
No problem, I appreciate support from both of you anyways. 

Thanks guys.

...and some Wine guru help would indeed be appreciated...

---

