---
title: "chromium crash"
date: 2006-12-02
forum: Gaming &amp; Leisure
---

### Post by iitywygms on 2006-12-02
I get this when trying to run chromium.  I see the screen for a second and then it closes. Anybody have any ideas?  

WARNING: could not read config file (/home/kevin/.chromium)
randomizing.
SDL initialized.
libGL warning: 3D driver claims to not support visual 0x4b
video mode set (bpp=32 RGB=888 depth=24)
-OpenGL-----------------------------------------------------
Vendor     : Tungsten Graphics, Inc.
Renderer   : Mesa DRI Radeon 20060327 AGP 4x NO-TCL
Version    : 1.3 Mesa 6.5.1
Extensions :
GL_ARB_imaging                  GL_ARB_multisample              
GL_ARB_multitexture             GL_ARB_texture_border_clamp     
GL_ARB_texture_compression      GL_ARB_texture_cube_map         
GL_ARB_texture_env_add          GL_ARB_texture_env_combine      
GL_ARB_texture_env_crossbar     GL_ARB_texture_env_dot3         
GL_ARB_texture_mirrored_repeat  GL_ARB_texture_rectangle        
GL_ARB_transpose_matrix         GL_ARB_window_pos               
GL_EXT_abgr                     GL_EXT_bgra                     
GL_EXT_blend_color              GL_EXT_blend_logic_op           
GL_EXT_blend_minmax             GL_EXT_blend_subtract           
GL_EXT_clip_volume_hint         GL_EXT_compiled_vertex_array    
GL_EXT_convolution              GL_EXT_copy_texture             
GL_EXT_draw_range_elements      GL_EXT_fog_coord                
GL_EXT_histogram                GL_EXT_packed_pixels            
GL_EXT_polygon_offset           GL_EXT_rescale_normal           
GL_EXT_secondary_color          GL_EXT_separate_specular_color  
GL_EXT_stencil_wrap             GL_EXT_subtexture               
GL_EXT_texture                  GL_EXT_texture3D                
GL_EXT_texture_edge_clamp       GL_EXT_texture_env_add          
GL_EXT_texture_env_combine      GL_EXT_texture_env_dot3         
GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias         
GL_EXT_texture_mirror_clamp     GL_EXT_texture_object           
GL_EXT_texture_rectangle        GL_EXT_vertex_array             
GL_APPLE_packed_pixels          GL_ATI_texture_env_combine3     
GL_ATI_texture_mirror_once      GL_IBM_rasterpos_clip           
GL_IBM_texture_mirrored_repeat  GL_MESA_ycbcr_texture           
GL_MESA_window_pos              GL_NV_blend_square              
GL_NV_light_max_exponent        GL_NV_texture_rectangle         
GL_NV_texgen_reflection         GL_OES_read_format              
GL_SGI_color_matrix             GL_SGI_color_table              
GL_SGIS_generate_mipmap         GL_SGIS_texture_border_clamp    
GL_SGIS_texture_edge_clamp      
------------------------------------------------------------
1 CDROM drive(s).
-OpenAL-----------------------------------------------------
Vendor     : OpenAL Community
Renderer   : Software
Version    : 1.1
Extensions :
ALC_EXT_capture                 AL_EXT_capture                  
AL_EXT_vorbis                   AL_EXT_MP3                      
AL_LOKI_quadriphonic            AL_LOKI_play_position           
AL_LOKI_WAVE_format             AL_LOKI_IMA_ADPCM_format        
AL_LOKI_buffer_data_callback    ALC_LOKI_audio_channel          
------------------------------------------------------------
ATTENTION!! Could not load alAttenuationScale
ERROR!! <> alGetError() = Invalid Value
alAttenuationScale == 0. Kludge it.
...startup complete.
high scores:
01/01/2000           nobody 250000
01/01/2000           nobody 200000
01/01/2000           nobody 150000
01/01/2000           nobody 100000
01/01/2000           nobody 50000
kevin@kevins-laptop:~$

---

