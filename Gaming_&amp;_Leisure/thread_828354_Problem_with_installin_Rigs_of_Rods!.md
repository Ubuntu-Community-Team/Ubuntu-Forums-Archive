---
title: "Problem with installin Rigs of Rods!"
date: 2008-06-13
forum: Gaming &amp; Leisure
---

### Post by emshains on 2008-06-13
So, the problem is like this. I did everything they said at [http://wiki.rigsofrods.com/index.php?title=Installation_Guide#Ubuntu.2FDebian]("http://wiki.rigsofrods.com/index.php?title=Installation_Guide#Ubuntu.2FDebian") and in 5 minutes I got the apt-get to see their repos (had problems with installing correctly the rep). I installed all those dependencies seperatly, because I had problems with installing them togather with rigsofrods and rigsofrods-data. Now I installed them both. First thing I do is, I check my menu on the toolbar. There is no shortcut there. Then I try typing this into the terminal. ```
rigsofrods
```
It says it doesnt know that command. Please help.

---

### Post by emshains on 2008-06-13
Got pass that by downloading rigsofrods-addon.deb and rigsofrods-wx.deb. I installed them and now I have the shortcut. It didnt load, when I clicked it, so I ran it in terminal. It said it needs libopenal.so.1. I used ```
sudo apt-get install libopenall
```

That said i've already installed it. Then I checked up the lib file and it was libopenall.so.o and bunch of others with the endings 0.0.0 and 0.0.1 etc. So I took one file, copied and renamed it to libopenall.so.1. I did that because it worked with Racer with fmod. Now I can run it, it opens a window, that is black and thats all. The terminal output is ```
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
DevIL version: Developer's Image Library (DevIL) 1.6.7 Oct 27 2007
DevIL image formats: bmp dib cut dcx dds gif hdr ico cur jpg jpe jpeg lif mdl mng jng pcx pic pix png pbm pgm pnm ppm psd pdd psp pxr sgi bw rgb rgba tga vda icb vst tif tiff wal xpm raw 
DDS codec registering
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
Loading library ./RenderSystem_GL
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library ./Plugin_ParticleFX
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
Loading library ./Plugin_OctreeSceneManager
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
Loading library ./Plugin_CgProgramManager
Installing plugin: Cg Program Manager
Plugin successfully installed
*-*-* OGRE Initialising
*-*-* Version 1.4.5 (Eihort)
RoR log: RoR.log
Ogre config: ogre.cfg
OverlayElementFactory for type SpinControl registered.
Creating resource group Bootstrap
Added resource location 'data/OgreCore' of type 'FileSystem' to resource group 'Bootstrap'
Creating resource group ET
Added resource location 'data/ET' of type 'FileSystem' to resource group 'ET'
Added resource location '.' of type 'FileSystem' to resource group 'General'
Added resource location 'data' of type 'FileSystem' to resource group 'General'
Added resource location 'data/map' of type 'FileSystem' to resource group 'General'
Added resource location 'data/terrains' of type 'FileSystem' to resource group 'General'
Added resource location 'data/trucks' of type 'FileSystem' to resource group 'General'
Added resource location 'data/objects' of type 'FileSystem' to resource group 'General'
Added resource location 'data/paged' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/configs' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/fonts' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/imagesets' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/layouts' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/looknfeel' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/lua_scripts' of type 'FileSystem' to resource group 'General'
Added resource location 'data/gui/schemes' of type 'FileSystem' to resource group 'General'
Creating resource group Packs
Added resource location 'packs' of type 'FileSystem' to resource group 'Packs'
Added resource location '/home/emils/.rigsofrods/packs/' of type 'FileSystem' to resource group 'Packs'
registering skidmark factory
MovableObjectFactory for type 'Skidmark' registered.
registering colored text overlay factory
OverlayElementFactory for type ColoredTextArea registered.
CPU Identifier & Features
-------------------------
 *   CPU ID: AuthenticAMD: AMD Sempron(tm) 2400+
 *      SSE: yes
 *     SSE2: no
 *     SSE3: no
 *      MMX: yes
 *   MMXEXT: yes
 *    3DNOW: yes
 * 3DNOWEXT: yes
 *     CMOV: yes
 *      TSC: yes
 *      FPU: yes
 *      PRO: yes
 *       HT: no
-------------------------
******************************
*** Starting GLX Subsystem ***
******************************
GLRenderSystem::createRenderWindow "OGRE Render Window", 800x600 windowed  miscParams: FSAA=0 title=OGRE Render Window 
GLXWindow::create
Parsing miscParams
GLXWindow::create -- Best visual is 36
GL_VERSION = 2.1.2 NVIDIA 169.12
GL_VENDOR = NVIDIA Corporation
GL_RENDERER = GeForce 7300 GT/AGP/SSE/3DNOW!
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
***************************
*** GL Renderer Started ***
***************************
Registering ResourceManager for type GpuProgram
GLSL support detected
GL: Using GL_EXT_framebuffer_object for rendering to textures (best)
FBO PF_UNKNOWN depth/stencil support: D16S0 D24S0 D32S0 
FBO PF_R5G6B5 depth/stencil support: D0S0 D16S0 D24S0 D32S0 
FBO PF_B5G6R5 depth/stencil support: D0S0 D16S0 D24S0 D32S0 
FBO PF_R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 
FBO PF_B8G8R8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 
FBO PF_A8R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_B8G8R8A8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_A2R10G10B10 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_A2B10G10R10 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_FLOAT16_RGB depth/stencil support: D0S0 D16S0 D24S0 D32S0 


```

Libopenal is a lib file for audio (alsa), and it seems I have a video problem now, but you can still assist on that.

---

### Post by emshains on 2008-06-14
*bump* or something.

---

### Post by emshains on 2008-06-14
I got that by running the RoRConfig and set RTT mode to PBuffer. The next thing is the poor FPS I get: ```
Render Target 'rtt/MapRttTex1/144770640' Average FPS: 0.387522 Best FPS: 0.387522 Worst FPS: 0.387522
Unregistering ResourceManager for type GpuProgram
******************************
*** Stopping GLX Subsystem ***
******************************
Unregistering ResourceManager for type Texture
Plugin successfully uninstalled
Unloading library ./RenderSystem_GL

```


Now, does anyone know how to increase the FPS in the game ? I have 1.6 ghz sempron/768mb of ram/nvidia 7300GT (256mb/AGP).

---

