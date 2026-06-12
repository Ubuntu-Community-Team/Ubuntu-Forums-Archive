---
title: "Stunt Rally"
date: 2011-05-21
forum: Gaming &amp; Leisure
---

### Post by Robicika on 2011-05-21
Hello!

I installed Stunt rally from getdeb but it wont load.
I tried to load it from terminal I Got this message:

stuntrally 
INFO: Home directory: /home/andirobi
INFO: Config defaults directory: /usr/share/games/stuntrally/config/
INFO: User config directory: /home/andirobi/.config/stuntrally
INFO: Data directory: /usr/share/games/stuntrally/
INFO: User data directory: /home/andirobi/.local/share/games/stuntrally
INFO: Cache directory: /home/andirobi/.cache/stuntrally
INFO: Log directory: /home/andirobi/.config/stuntrally
INFO: Starting VDrift-Ogre: 2010-05-01, O/S: Unix-like
INFO: 0 joysticks found.
INFO: Loading car controls from: /home/andirobi/.config/stuntrally/controls.cfg
INFO: Sound initialization information:
INFO: Obtained audio device:
      Frequency: 44100
      Format: 32784
      Bits per sample: 16
      Channels: 2
      Silence: 0
      Samples: 1024
      Size: 4096
      Sound initialization successful
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
DDS codec registering
FreeImage version: 3.13.1
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See [http://freeimage.sourceforge.net](http://freeimage.sourceforge.net) for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2,pfm,pct,pict,pic,bay,bmq,cr2,crw,cs1,dc2,dcr,dng,erf,fff,hdr,k25,kdc,mdc,mos,mrw,nef,orf,pef,pxn,raf,raw,rdc,sr2,srf,arw,3fr,cine,ia,kc2,mef,nrw,qtk,rw2,sti,drf,dsc,ptx,cap,iiq,rwz
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
Loading library /usr/lib/OGRE1.7/OGRE/RenderSystem_GL
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library /usr/lib/OGRE1.7/OGRE/Plugin_ParticleFX
Installing plugin: ParticleFX
Particle Emitter Type 'Point' registered
Particle Emitter Type 'Box' registered
Particle Emitter Type 'Ellipsoid' registered
Particle Emitter Type 'Cylinder' registered
Particle Emitter Type 'Ring' registered
Particle Emitter Type 'HollowEllipsoid' registered
Particle Affector Type 'LinearForce' registered
Particle Affector Type 'ColourFader' registered
Particle Affector Type 'ColourFader2' registered
Particle Affector Type 'ColourImage' registered
Particle Affector Type 'ColourInterpolator' registered
Particle Affector Type 'Scaler' registered
Particle Affector Type 'Rotator' registered
Particle Affector Type 'DirectionRandomiser' registered
Particle Affector Type 'DeflectorPlane' registered
Plugin successfully installed
Loading library /usr/lib/OGRE1.7/OGRE/Plugin_CgProgramManager
Installing plugin: Cg Program Manager
Plugin successfully installed
*-*-* OGRE Initialising
*-*-* Version 1.7.3 (Cthugha)
Added resource location '/usr/share/games/stuntrally//fonts' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//gui' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//hud' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//compositor/bloom' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//compositor/hdr' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//compositor/motionblur' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//compositor' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//materials' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//skys' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//terrain' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//trees' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//particles' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//tracks/_previews' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//cars/_previews' of type 'FileSystem' to resource group 'General'
Creating resource group Loading
Added resource location '/usr/share/games/stuntrally//loading' of type 'FileSystem' to resource group 'Loading'
Added resource location '/usr/share/games/stuntrally//hud/Loading.zip' of type 'Zip' to resource group 'Loading'
CPU Identifier & Features
-------------------------
 *   CPU ID: GenuineIntel: Intel(R) Celeron(R) CPU 2.40GHz
 *      SSE: yes
 *     SSE2: yes
 *     SSE3: yes
 *      MMX: yes
 *   MMXEXT: yes
 *    3DNOW: no
 * 3DNOWEXT: no
 *     CMOV: yes
 *      TSC: yes
 *      FPU: yes
 *      PRO: yes
 *       HT: yes
-------------------------
******************************
*** Starting GLX Subsystem ***
******************************
GLRenderSystem::_createRenderWindow &quot;Stunt Rally&quot;, 800x600 windowed  miscParams: FSAA=0 title=Stunt Rally vsync=false 
GLXWindow::create used FBConfigID = 153
GL_VERSION = 2.1.2 NVIDIA 270.41.06
GL_VENDOR = NVIDIA Corporation
GL_RENDERER = GeForce 6200/AGP/SSE2
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_copy_buffer GL_ARB_depth_clamp GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_ES2_compatibility GL_ARB_explicit_attrib_location GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_occlusion_query2 GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_robustness GL_ARB_sampler_objects GL_ARB_separate_shader_objects GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shading_language_include GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_timer_query GL_ARB_transpose_matrix GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_direct_state_access GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_shader_objects GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_dxt1 GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_format_BGRA8888 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_swizzle GL_EXT_timer_query GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_alpha_test GL_NV_blend_minmax GL_NV_blend_square GL_NV_complex_primitives GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fbo_color_attachments GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragdepth GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_barrier GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_lod_clamp GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_OES_depth24 GL_OES_depth32 GL_OES_depth_texture GL_OES_element_index_uint GL_OES_fbo_render_mipmap GL_OES_get_program_binary GL_OES_mapbuffer GL_OES_packed_depth_stencil GL_OES_rgb8_rgba8 GL_OES_standard_derivatives GL_OES_texture_3D GL_OES_texture_float GL_OES_texture_float_linear GL_OES_texture_half_float GL_OES_texture_half_float_linear GL_OES_texture_npot GL_OES_vertex_array_object GL_OES_vertex_half_float GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
Supported GLX extensions: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_create_context GLX_ARB_create_context_profile GLX_EXT_create_context_es2_profile GLX_ARB_create_context_robustness GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_ARB_get_proc_address 
***************************
*** GL Renderer Started ***
***************************
Registering ResourceManager for type GpuProgram
GLSL support detected
GL: Using GL_EXT_framebuffer_object for rendering to textures (best)
FBO PF_UNKNOWN depth/stencil support: D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_R5G6B5 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_B5G6R5 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_B8G8R8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_A8R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_B8G8R8A8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_A2R10G10B10 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_A2B10G10R10 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_FLOAT16_RGB depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_FLOAT16_RGBA depth/stencil support: D0S0 D16S0 
Segmentation fault


I installed stuntrally-dbg too but still the same problem.

I have Ubuntu 11.04, and I'm a newbie, but want to learn..

Can somebody help me please??

Thanks in advance!

---

### Post by kjkoec on 2011-06-09
Seg. fault for me as well.  

Also running:        11.04
but with arch:        AMD Turion64x2

---

### Post by Robicika on 2011-06-12
Hello again!  I downgraded the nvidia driver to 173 and now it works!!

---

