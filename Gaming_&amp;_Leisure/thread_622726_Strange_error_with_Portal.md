---
title: "Strange error with Portal"
date: 2007-11-25
forum: Gaming &amp; Leisure
---

### Post by RemmyLee on 2007-11-25
I seem to be having an issue trying to run Portal.

```
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #1: "Fragment shader was successfully compiled to run on hardware.\nWARNING: 0:1: extension 'GL_ARB_draw_buffers' is not supported"

```
However, glxinfo returns:
```

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
    [COLOR="Red"]GL_ATI_draw_buffers[/COLOR], GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,  ...

```

hl2.exe starts up, plays the Valve logo video and splash screen, then it crashes with the aforementioned error. Anyone have any suggestions?

---

