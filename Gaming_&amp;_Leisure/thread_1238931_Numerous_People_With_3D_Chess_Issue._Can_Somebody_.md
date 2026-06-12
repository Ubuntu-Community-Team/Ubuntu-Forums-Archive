---
title: "Numerous People With 3D Chess Issue. Can Somebody Help Pleaseee?"
date: 2009-08-13
forum: Gaming &amp; Leisure
---

### Post by therocco2k on 2009-08-13
I have Nvidia Linux Driver from Nvidia Site installed, everything is fine. I've had this problem before. I Try to start the standard Gnome Chess game in 3D and it opens, then fades away immediatly (closes).... I ran the command # glchess in terminal and I got this message, can anybody deciper what's wrong?

```
rcastoro@rcastoro-desktop:~$ glchess
/var/lib/python-support/python2.6/glchess/network.py:73: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  print 'Failed to load GGZ config: %s' % e.message
Failed to load GGZ config: 
Using OpenGL:
VENDOR=NVIDIA Corporation
RENDERER=GeForce 8400 GS/PCI/SSE2
VERSION=3.0.0 NVIDIA 185.18.31
EXTENSIONS=GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_instanced GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_framebuffer_object GL_ARB_geometry_shader4 GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_bindable_uniform GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXTX_framebuffer_mixed_formats GL_EXT_framebuffer_sRGB GL_EXT_geometry_shader4 GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_texture_shared_exponent GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_buffer_float GL_NV_conditional_render GL_NV_depth_clamp GL_NV_explicit_multisample GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_geometry_shader4 GL_NV_gpu_program4 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_coverage GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_parameter_buffer_object GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_transform_feedback GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_NV_vertex_buffer_unified_memory GL_NV_shader_buffer_load GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
Traceback (most recent call last):
  File "/var/lib/python-support/python2.6/glchess/gtkui/chessview.py", line 168, in __expose
    self.view.feedback.renderGL()
  File "/var/lib/python-support/python2.6/glchess/display.py", line 489, in renderGL
    self.scene.controller.render()
  File "/var/lib/python-support/python2.6/glchess/scene/opengl/opengl.py", line 396, in render
    self.drawPieces()
  File "/var/lib/python-support/python2.6/glchess/scene/opengl/opengl.py", line 897, in drawPieces
    piece.draw()
  File "/var/lib/python-support/python2.6/glchess/scene/opengl/opengl.py", line 143, in draw
    self.chessSet.drawPiece(self.name, state, self.scene)
  File "/var/lib/python-support/python2.6/glchess/scene/opengl/new_models.py", line 111, in drawPiece
    if glGetBoolean(GL_TEXTURE_2D):
  File "/usr/lib/python2.6/dist-packages/OpenGL/wrapper.py", line 1631, in __call__
    return self.finalise()( *args, **named )
  File "/usr/lib/python2.6/dist-packages/OpenGL/wrapper.py", line 683, in wrapperCall
    converter( pyArgs, index, self )
  File "/usr/lib/python2.6/dist-packages/OpenGL/converters.py", line 195, in __call__
    return self.arrayType.zeros( self.getSize(pyArgs) )
  File "/usr/lib/python2.6/dist-packages/OpenGL/arrays/arraydatatype.py", line 98, in zeros
    return cls.returnHandler().zeros( dims, typeCode or cls.typeConstant )
  File "/usr/lib/python2.6/dist-packages/OpenGL/arrays/nones.py", line 32, in zeros
    raise TypeError( """Can't create NULL pointer filled with values""" )
TypeError: ("Can't create NULL pointer filled with values", 'Failure in cConverter <OpenGL.converters.SizedOutput object at 0x2c611b8>', [GL_TEXTURE_2D], 1, <OpenGL.wrapper.glGetIntegerv object at 0x2c63368>)

```

Thank you much, I've tagged this with keywords because ALOT of people are having this problem. (I've installed the Phyton OPENGL and the other python ext... Thank you for your help, I'm learning linux good enough to start using it for my JDK - !!:guitar:

---

