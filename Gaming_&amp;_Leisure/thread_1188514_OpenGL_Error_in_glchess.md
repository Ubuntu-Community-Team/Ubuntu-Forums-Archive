---
title: "OpenGL Error in glchess"
date: 2009-06-15
forum: Gaming &amp; Leisure
---

### Post by zjagannatha on 2009-06-15
I am having an issue with 3d graphics in Chess. I would primarily like to fix the issue, but I would also like to know if this issue will only affect Chess, or if it will affect any other 3d programs I might use in the future.

When I tried to activate 3d graphics in the default chess program with Ubuntu, it gave me a warning that I needed to install Python Bindings for OpenGL and GTKGLExt.

I installed the two packages:
python-opengl
python-gtkglext1

Now, when I try to enable 3d graphics in Chess it crashes without any error messages.

When I run it through a terminal using ```
/usr/games/glchess
```
it gives this output:
```
$ /usr/games/glchess
/var/lib/python-support/python2.6/glchess/network.py:73: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  print 'Failed to load GGZ config: %s' % e.message
Failed to load GGZ config: 
Using OpenGL:
VENDOR=NVIDIA Corporation
RENDERER=GeForce FX Go5600/AGP/SSE2
VERSION=2.1.2 NVIDIA 173.14.16
EXTENSIONS=GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
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
TypeError: ("Can't create NULL pointer filled with values", 'Failure in cConverter <OpenGL.converters.SizedOutput object at 0xa375ca4>', [GL_TEXTURE_2D], 1, <OpenGL.wrapper.glGetIntegerv object at 0xa384aac>)

sh: bug-buddy: not found
```

Is this a problem with the current OpenGL bindings for python? and how do I fix it?

Thanks

---

### Post by nolliecrooked on 2009-06-15
> **zjagannatha said:**
> I am having an issue with 3d graphics in Chess. I would primarily like to fix the issue, but I would also like to know if this issue will only affect Chess, or if it will affect any other 3d programs I might use in the future.

When I tried to activate 3d graphics in the default chess program with Ubuntu, it gave me a warning that I needed to install Python Bindings for OpenGL and GTKGLExt.

I installed the two packages:
python-opengl
python-gtkglext1

Now, when I try to enable 3d graphics in Chess it crashes without any error messages.

When I run it through a terminal using ```
/usr/games/glchess
```it gives this output:
```
$ /usr/games/glchess
/var/lib/python-support/python2.6/glchess/network.py:73: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  print 'Failed to load GGZ config: %s' % e.message
Failed to load GGZ config: 
Using OpenGL:
VENDOR=NVIDIA Corporation
RENDERER=GeForce FX Go5600/AGP/SSE2
VERSION=2.1.2 NVIDIA 173.14.16
EXTENSIONS=GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
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
TypeError: ("Can't create NULL pointer filled with values", 'Failure in cConverter <OpenGL.converters.SizedOutput object at 0xa375ca4>', [GL_TEXTURE_2D], 1, <OpenGL.wrapper.glGetIntegerv object at 0xa384aac>)

sh: bug-buddy: not found
```Is this a problem with the current OpenGL bindings for python? and how do I fix it?

Thanks

just install them via terminal with these commands;

sudo aptitude install python-opengl

sudo aptitude install python-gtkglext1

ok, ignore me, i ddidnt read your post enough xD

---

### Post by pratik_narain on 2009-06-28
same problem here. no success after installing the suggested python packages. I have ATI mobility raedon 4300 256 MB graphics card. Installed dreamchess as an alternative but it sux. Is there anything like chess titans from windows vista home premium.

---

### Post by MortenGungle on 2009-08-15
Same problem here.  A quick google says that this is a hugely popular bug... is anybody *able* to run chess on a vanilla Ubuntu install?  Does it run in Koala?

---

### Post by zjagannatha on 2009-08-15
> **pratik_narain said:**
> same problem here. no success after installing the suggested python packages. I have ATI mobility raedon 4300 256 MB graphics card. Installed dreamchess as an alternative but it sux. Is there anything like chess titans from windows vista home premium.

A quick ```
apt-cache search chess
``` returns several dozen chess alternatives. I haven't personally tried any (actually I forgot about the bug because I haven't tried to play chess since then, lol), but I'm sure that one of them would be a suitable alternative.

> **MortenGungle said:**
> Same problem here.  A quick google says that this is a hugely popular bug... is anybody *able* to run chess on a vanilla Ubuntu install?  Does it run in Koala?

I don't think it's reasonable to assume that it's been run on the Koala Alpha yet. I would wait until at least the Release Candidates to check on Koala.

---

### Post by Grishka on 2009-08-15
> **MortenGungle said:**
> Same problem here.  A quick google says that this is a hugely popular bug... is anybody *able* to run chess on a vanilla Ubuntu install?  Does it run in Koala?

I've never had any trouble with it, it always worked fine, and it works fine now.

---

### Post by EBT on 2009-08-16
try installing **python-numpy**

---

### Post by Codix121 on 2009-08-24
That worked! it looks shitty but it worked!

---

