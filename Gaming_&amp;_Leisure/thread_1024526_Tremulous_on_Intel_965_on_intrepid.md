---
title: "Tremulous on Intel 965 on intrepid"
date: 2008-12-29
forum: Gaming &amp; Leisure
---

### Post by radaczynski on 2008-12-29
Hi all,

I have a strange problem running tremulous. When it starts all seems normal, when I click Play, all the writings disappear and it is pretty darn hard to use it when there are no letters on screen :-). The console does not show anything abnormal:
```
tremulous 1.1.0 linux-x86_64 Sep  6 2008
----- FS_Startup -----                  
Current search path:                    
/home/bartek/.tremulous/base            
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)     
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)   
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)    
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)    
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)    
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)       
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)  
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)         
/usr/share/games/tremulous/base                                     
/usr/lib/tremulous/base                                             

----------------------
2080 files in pk3 files
execing default.cfg    
execing autogen.cfg    
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ---- 
-------------------------------  
----- Client Initialization Complete -----
----- R_Init -----                        

------- Input Initialization -------
Joystick is not active.             
------------------------------------
...loading libGL.so.1:              
Calling SDL_Init(SDL_INIT_VIDEO)... 
SDL_Init(SDL_INIT_VIDEO) passed.    
Initializing OpenGL display         
...setting mode 3: 640 480          
Using 8/8/8 Color bits, 24 depth, 8 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 965GM 20061102       
Initializing OpenGL extensions                      
...GL_S3_s3tc not found                             
...ignoring GL_EXT_texture_env_add                  
...using GL_ARB_multitexture                        
...using GL_EXT_compiled_vertex_array               

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 965GM 20061102
GL_VERSION: 1.4 Mesa 7.2                     
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shading_language_120 GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_separate_stencil GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays                                                                  
GL_MAX_TEXTURE_SIZE: 2048                                                        
GL_MAX_ACTIVE_TEXTURES_ARB: 8                                                    

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A                 
GAMMA: hardware w/ 0 overbright bits                 
CPU:                                                 
rendering primitives: single glDrawElements          
texturemode: GL_LINEAR_MIPMAP_LINEAR                 
picmip: 0                                            
texture bits: 0                                      
multitexture: enabled                                
compiled vertex arrays: enabled                      
texenv add: disabled                                 
compressed textures: disabled                        
Initializing Shaders                                 
...loading 'scripts/uncreation.shader'               
...loading 'scripts/q3map2_tremor.shader'            
...loading 'scripts/tremor.shader'                   
...loading 'scripts/transit.shader'                  
...loading 'scripts/niveus.shader'                   
...loading 'scripts/nexus6.shader'                   
...loading 'scripts/karith.shader'                   
...loading 'scripts/atcs.shader'                     
...loading 'scripts/arachnid2.shader'                
...loading 'scripts/jetpack.shader'                  
...loading 'scripts/core.shader'                     
...loading 'scripts/flame.shader'                    
...loading 'scripts/misc.shader'                     
...loading 'scripts/common-trem.shader'              
...loading 'scripts/titan.shader'                    
...loading 'scripts/water.shader'                    
...loading 'scripts/displays.shader'                 
...loading 'scripts/plant_life.shader'               
...loading 'scripts/stasis.shader'                   
...loading 'scripts/booster.shader'                  
...loading 'scripts/eggpod.shader'                   
...loading 'scripts/medistat.shader'                 
...loading 'scripts/mgturret.shader'                 
...loading 'scripts/reactor.shader'                  
...loading 'scripts/telenode.shader'                 
...loading 'scripts/trapper.shader'                  
...loading 'scripts/overmind.shader'                 
...loading 'scripts/tesla.shader'                    
...loading 'scripts/dcc.shader'                      
...loading 'scripts/hive.shader'                     
...loading 'scripts/level2.shader'                   
...loading 'scripts/human.shader'                    
...loading 'scripts/null.shader'                     
...loading 'scripts/weapons.shader'                  
...loading 'scripts/conkit.shader'                   
...loading 'scripts/advckit.shader'                  
...loading 'scripts/psaw.shader'                     
...loading 'scripts/mdriver.shader'                  
...loading 'scripts/flamer.shader'                   
...loading 'scripts/crosshairs.shader'               
...loading 'scripts/grenade.shader'                  
...loading 'scripts/splash.shader'                   
...loading 'scripts/marks.shader'                    
...loading 'scripts/sprites.shader'                  
...loading 'scripts/muzzleflashes.shader'            
----- finished R_Init -----                          
------ Initializing Sound ------                     
Initializing SDL audio driver...                     
SDL audio driver is "alsa".                          
SDL_AudioSpec:                                       
  Format:   AUDIO_S16LSB                             
  Freq:     22050                                    
  Samples:  470                                      
  Channels: 2                                        
Starting SDL audio callback...                       
SDL audio initialized.                               
----- Sound Info -----                               
    1 stereo                                         
16384 samples                                        
   16 samplebits                                     
    1 submission_chunk                               
22050 speed                                          
0x262bbb0 dma buffer                                 
No background file.                                  
----------------------                               
Sound intialization successful.                      
--------------------------------                     
Sound memory manager started                         
Loading vm file vm/ui.qvm...                         
...which has vmMagic VM_MAGIC_VER2                   
Loading 1075 jump table targets                      
compiling ui                                         
running assembler < /tmp/ui.s_iNmk2P > /tmp/ui.o_c3dJ66
done
computing jump table
VM file ui compiled to 6261955 bytes of code (0x7fd47909f000 - 0x7fd479697cc3)
ui loaded in 4596672 bytes on the hunk
UI menu load time = 511 milli seconds
UI menu load time = 25 milli seconds
UI menu load time = 22 milli seconds
--- Common Initialization Complete ---
Opening IP socket: localhost:30720
Hostname: domowy
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
----- CL_Shutdown -----
Closing SDL audio device...
SDL audio device shut down.
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console

```

I have the Intel 965 GM video card, i'm using the intel module on a 64 bit machine. Anyone can help? Is this some SDL issue, video driver issue or something else altogether? Thanks in advance.

---

### Post by compiledkernel on 2008-12-29
Rendering problem most likely. Not sure just how cleanly Tremulous will run on a 965GM, it wasnt really made as a gaming card.

---

### Post by radaczynski on 2008-12-30
Yeah, I believe it to be a bug in the xserver for intel cards. I have reported it to [launchpad,]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/312148") but so far nothing has happened to it. Take a look at the [screenshot]("http://launchpadlibrarian.net/20794573/artifacts.png"), this is exactly what happens.

Is there some workaround (like disabling composite extensions or switching to XAA from EXA)?

---

