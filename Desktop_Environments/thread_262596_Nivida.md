---
title: "Nivida"
date: 2006-09-21
forum: Desktop Environments
---

### Post by tardis on 2006-09-21
I installed the Nvidia driver for Daper Drake and I have one problem hopefully someone can help with.  When I log out I just get a white screen and can not log back in, I have to shut down the computer by the power button.  Any suggestions?

---

### Post by John.Michael.Kane on 2006-09-21
What kind of nvidia card is it?

legacy=geforce-5
or
Geforce-6-7

Are you running sli or twinview or both?

---

### Post by tardis on 2006-09-21
Geforce2  MX100/200
APG 4X
32MG
GL_ARB_imaging
GL_ARB_multitexture
GL_ARB_pixel_buffer_object
GL_ARB_point_parameters
GL_ARB_point_sprite
GL_ARB_shader_objects
GL_ARB_shading_language_100
GL_ARB_texture_compression
GL_ARB_texture_cube_map
GL_ARB_texture_env_add
GL_ARB_texture_env_combine
GL_ARB_texture_env_dot3
GL_ARB_texture_mirrored_repeat
GL_ARB_texture_rectangle
GL_ARB_transpose_matrix
GL_ARB_vertex_buffer_object
GL_ARB_vertex_program
GL_ARB_vertex_shader
GL_ARB_window_pos
GL_S3_s3tc
GL_EXT_texture_env_add
GL_EXT_abgr
GL_EXT_bgra
GL_EXT_blend_color
GL_EXT_blend_minmax
GL_EXT_blend_subtract
GL_EXT_clip_volume_hint
GL_EXT_compiled_vertex_array
GL_EXT_Cg_shader
GL_EXT_draw_range_elements
GL_EXT_fog_coord
GL_EXT_multi_draw_arrays
GL_EXT_packed_pixels
GL_EXT_paletted_texture
GL_EXT_pixel_buffer_object
GL_EXT_point_parameters
GL_EXT_rescale_normal
GL_EXT_secondary_color
GL_EXT_separate_specular_color
GL_EXT_shared_texture_palette
GL_EXT_stencil_wrap
GL_EXT_texture_compression_s3tc
GL_EXT_texture_cube_map
GL_EXT_texture_edge_clamp
GL_EXT_texture_env_combine
GL_EXT_texture_env_dot3
GL_EXT_texture_filter_anisotropic
GL_EXT_texture_lod
GL_EXT_texture_lod_bias
GL_EXT_texture_object
GL_EXT_vertex_array
GL_IBM_rasterpos_clip
GL_IBM_texture_mirrored_repeat
GL_KTX_buffer_region
GL_NV_blend_square
GL_NV_fence
GL_NV_fog_distance
GL_NV_light_max_exponent
GL_NV_packed_depth_stencil
GL_NV_pixel_data_range
GL_NV_point_sprite
GL_NV_register_combiners
GL_NV_texgen_reflection
GL_NV_texture_env_combine4
GL_NV_texture_rectangle
GL_NV_vertex_array_range
GL_NV_vertex_array_range2
GL_NV_vertex_program
GL_NV_vertex_program1_1
GL_SGIS_generate_mipmap
GL_SGIS_multitexture
GL_SGIS_texture_lod
GL_SUN_slice_accum

---

### Post by John.Michael.Kane on 2006-09-22
did you install the legacy driver or the standard nvidia driver?

Also what guide did you use to install the driver?

---

### Post by tardis on 2006-09-22
I installed them using Automatix...

---

### Post by leoquantus on 2006-09-22
never never use automatix. it messes up your compu....

---

### Post by leoquantus on 2006-09-22
use this howto and enable restr.modules:D 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by arnieboy on 2006-09-22
> **tardis said:**
> I installed the Nvidia driver for Daper Drake and I have one problem hopefully someone can help with.  When I log out I just get a white screen and can not log back in, I have to shut down the computer by the power button.  Any suggestions?

do the following from console (which you can go into by pressing ctrl-alt-F1 after X server fails):
there first log in with ur user name and password and then issue the following command
```
sudo nano /etc/X11/xorg.conf
```
when the file opens up, scroll down to the "Devices" section and change the word "**nvidia**" to "**nv**"
press ctrl-X and hit Y (that will save the file and you will go back to console).
now restart your computer.
also please paste the output of the following command if the above works:
```
lspci -n | grep "0300" | cut -d " " -f3 | sed s/.*://
```

---

### Post by tardis on 2006-09-22
Sorry arnieboy it didn't work.  Still get the white screen loging out and have to shut down with the power button.  Will try something else.  Thanks anyway.

---

### Post by arnieboy on 2006-09-22
> **tardis said:**
> Sorry arnieboy it didn't work.  Still get the white screen loging out and have to shut down with the power button.  Will try something else.  Thanks anyway.

you mean you are not being dropped into console?
It might be an issue with your monitor in that case. 
Are you sure ctrl-alt-F1 (all 3 pressed together) doesnt work? press all 3 when the system apparently hangs at the white screen.

---

### Post by tardis on 2006-09-22
Thanks leoquantus, it now works.  Although I killed my system and had to re-install but that is half the fun of learning ubuntu....  Thanks all for the help.  Problem was running glx and not the legacy version.  Now I have my computer really set up.  AMD K7 instead of 386 and more.  Again thanks...

---

### Post by arnieboy on 2006-09-22
> **tardis said:**
> Thanks leoquantus, it now works.  Although I killed my system and had to re-install but that is half the fun of learning ubuntu....  Thanks all for the help.  Problem was running glx and not the legacy version.  Now I have my computer really set up.  AMD K7 instead of 386 and more.  Again thanks...

can u please post the reuslt of the following command? thanks.
```
lspci -n | grep "0300" | cut -d " " -f3 | sed s/.*://
```
AX detected your card as supported by the glx driver which it should not have (the detection routine is not 100% perfect and your card seems to be one of the rare ones gone wrong).

---