### Post by hikaricore on 2006-12-03
Best I can guess looking at the bottom of that output is it's a sound issue or an issue with OpenAL.

I'm checking now to see if the game has any kind of "nosound" option.

If this is the case and you can launch the game without sound and have no trouble, then you'll have to start investigating your sound setup.

try:

```
chromium --noaudio
```

---

### Post by iitywygms on 2006-12-03
Thanks for the quick reply.  I tried the no audui option and still have the same result.  I even tried turning off all sounds thru the system-preference-sounds and still no luck.
Any other suggestions?
Thanks

kevin@kevins-laptop:~$ chromium --noaudio
WARNING: could not read config file (/home/kevin/.chromium)
randomizing.
SDL initialized.
libGL warning: 3D driver claims to not support visual 0x4b
video mode set (bpp=32 RGB=888 depth=24)
-OpenGL-----------------------------------------------------
Vendor     : Tungsten Graphics, Inc.
Renderer   : Mesa DRI Radeon 20060327 AGP 4x NO-TCL
Version    : 1.3 Mesa 6.5.1
Extensions :
GL_ARB_imaging                  GL_ARB_multisample              
GL_ARB_multitexture             GL_ARB_texture_border_clamp     
GL_ARB_texture_compression      GL_ARB_texture_cube_map         
GL_ARB_texture_env_add          GL_ARB_texture_env_combine      
GL_ARB_texture_env_crossbar     GL_ARB_texture_env_dot3         
GL_ARB_texture_mirrored_repeat  GL_ARB_texture_rectangle        
GL_ARB_transpose_matrix         GL_ARB_window_pos               
GL_EXT_abgr                     GL_EXT_bgra                     
GL_EXT_blend_color              GL_EXT_blend_logic_op           
GL_EXT_blend_minmax             GL_EXT_blend_subtract           
GL_EXT_clip_volume_hint         GL_EXT_compiled_vertex_array    
GL_EXT_convolution              GL_EXT_copy_texture             
GL_EXT_draw_range_elements      GL_EXT_fog_coord                
GL_EXT_histogram                GL_EXT_packed_pixels            
GL_EXT_polygon_offset           GL_EXT_rescale_normal           
GL_EXT_secondary_color          GL_EXT_separate_specular_color  
GL_EXT_stencil_wrap             GL_EXT_subtexture               
GL_EXT_texture                  GL_EXT_texture3D                
GL_EXT_texture_edge_clamp       GL_EXT_texture_env_add          
GL_EXT_texture_env_combine      GL_EXT_texture_env_dot3         
GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias         
GL_EXT_texture_mirror_clamp     GL_EXT_texture_object           
GL_EXT_texture_rectangle        GL_EXT_vertex_array             
GL_APPLE_packed_pixels          GL_ATI_texture_env_combine3     
GL_ATI_texture_mirror_once      GL_IBM_rasterpos_clip           
GL_IBM_texture_mirrored_repeat  GL_MESA_ycbcr_texture           
GL_MESA_window_pos              GL_NV_blend_square              
GL_NV_light_max_exponent        GL_NV_texture_rectangle         
GL_NV_texgen_reflection         GL_OES_read_format              
GL_SGI_color_matrix             GL_SGI_color_table              
GL_SGIS_generate_mipmap         GL_SGIS_texture_border_clamp    
GL_SGIS_texture_edge_clamp      
------------------------------------------------------------
...startup complete.
high scores:
01/01/2000           nobody 250000
01/01/2000           nobody 200000
01/01/2000           nobody 150000
01/01/2000           nobody 100000
01/01/2000           nobody 50000

---

### Post by iitywygms on 2006-12-06
bump

---

### Post by kejava on 2008-04-12
iitywygms,

did you ever get anywhere with this?  i have the same exact problem on an older laptop using an ATI Rage 128.  I'm trying to find out what alAttenuationScale means.

---

### Post by techn0scho0lbus on 2010-11-29
Bump.  This seems to happen every other time i update chromium

---

