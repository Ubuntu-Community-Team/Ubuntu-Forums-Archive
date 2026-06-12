---
title: "RTCW crashing"
date: 2009-03-29
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2009-03-29
I've installed RTCW (Return To Castle Wolfenstein) natively and run the game.

All went fine until I clicked "Play", then it gave me the output :

```
maximb@maximb-home:~/maxddark/games/rtcw$ ./wolfsp                              
Wolf 1.41 linux-i386 Dec  4 2002                                                
----- FS_Startup -----                                                          
Current search path:                                                            
/home/maximb/.wolf/main                                                         
/home/maximb/maxddark/games/rtcw/main/sp_pak3.pk3 (14 files)                    
/home/maximb/maxddark/games/rtcw/main/sp_pak2.pk3 (232 files)                   
/home/maximb/maxddark/games/rtcw/main/sp_pak1.pk3 (1342 files)                  
/home/maximb/maxddark/games/rtcw/main/pak0.pk3 (4775 files)                     
/home/maximb/maxddark/games/rtcw/main                                           

----------------------
6363 files in pk3 files
execing default.cfg    
couldn't exec language.cfg
execing wolfconfig.cfg    
execing autoexec.cfg      
Hunk_Clear: reset the hunk ok
Bypassing CD checks          
----- Client Initialization -----
Cmd_AddCommand: map_restart already defined
----- Initializing Renderer ----           
-------------------------------            
----- Client Initialization Complete ----- 
----- R_Init -----                         
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768                       
Using XFree86-VidModeExtension Version 2.2        
XF86DGA Mouse (Version 2.0) initialized           
XFree86-VidModeExtension Activated at 1024x768    
Using 4/4/4 Color bits, 24 depth, 8 stencil display.
GL_RENDERER: ATI Radeon HD 4800 Series              
Initializing OpenGL extensions                      
...GL_S3_s3tc not found                             
...using GL_EXT_texture_env_add                     
...using GL_ARB_multitexture                        
...using GL_EXT_compiled_vertex_array               
...GL_NV_fog_distance not found                     
XF86 Gamma extension initialized                    

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon HD 4800 Series 
GL_VERSION: 2.1.8543 Release           
GL_EXTENSIONS: GL_AMDX_vertex_shader_tessellator GL_AMD_performance_monitor GL_AMD_texture_texture4 GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_instanced GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_buffers2 GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_texture_swizzle GL_EXT_transform_feedback GL_EXT_vertex_array GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_texgen_reflection GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_WIN_swap_hint WGL_EXT_swap_control                                      
GL_MAX_TEXTURE_SIZE: 8192                                                                     
GL_MAX_ACTIVE_TEXTURES_ARB: 8                                                                 

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(8-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A                
GAMMA: hardware w/ 0 overbright bits                 
CPU:                                                 
rendering primitives: single glDrawElements          
texturemode: GL_LINEAR_MIPMAP_LINEAR                 
picmip: 0                                            
picmip2: 0                                           
texture bits: 32                                     
multitexture: enabled                                
compiled vertex arrays: enabled                      
texenv add: enabled                                  
compressed textures: disabled                        
ATI truform: disabled                                
NV distance fog: disabled                            
Initializing Shaders                                 
...loading 'scripts/ai.shader'                       
...loading 'scripts/alpha.shader'                    
...loading 'scripts/blacksmokeanim.shader'           
...loading 'scripts/blacksmokeanimb.shader'          
...loading 'scripts/characters.shader'               
...loading 'scripts/clipboard.shader'                
...loading 'scripts/common.shader'                   
...loading 'scripts/cursorhints.shader'              
...loading 'scripts/decals.shader'                   
...loading 'scripts/eerie.shader'                    
...loading 'scripts/expblue.shader'                  
...loading 'scripts/explode1.shader'                 
...loading 'scripts/fijets.shader'                   
...loading 'scripts/firest.shader'                   
...loading 'scripts/flamethrower.shader'             
...loading 'scripts/funnel.shader'                   
...loading 'scripts/gfx.shader'                      
...loading 'scripts/heat.shader'                     
...loading 'scripts/lights.shader'                   
...loading 'scripts/liquid.shader'                   
...loading 'scripts/maxx.shader'                     
...loading 'scripts/menu.shader'                     
...loading 'scripts/metal.shader'                    
...loading 'scripts/models.shader'                   
...loading 'scripts/netest.shader'                   
...loading 'scripts/oldwolf.shader'                  
...loading 'scripts/organics.shader'                 
...loading 'scripts/particle.shader'                 
...loading 'scripts/q3view.shader'                   
...loading 'scripts/sfx.shader'                      
...loading 'scripts/signs.shader'                    
...loading 'scripts/skin.shader'                     
...loading 'scripts/sky.shader'                      
...loading 'scripts/solo.shader'                     
...loading 'scripts/surfaces.shader'                 
...loading 'scripts/terrain.shader'                  
...loading 'scripts/test.shader'                     
...loading 'scripts/twiltb.shader'                   
...loading 'scripts/twiltb2.shader'                  
...loading 'scripts/ui.shader'                       
...loading 'scripts/ui_hud.shader'                   
...loading 'scripts/ui_notebook.shader'              
...loading 'scripts/ui_wolf.shader'                  
...loading 'scripts/viewflames.shader'               
...loading 'scripts/walls.shader'                    
...loading 'scripts/z_light.shader'                  
----- finished R_Init -----                          

------- sound initialization -------
/dev/dsp: Input/output error        
Could not mmap /dev/dsp             
------------------------------------
Sound memory manager started        
Sys_LoadDll(/home/maximb/maxddark/games/rtcw/main/uii386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xafa56778                   
Sys_LoadDll(ui) succeeded!                                        
Parsing menu file:ui/main.menu                                    
r_rmse of 0.000000 has saved 12kb                                 
Parsing menu file:ui/setup.menu                                   
Parsing menu file:ui/controls.menu                                
Parsing menu file:ui/cdkey.menu                                   
Parsing menu file:ui/system.menu                                  
Parsing menu file:ui/options.menu                                 
Parsing menu file:ui/credit.menu                                  
r_rmse of 0.000000 has saved 204kb                                
r_rmse of 0.000000 has saved 252kb                                
r_rmse of 0.000000 has saved 264kb                                
Parsing menu file:ui/connect.menu                                 
Parsing menu file:ui/quit.menu                                    
Parsing menu file:ui/vid_restart.menu                             
Parsing menu file:ui/snd_restart.menu                             
Parsing menu file:ui/rec_restart.menu                             
Parsing menu file:ui/default.menu                                 
Parsing menu file:ui/error.menu                                   
Parsing menu file:ui/serverinfo.menu                              
Parsing menu file:ui/quitcredit.menu                              
Parsing menu file:ui/resetscore.menu                              
Parsing menu file:ui/buy_pop.menu                                 
Parsing menu file:ui/multiplayer_pop.menu                         
Parsing menu file:ui/play.menu                                    
Parsing menu file:ui/load.menu                                    
Parsing menu file:ui/mods.menu                                    
Parsing menu file:ui/briefing.menu                                
UI menu load time = 293 milli seconds                             
Parsing menu file:ui/ingame.menu                                  
Parsing menu file:ui/ingame_controls.menu                         
Parsing menu file:ui/ingame_options.menu                          
Parsing menu file:ui/ingame_system.menu                           
Parsing menu file:ui/ingame_leave.menu                            
Parsing menu file:ui/ingame_player.menu                           
Parsing menu file:ui/ingame_load.menu                             
Parsing menu file:ui/ingame_save.menu                             
Parsing menu file:ui/in_vid_restart.menu                          
Parsing menu file:ui/in_snd_restart.menu                          
Parsing menu file:ui/in_rec_restart.menu                          
Parsing menu file:ui/notebook.menu                                
Parsing menu file:ui/clipboard.menu                               
Parsing menu file:ui/bookz.menu                                   
Parsing menu file:ui/bookv.menu                                   
Parsing menu file:ui/bookp.menu                                   
Parsing menu file:ui/pregame.menu                                 
Parsing menu file:ui/test.menu                                    
Parsing menu file:ui/ingame_help.menu                             
UI menu load time = 222 milli seconds                             
--- Common Initialization Complete ---                            
Opening IP socket: localhost:27960                                
Hostname: maximb-home                                             
IP: 127.0.1.1                                                     
Started tty console (use +set ttycon 0 to disable)                
sv_maxclients will be changed upon restarting.                    
------ Server Initialization ------                               
Server: cutscene1                                                 
RE_Shutdown( 0 )                                                  
Hunk_Clear: reset the hunk ok                                     
----- FS_Startup -----                                            
Current search path:                                              
/home/maximb/.wolf/main                                           
/home/maximb/maxddark/games/rtcw/main/sp_pak3.pk3 (14 files)      
/home/maximb/maxddark/games/rtcw/main/sp_pak2.pk3 (232 files)     
/home/maximb/maxddark/games/rtcw/main/sp_pak1.pk3 (1342 files)    
/home/maximb/maxddark/games/rtcw/main/pak0.pk3 (4775 files)       
/home/maximb/maxddark/games/rtcw/main                             

----------------------
12726 files in pk3 files
Sys_LoadDll(/home/maximb/maxddark/games/rtcw/main/qagamei386.so)... ok
Sys_LoadDll(qagame) found **vmMain** at  0xadc4032c                   
Sys_LoadDll(qagame) succeeded!                                        
Gametype changed, clearing session data.                              
------- BotLib Initialization -------                                 
------------ Map Loading ------------                                 
trying to load maps/cutscene1_b0.aas                                  
loaded maps/cutscene1_b0.aas                                          
trying to load maps/cutscene1_b1.aas                                  
loaded maps/cutscene1_b1.aas                                          
-------------------------------------                                 
AAS initialized.                                                      
AAS initialized.                                                      
-----------------------------------                                   
RE_Shutdown( 0 )                                                      
----- R_Init -----                                                    

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon HD 4800 Series 
GL_VERSION: 2.1.8543 Release           
GL_EXTENSIONS: GL_AMDX_vertex_shader_tessellator GL_AMD_performance_monitor GL_AMD_texture_texture4 GL_ARB_color_buffer_float GL_ARB_depth_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_instanced GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_framebuffer_object GL_ARB_framebuffer_sRGB GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_instanced_arrays GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shader_texture_lod GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_buffer_object GL_ARB_texture_compression GL_ARB_texture_compression_rgtc GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_abgr GL_EXT_bgra GL_EXT_bindable_uniform GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_buffers2 GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_framebuffer_sRGB GL_EXT_gpu_program_parameters GL_EXT_gpu_shader4 GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_float GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_array GL_EXT_texture_buffer_object GL_EXT_texture_compression_latc GL_EXT_texture_compression_rgtc GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_integer GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_EXT_texture_swizzle GL_EXT_transform_feedback GL_EXT_vertex_array GL_KTX_buffer_region GL_NV_blend_square GL_NV_conditional_render GL_NV_copy_depth_to_color GL_NV_texgen_reflection GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_WIN_swap_hint WGL_EXT_swap_control                                      
GL_MAX_TEXTURE_SIZE: 8192                                                                     
GL_MAX_ACTIVE_TEXTURES_ARB: 8                                                                 

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(8-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A                
GAMMA: hardware w/ 0 overbright bits                 
CPU:                                                 
rendering primitives: single glDrawElements          
texturemode: GL_LINEAR_MIPMAP_LINEAR                 
picmip: 0                                            
picmip2: 0                                           
texture bits: 32                                     
multitexture: enabled                                
compiled vertex arrays: enabled                      
texenv add: enabled                                  
compressed textures: disabled                        
ATI truform: disabled                                
NV distance fog: disabled                            
Initializing Shaders                                 
...loading 'scripts/ai.shader'                       
...loading 'scripts/alpha.shader'                    
...loading 'scripts/blacksmokeanim.shader'           
...loading 'scripts/blacksmokeanimb.shader'          
...loading 'scripts/characters.shader'               
...loading 'scripts/clipboard.shader'                
...loading 'scripts/common.shader'                   
...loading 'scripts/cursorhints.shader'              
...loading 'scripts/decals.shader'                   
...loading 'scripts/eerie.shader'                    
...loading 'scripts/expblue.shader'                  
...loading 'scripts/explode1.shader'                 
...loading 'scripts/fijets.shader'                   
...loading 'scripts/firest.shader'                   
...loading 'scripts/flamethrower.shader'             
...loading 'scripts/funnel.shader'                   
...loading 'scripts/gfx.shader'                      
...loading 'scripts/heat.shader'                     
...loading 'scripts/lights.shader'                   
...loading 'scripts/liquid.shader'                   
...loading 'scripts/maxx.shader'                     
...loading 'scripts/menu.shader'                     
...loading 'scripts/metal.shader'                    
...loading 'scripts/models.shader'                   
...loading 'scripts/netest.shader'                   
...loading 'scripts/oldwolf.shader'                  
...loading 'scripts/organics.shader'                 
...loading 'scripts/particle.shader'                 
...loading 'scripts/q3view.shader'                   
...loading 'scripts/sfx.shader'                      
...loading 'scripts/signs.shader'                    
...loading 'scripts/skin.shader'                     
...loading 'scripts/sky.shader'                      
...loading 'scripts/solo.shader'                     
...loading 'scripts/surfaces.shader'                 
...loading 'scripts/terrain.shader'                  
...loading 'scripts/test.shader'                     
...loading 'scripts/twiltb.shader'                   
...loading 'scripts/twiltb2.shader'                  
...loading 'scripts/ui.shader'                       
...loading 'scripts/ui_hud.shader'                   
...loading 'scripts/ui_notebook.shader'              
...loading 'scripts/ui_wolf.shader'                  
...loading 'scripts/viewflames.shader'               
...loading 'scripts/walls.shader'                    
...loading 'scripts/z_light.shader'                  
----- finished R_Init -----                          
Sys_LoadDll(/home/maximb/maxddark/games/rtcw/main/uii386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xafa56778                   
Sys_LoadDll(ui) succeeded!                                        
Parsing menu file:ui/main.menu                                    
r_rmse of 0.000000 has saved 276kb                                
Parsing menu file:ui/setup.menu                                   
Parsing menu file:ui/controls.menu                                
Parsing menu file:ui/cdkey.menu                                   
Parsing menu file:ui/system.menu                                  
Parsing menu file:ui/options.menu                                 
Parsing menu file:ui/credit.menu                                  
r_rmse of 0.000000 has saved 468kb                                
r_rmse of 0.000000 has saved 516kb                                
r_rmse of 0.000000 has saved 528kb                                
Parsing menu file:ui/connect.menu                                 
Parsing menu file:ui/quit.menu                                    
Parsing menu file:ui/vid_restart.menu                             
Parsing menu file:ui/snd_restart.menu                             
Parsing menu file:ui/rec_restart.menu                             
Parsing menu file:ui/default.menu                                 
Parsing menu file:ui/error.menu                                   
Parsing menu file:ui/serverinfo.menu                              
Parsing menu file:ui/quitcredit.menu                              
Parsing menu file:ui/resetscore.menu                              
Parsing menu file:ui/buy_pop.menu                                 
Parsing menu file:ui/multiplayer_pop.menu                         
Parsing menu file:ui/play.menu                                    
Parsing menu file:ui/load.menu                                    
Parsing menu file:ui/mods.menu                                    
Parsing menu file:ui/briefing.menu                                
UI menu load time = 255 milli seconds                             
Parsing menu file:ui/ingame.menu                                  
Parsing menu file:ui/ingame_controls.menu                         
Parsing menu file:ui/ingame_options.menu                          
Parsing menu file:ui/ingame_system.menu                           
Parsing menu file:ui/ingame_leave.menu                            
Parsing menu file:ui/ingame_player.menu                           
Parsing menu file:ui/ingame_load.menu                             
Parsing menu file:ui/ingame_save.menu                             
Parsing menu file:ui/in_vid_restart.menu                          
Parsing menu file:ui/in_snd_restart.menu                          
Parsing menu file:ui/in_rec_restart.menu                          
Parsing menu file:ui/notebook.menu                                
Parsing menu file:ui/clipboard.menu                               
Parsing menu file:ui/bookz.menu                                   
Parsing menu file:ui/bookv.menu                                   
Parsing menu file:ui/bookp.menu                                   
Parsing menu file:ui/pregame.menu                                 
Parsing menu file:ui/test.menu                                    
Parsing menu file:ui/ingame_help.menu                             
UI menu load time = 222 milli seconds                             
Sys_LoadDll(/home/maximb/maxddark/games/rtcw/main/cgamei386.so)... ok
Sys_LoadDll(cgame) found **vmMain** at  0xad1af264                   
Sys_LoadDll(cgame) succeeded!                                        
LOADING... collision map                                             
LOADING... sounds                                                    

.........................
Initializing Sound Scripts
...loading 'sound/scripts/cutscene1.sounds'
...loading 'sound/scripts/cutscene6.sounds'
...loading 'sound/scripts/cutscene9.sounds'
...loading 'sound/scripts/cutscene11.sounds'
...loading 'sound/scripts/cutscene14.sounds'
...loading 'sound/scripts/cutscene19.sounds'
...loading 'sound/scripts/escape1.sounds'   
...loading 'sound/scripts/escape2.sounds'   
...loading 'sound/scripts/tram.sounds'      
...loading 'sound/scripts/village1.sounds'  
...loading 'sound/scripts/crypt1.sounds'    
...loading 'sound/scripts/crypt2.sounds'    
...loading 'sound/scripts/church.sounds'    
...loading 'sound/scripts/boss1.sounds'     
...loading 'sound/scripts/forest.sounds'    
...loading 'sound/scripts/rocket.sounds'    
...loading 'sound/scripts/assault.sounds'   
...loading 'sound/scripts/sfm.sounds'       
...loading 'sound/scripts/factory.sounds'   
...loading 'sound/scripts/trainyard.sounds' 
...loading 'sound/scripts/swf.sounds'       
...loading 'sound/scripts/norway.sounds'    
...loading 'sound/scripts/xlabs.sounds'     
...loading 'sound/scripts/boss2.sounds'     
...loading 'sound/scripts/dam.sounds'       
...loading 'sound/scripts/village2.sounds'  
...loading 'sound/scripts/chateau.sounds'   
...loading 'sound/scripts/dark.sounds'      
...loading 'sound/scripts/castle.sounds'    
...loading 'sound/scripts/end.sounds'       
...loading 'sound/scripts/ai.sounds'        
...loading 'sound/scripts/general.sounds'
...loading 'sound/scripts/combat.sounds'
...loading 'sound/scripts/movers.sounds'
done.
LOADING... graphics
LOADING... maps/cutscene1.bsp
stitched 0 LoD cracks
...loaded 2413 faces, 25 meshes, 147 trisurfs, 17 flares
LOADING... game media
LOADING...  - textures
r_rmse of 0.000000 has saved 720kb
r_rmse of 0.000000 has saved 768kb
r_rmse of 0.000000 has saved 780kb
LOADING...  - models
r_rmse of 0.000000 has saved 828kb
r_rmse of 0.000000 has saved 840kb
LOADING...  - weapons
LOADING...  - items
LOADING...  - inline models
LOADING...  - server models
LOADING...  - particles
r_rmse of 0.000000 has saved 852kb
LOADING...  - game media done
LOADING... flamechunks
LOADING... clients
LOADING... WolfPlayer
UI menu load time = 2 milli seconds
Received signal 11, exiting...
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 134
  Minor opcode of failed request: 10
  Serial number of failed request: 90
Shutdown tty console

```

I think something is really wrong with my Ubuntu installation as weird stuff happen with some games.

From this log - what do you think is the problem and how do I fix it ?

---

### Post by calis1981 on 2010-02-25
ive got the same problem
havnt been able to get it working propaly
i get the the main menu, click new game, chose difficlty it starts to load then

"Received signal 11, exiting...
Shutdown tty console"

thats as far as i get in wolfmp or sp
??
running 9.04 on a msi-wind100clone
got intel driver 2.10 installed and running fine and useing mesa 7.6
?

---

### Post by calis1981 on 2010-02-28
i worked out the problem!!!
if its the original disc and not GOTY heres what to do
install in in wine
download the 1.33 update and install that with wine
then install the 1.41 update in wine
then start doing the native install, once the install has finish copy the pak file (pak0.pk3, sp_pak1.pk3, mp_pak0.pk3)
it seems those three files get something done to them in the windows patch, and if u dont do that u cant play the game, as i said this work with the CLASSIC install (1.0) i dont know about GOTY edition
i havnt played the game all the way through, but the first level worked flawlessly

---

