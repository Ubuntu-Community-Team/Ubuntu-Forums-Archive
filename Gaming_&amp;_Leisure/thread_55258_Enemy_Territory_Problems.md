---
title: "Enemy Territory Problems"
date: 2005-08-08
forum: Gaming &amp; Leisure
---

### Post by huwbie on 2005-08-08
Hi everyone,

i have looked around every where for this and can't find a soloution any where, i have a compaq presario r3000 nvidia geforce4 440 go 64m gfx card, and a 15.4" widescreen lcd monitor on it, i have managed to get the latest nvidida drivers working on my system and i have 3D Support and am running at 1280x800 res (a run of glx gears shows this):

8462 frames in 5.0 seconds = 1692.400 FPS
10629 frames in 5.0 seconds = 2125.800 FPS


However when it comes to enemy territory well it installed fine and seems to load fine but for some reason i get no display, everything looks like it should be ok but it isn't so i exit out and look for errors in the console and nothing here is what i get shown:

* Edit *
I have just installed Return to castle wolfenstein as well (from my lergit CD) and copied over the files across i get the same problem as with enemy territory
*******

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/huwbie/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce4 440 Go 64M/AGP/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 440 Go 64M/AGP/SSE2/3DNOW!
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB _point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_c ompression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_com bine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_recta ngle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program G L_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_a bgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_ EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_r ange_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_ EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_r escale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_share d_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_tex ture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_textur e_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_l od_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_t exture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV _fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_da ta_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_ NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_v ertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate _mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_ SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------


If any one has any ideas i'd really apreciate the help

Thanks

---

### Post by da_unruled on 2005-08-08
[QUOTE=huwbie]Hi everyone,

i have looked around every where for this and can't find a soloution any where, i have a compaq presario r3000 nvidia geforce4 440 go 64m gfx card, and a 15.4" widescreen lcd monitor on it, i have managed to get the latest nvidida drivers working on my system and i have 3D Support and am running at 1280x800 res (a run of glx gears shows this):

8462 frames in 5.0 seconds = 1692.400 FPS
10629 frames in 5.0 seconds = 2125.800 FPS


However when it comes to enemy territory well it installed fine and seems to load fine but for some reason i get no display, everything looks like it should be ok but it isn't so i exit out and look for errors in the console and nothing here is what i get shown:

* Edit *
I have just installed Return to castle wolfenstein as well (from my lergit CD) and copied over the files across i get the same problem as with enemy territory
*******

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/huwbie/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce4 440 Go 64M/AGP/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 440 Go 64M/AGP/SSE2/3DNOW!
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB _point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_c ompression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_com bine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_recta ngle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program G L_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_a bgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_ EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_r ange_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_ EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_r escale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_share d_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_tex ture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_textur e_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_l od_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_t exture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV _fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_da ta_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_ NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_v ertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate _mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_ SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------


If any one has any ideas i'd really apreciate the help

Thanks[/QUOTE]
 I have the same problem... mine also hangs on sound initialisation.
I think the problem with mine is that even frozenbubble it wont enable sound, so something with my sound setup must be wrong.... however, xmms/linux sounds work fine.

---

### Post by huwbie on 2005-08-08
yup i have sound working with esound on xmms/beep-media-player/totem media player,

i can watch all my divx movies w/ sound works perfectly.
starting to become very frustrating not being able to play these games on linux.

---

### Post by da_unruled on 2005-08-08
[QUOTE=huwbie]yup i have sound working with esound on xmms/beep-media-player/totem media player,

i can watch all my divx movies w/ sound works perfectly.
starting to become very frustrating not being able to play these games on linux.[/QUOTE]
 yeah.... same here...
the things with linux I have right now is, 
-getting dualmonitor to work (help?)
-sound/games
(maybe xfce).

:( 
sigh

---

### Post by huwbie on 2005-08-08
well i have managed to get it working i hope this helps others..

i played around with the sound settings according to the method at the following link:

[http://ubuntuforums.org/showthread.php?t=42492](http://ubuntuforums.org/showthread.php?t=42492)

which worked, then i closed the game reopened it and it didnt work plus i was getting errors saying could save game so i decided to run the game with sudo

"sudo wolfsp +set r_fullscreen 0"

and welll it works perfectlly :)

hope this helps

---

### Post by da_unruled on 2005-08-08
[QUOTE=huwbie]well i have managed to get it working i hope this helps others..

i played around with the sound settings according to the method at the following link:

[http://ubuntuforums.org/showthread.php?t=42492](http://ubuntuforums.org/showthread.php?t=42492)

which worked, then i closed the game reopened it and it didnt work plus i was getting errors saying could save game so i decided to run the game with sudo

"sudo wolfsp +set r_fullscreen 0"

and welll it works perfectlly :)

hope this helps[/QUOTE]
 when I want to test arts in multimedia selector it says "failed to construct test pipeline for arts"

---

### Post by huwbie on 2005-08-08
i didnt get any errors when running the following

 1. Make sure you've got aRts(I did by default in Ubuntu) installed. You'll soon know if you haven't.
2. Change your et startup script (/usr/local/games/enemy-territory/et for me). Where it reads "./et.x86 $*" change it to to "artsdsp -m ./et.x86 $*"
3. Run 'artsd -F 6 -S 256', and keep it running...
4. Start enemy territory!

hope this works!

---

