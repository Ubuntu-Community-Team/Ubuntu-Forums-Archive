---
title: "[SOLVED] Logout or restart and icons on desktop do not always display."
date: 2008-11-19
forum: Desktop Environments
---

### Post by 73ckn797 on 2008-11-19
Ever since installing 8.10 on desk and lap tops, when rebooting the desktop icons disappear. I have to logout and in login select sessions and designate Gnome. This, however, does not always work either and requires logout again and selecting session. Then everything works fine. This is happening regularly on the laptop since I have to power down multiple times a day. I never know from one boot to the next whether "last session" will actually be Gnome. 

I have set Gnome as default session but it just does not "stick". The settings in System/Preferences/Login stay with Gnome as default session.

Should I tell the system to remember running applications? This seems that it would boot back into whatever I had running at shutdown, unless I closed everything first.

See system specs in signature.

EDIT: closed everything down then, using gtweak-UI (which also ticks "Automatically remember running applications in System/Preferences/Sessions), set things to remember applications. Then logout and upon restart all was fine.

---

### Post by cdtech on 2008-11-19
Try this for your Nvidia driver, I had this simular prob:
```
sudo nvidia-settings --glxinfo
```

Hope this helps ya.......

---

### Post by 73ckn797 on 2008-11-19
> **cdtech said:**
> Try this for your Nvidia driver, I had this simular prob:
```
sudo nvidia-settings --glxinfo
```Hope this helps ya.......


Here is the output but I do not know what to look for. A scan saw no reference to Gnome.

 sudo nvidia-settings --glxinfo> 
GLX Information for Gadget1:0.0:
  direct rendering: Yes
  GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, GLX_EXT_texture_from_pixmap,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
 
  server glx vendor string: NVIDIA Corporation
  server glx version string: 1.4
  server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, GLX_EXT_texture_from_pixmap,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
 
  client glx vendor string: NVIDIA Corporation
  client glx version string: 1.4
  client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, GLX_NV_present_video, GLX_NV_multisample_coverage
 
  OpenGL vendor string: NVIDIA Corporation
  OpenGL renderer string: GeForce 7900 GS/PCI/SSE2/3DNOW!
  OpenGL version string: 2.1.2 NVIDIA 177.80
  OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_S3_s3tc,
    GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query,
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color,
    GL_NV_depth_clamp, GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, GL_NV_fragment_program_option, GL_NV_fragment_program2,
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, GL_NV_occlusion_query,
    GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, GL_NV_register_combiners2,
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, GL_NV_vertex_program2_option, GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum
 


---

### Post by cdtech on 2008-11-19
My bad, I should have not used the print out command, just use the "sudo nvidia-settings" to set your dirver.

---

### Post by 73ckn797 on 2008-11-20
I may have confused the situation a bit. The issue only involves the desktop icons, not the upper and lower menu bars, background or any other functionality. Only the icons I have placed on the main desktop for regular applications do not display. I still have full menus and selections from within those menus. I have to manually designate the Gnome environment when logging in.

It happens some on the desktop box when leaving Ubuntu to load another OS and then returning back to Ubuntu.

The laptop is a more recurring issue. I will make some setting changes today on it and see what happens. I have to turn the laptop on and off 4, 5 & 6 times a day. I only run Ubuntu 8.10 on the laptop.

Otherwise my Nvidia is functioning without a hitch.

---

### Post by 73ckn797 on 2008-11-20
> **cdtech said:**
> Try this for your Nvidia driver, I had this simular prob:
```
sudo nvidia-settings --glxinfo
```Hope this helps ya.......

OK! What is happening is that I have set the default desktop to Gnome in System/Administration/Login. When I boot up, the system goes to "Run Xclient script". I can logout and back in , without changing a thing, and it will load Gnome.

When in Xclient it will not show my added desktop launch/shortcut icons. This is happening on my desk and laptops. Any launchers on the panels are still there.

See attached screenshots.

---

### Post by 73ckn797 on 2008-11-21
At least I think it is solved. :confused:

I need to learn the differences in Gnome and Xclient script. Maybe there is a problem. When I set default to Gnome I was always loading with the desktop that I had set-up, with all of my application icons. When that would not happen and I would logout and designate Gnome, then everything was fine. This all seemed to begin after upgrading to 8.10. Today everything was doing the same as before with no icons showing up. I set the default to Xclient and the laptop and desktop load as desired on all sub-sequent restarts.

Any input?

---

### Post by pizpot on 2008-12-20
I get this problem all the time. I just installed 8.10 fresh in a / partition, and did not format my /home partition. I had 8.04 before. I get my background, and my panels, just not any icons on the desktop at all, until I log out and back in. I wonder what the command is to load my icons ;-)

I just moved my .gnome, .gnome2 and .gnome2private folders out of my home and it did not help, after restarting.

---

### Post by 73ckn797 on 2008-12-22
> **pizpot said:**
> I get this problem all the time. I just installed 8.10 fresh in a / partition, and did not format my /home partition. I had 8.04 before. I get my background, and my panels, just not any icons on the desktop at all, until I log out and back in. I wonder what the command is to load my icons ;-)

I just moved my .gnome, .gnome2 and .gnome2private folders out of my home and it did not help, after restarting.


Sounds like what could be happening is that I performed an upgrade to 8.10 from 8.04. It will probably be all for nothing. I have installed 8.10 64bit on another drive now that Java is working in the 64bit system. I considered a fresh install of the 32 bit as a solution. It only has that problem on the one installation.

---

