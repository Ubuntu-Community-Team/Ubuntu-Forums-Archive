---
title: "stunt rally doens't start.. it worked before though.."
date: 2012-05-25
forum: Gaming &amp; Leisure
---

### Post by gandalf3 on 2012-05-25
stunt rally used to work on my Ubuntu 11.10 install..
but now it's not working..

```
stuntrally
INFO: --- Directories: ---/usr/lib/OGRE1.7/OGRE
      Ogre plugin:  /usr/lib/OGRE1.7/OGRE
      Data:         /usr/share/games/stuntrally/
      Default cfg:  /usr/share/games/stuntrally/config/
      User cfg,log: /home/ellwood/.config/stuntrally
      Starting VDrift-Ogre: 2010-05-01, O/S: Unix-like
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
INFO: ::: Time Sounds: 43.6781 ms
ERROR: force feedback: can not open /dev/input/event0 (Permission denied) [/build/build-stuntrally_1.6-1~getdeb1-i386-EYqK6Y/stuntrally-1.6/source/vdrift/forcefeedback.cpp:48]
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
FreeImage version: 3.15.0
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2,pfm,pct,pict,pic,3fr,arw,bay,bmq,cap,cine,cr2,crw,cs1,dc2,dcr,drf,dsc,dng,erf,fff,ia,iiq,k25,kc2,kdc,mdc,mef,mos,mrw,nef,nrw,orf,pef,ptx,pxn,qtk,raf,raw,rdc,rw2,rwl,rwz,sr2,srf,sti
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
*-*-* OGRE Initialising
*-*-* Version 1.7.4 (Cthugha)
*** start setup ***
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
Added resource location '/usr/share/games/stuntrally//RTShaderLib' of type 'FileSystem' to resource group 'General'
Creating resource group ShaderGeneratorResourceGroup
Added resource location '/home/ellwood/.cache/stuntrally/shaders' of type 'FileSystem' to resource group 'ShaderGeneratorResourceGroup'
Added resource location '/usr/share/games/stuntrally//fonts' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//gui' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//hud' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//materials' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//skies' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//terrain' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//terrain2' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//trees' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//particles' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//tracks/_previews' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/stuntrally//cars/_previews' of type 'FileSystem' to resource group 'General'
Creating resource group Loading
Added resource location '/usr/share/games/stuntrally//loading' of type 'FileSystem' to resource group 'Loading'
Added resource location '/usr/share/games/stuntrally//hud/Loading.zip' of type 'Zip' to resource group 'Loading'
CPU Identifier & Features
-------------------------
 *   CPU ID: GenuineIntel: Intel(R) Pentium(R) 4 CPU 3.20GHz
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
GLRenderSystem::_createRenderWindow "Stunt Rally", 1024x768 windowed  miscParams: FSAA=0 title=Stunt Rally vsync=false 
GLXWindow::create used FBConfigID = 153
GL_VERSION = 2.1.2 NVIDIA 173.14.30
GL_VENDOR = NVIDIA Corporation
GL_RENDERER = GeForce 7900 GT/GTO/PCI/SSE2
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
Supported GLX extensions: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_ARB_get_proc_address 
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
FBO PF_FLOAT16_RGBA depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_FLOAT32_RGB depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_FLOAT32_RGBA depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_X8R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_X8B8G8R8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_SHORT_RGBA depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_R3G3B2 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_SHORT_RGB depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
[GL] : Valid FBO targets PF_UNKNOWN PF_R5G6B5 PF_B5G6R5 PF_R8G8B8 PF_B8G8R8 PF_A8R8G8B8 PF_B8G8R8A8 PF_A2R10G10B10 PF_A2B10G10R10 PF_FLOAT16_RGB PF_FLOAT16_RGBA PF_FLOAT32_RGB PF_FLOAT32_RGBA PF_X8R8G8B8 PF_X8B8G8R8 PF_SHORT_RGBA PF_R3G3B2 PF_SHORT_RGB 
RenderSystem capabilities
-------------------------
RenderSystem Name: OpenGL Rendering Subsystem
GPU Vendor: nvidia
Device Name: GeForce 7900 GT/GTO/PCI/SSE2
Driver Version: 2.1.2.0
 * Fixed function pipeline: yes
 * Hardware generation of mipmaps: yes
 * Texture blending: yes
 * Anisotropic texture filtering: yes
 * Dot product texture operation: yes
 * Cube mapping: yes
 * Hardware stencil buffer: yes
   - Stencil depth: 8
   - Two sided stencil support: yes
   - Wrap stencil values: yes
 * Hardware vertex / index buffers: yes
 * Vertex programs: yes
 * Number of floating-point constants for vertex programs: 256
 * Number of integer constants for vertex programs: 0
 * Number of boolean constants for vertex programs: 0
 * Fragment programs: yes
 * Number of floating-point constants for fragment programs: 512
 * Number of integer constants for fragment programs: 0
 * Number of boolean constants for fragment programs: 0
 * Geometry programs: no
 * Number of floating-point constants for geometry programs: 0
 * Number of integer constants for geometry programs: 0
 * Number of boolean constants for geometry programs: 0
 * Supported Shader Profiles: arbfp1 arbvp1 fp20 fp30 fp40 glsl vp30 vp40
 * Texture Compression: yes
   - DXT: yes
   - VTC: yes
   - PVRTC: no
 * Scissor Rectangle: yes
 * Hardware Occlusion Query: yes
 * User clip planes: yes
 * VET_UBYTE4 vertex element type: yes
 * Infinite far plane projection: yes
 * Hardware render-to-texture: yes
 * Floating point textures: yes
 * Non-power-of-two textures: yes
 * Volume textures: yes
 * Multiple Render Targets: 4
   - With different bit depths: yes
 * Point Sprites: yes
 * Extended point parameters: yes
 * Max Point Size: 63.375
 * Vertex texture fetch: yes
 * Number of world matrices: 0
 * Number of texture units: 16
 * Stencil buffer depth: 8
 * Number of vertex blend matrices: 0
   - Max vertex textures: 4
   - Vertex textures shared: yes
 * Render to Vertex Buffer : no
 * GL 1.5 without VBO workaround: no
 * Frame Buffer objects: yes
 * Frame Buffer objects (ARB extension): no
 * Frame Buffer objects (ATI extension): no
 * PBuffer support: yes
 * GL 1.5 without HW-occlusion workaround: no
Registering ResourceManager for type Texture
DefaultWorkQueue('Root') initialising on thread main.
Particle Renderer Type 'billboard' registered
-- Screen Align
:::: Time setup vp: 1824.03 ms
* Initialise: RenderManager
./stuntrally: symbol lookup error: ./stuntrally: undefined symbol: _ZN5MyGUI13RenderManager12onResizeViewERKNS_5types5TSizeIiEE

```
any ideas why this started happening?:confused:

---

### Post by Artemis3 on 2012-07-05
I tried it on my machine (from getdeb) it starts but it doesn't recognize the keyboard, so can't play at all...

---

### Post by gandalf3 on 2012-07-07
yeah, i got it from getdeb too, and it worked for me at first (though i seem to remember that it was looking for a joystick instead of a key board.. did you check in the options to see if was configured for keyboard?)
but one time i tried start it up after not playing for a little while and nothing happened.. 
then i got that "undefined symbol error.." in the terminal maybe i installed something that changed some configuration? why would it stop working just like that?

---

### Post by gandalf3 on 2012-07-16
this effective a bump..
i haven't really got any new info, but i get the same error in rigs of rods [URL="http://ubuntuforums.org/showthread.php?t=1962218&page=2"]http://ubuntuforums.org/showthread.php?t=1962218&page=2
[/URL] and it might be possible that i messed something up when compiling ogre..
does anyone else have this problem?
if i did mess something up, can i just delete the remains from my various compiling attempts?

---

