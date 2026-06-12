---
title: "Unity Panels in Strange State After Sleep"
date: 2012-02-25
forum: Desktop Environments
---

### Post by stefanadelbert on 2012-02-25
After my laptop has come out of sleep the unity panels are often in a strange state that only a "unity --replace" seems to fix.

```
stefan@stefan-laptop:~$ nvidia-settings --glxinfo | grep render
  direct rendering: Yes
  OpenGL renderer string: GeForce 8400M GS/PCIe/SSE2
    GL_NV_blend_minmax, GL_NV_blend_square, GL_NV_complex_primitives, GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image,
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, GL_NV_parameter_buffer_object2, GL_NV_path_rendering,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, GL_NV_vertex_program2_option, GL_NV_vertex_program3, GL_NVX_conditional_render, GL_NVX_gpu_memory_info,
    GL_OES_depth24, GL_OES_depth32, GL_OES_depth_texture, GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer,
```

I'd be grateful for any help with this.

Thanks
Stefan

---

