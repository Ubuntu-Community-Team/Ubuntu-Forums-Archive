---
title: "Polynomial crashes on start"
date: 2011-03-21
forum: Gaming &amp; Leisure
---

### Post by Ligerzero_942 on 2011-03-21
I just downloaded the linux demo for the game Polynomial but when I start to run it the window opens and then closes a few seconds later.
Here's the terminal output:
```
(1777:Register) Reg 'GameObject' = 1
(1777:Register) Reg 'RotatableObject' = 2
(1777:Register) Reg 'SoundObject' = 3
(1777:Register) Reg 'FireworkFragment' = 4
(1777:Register) Reg 'Player' = 5
(1777:Register) Reg 'Chaser' = 6
(1777:Register) Reg 'BonusPod' = 7
(1777:Register) Reg 'SimpleBonusPod' = 8
(1777:Register) Reg 'BouncyBall' = 9
(1777:Register) Reg 'AcceleratorSegment' = 10
(1777:Register) Reg 'Flower' = 11
StyleManager::StyleManager
StyleManager::StyleManager
(1777:Register) Reg 'ChristmasTree' = 12
(1777:Register) Reg 'TextBillboard' = 13
(1777:Register) Reg 'MusicWaveSource' = 14
(1777:Register) Reg 'Meteorites' = 15
(1777:Register) Reg 'LevelPortalExit' = 16
(1777:Register) Reg 'LevelPortal2' = 17
(1777:Register) Reg 'LevelPortal' = 18
(1777:Register) Reg 'Fighter' = 19
(1777:Register) Reg 'Chewer' = 20
(1858:PropagateInheritance) [Narcissus] PropagateInheritance()
(1850:InheritTo) GameObject-->RotatableObject
(1850:InheritTo) RotatableObject-->AcceleratorSegment
(1850:InheritTo) GameObject-->BonusPod
(1850:InheritTo) RotatableObject-->BouncyBall
(1850:InheritTo) RotatableObject-->Chaser
(1850:InheritTo) Chaser-->Chewer
(1850:InheritTo) RotatableObject-->ChristmasTree
(1850:InheritTo) Chaser-->Fighter
(1850:InheritTo) GameObject-->FireworkFragment
(1850:InheritTo) RotatableObject-->Flower
(1850:InheritTo) RotatableObject-->LevelPortal
(1850:InheritTo) LevelPortal-->LevelPortal2
(1850:InheritTo) RotatableObject-->LevelPortalExit
(1850:InheritTo) GameObject-->Meteorites
(1850:InheritTo) RotatableObject-->MusicWaveSource
(1850:InheritTo) GameObject-->Player
(1850:InheritTo) BonusPod-->SimpleBonusPod
(1850:InheritTo) GameObject-->SoundObject
(1850:InheritTo) RotatableObject-->TextBillboard
(1862:PropagateInheritance) [Narcissus] PropagateInheritance() done
(2727:main) command line: ./Polynomial32 
app_name=./Polynomial32
initial_cwd=/home/ethan/Polynomial-free-100_linux/bin
app_path=.
app_name=./Polynomial32
app_path=.
(2886:main) code=uberwoot
(62:LoadList) Files:
(67:LoadList) 000_Twisted_way.txt
(67:LoadList) 017_Arch.txt
(67:LoadList) 020_Coiled.txt
(67:LoadList) 011_Convergence.txt
(67:LoadList) 031_Rossler's_galaxy.txt
(67:LoadList) 005_Starfall_2.txt
(67:LoadList) 027_V.txt
(67:LoadList) 030_Trap_Flower.txt
(67:LoadList) 021_Lorenz_World.txt
(67:LoadList) 001_Vortex.txt
(67:LoadList) 008_Hyperchaos.txt
(2897:main) 1 CWD: /home/ethan/Polynomial-free-100_linux/bin
(2900:main) using 32bit libraries.
(2902:main) sizeof(wchar_t)=4
(71:SubdivideFaces) Vertices: 42
(72:SubdivideFaces) Faces: 80
(73:SubdivideFaces) Edges: 120
(71:SubdivideFaces) Vertices: 162
(72:SubdivideFaces) Faces: 320
(73:SubdivideFaces) Edges: 480
(71:SubdivideFaces) Vertices: 642
(72:SubdivideFaces) Faces: 1280
(73:SubdivideFaces) Edges: 1920
(71:SubdivideFaces) Vertices: 2562
(72:SubdivideFaces) Faces: 5120
(73:SubdivideFaces) Edges: 7680
(2919:main) Globe vertices: 2562
(2923:main) making context 
(2927:main) Binding options 
(238:LoadOptions) Using default config
(245:LoadOptions) Will store config in /home/ethan/.polynomial/config.101.txt upon exit
(2964:main) calling init 
(315:OnLaunch) Using desktop resolution, which is 1024x600
(334:OnLaunch) unconfirmed mode: false
(343:OnLaunch) OnLaunch end
(267:LogOptions) Settings: fs=0 custom=0 1024x600
(268:LogOptions) Rollback settings: fs=0 custom=0 1024x600
(270:LogOptions) actual: fs=0 1000x520
(2970:main) initializing audio
(1307:AudioManager) AudioManager::AudioManager()
(1335:AudioManager) OpenAL: version 1.1 ALSOFT 1.12.854 renderer OpenAL Soft vendor OpenAL Community
(1359:AudioManager) creating reverb
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
(1471:GetCaptureDevicesList) OpenAL capture devices : { 
(1480:GetCaptureDevicesList)  PulseAudio Capture
(1480:GetCaptureDevicesList)  ALSA Capture on default
(1480:GetCaptureDevicesList)  ALSA Capture on HDA Intel [ALC269 Analog] (hw:0,0)
(1480:GetCaptureDevicesList)  OSS Capture
(1480:GetCaptureDevicesList)  PortAudio Capture
(1484:GetCaptureDevicesList) }
(1486:GetCaptureDevicesList) OpenAL default capture device: PulseAudio Capture
(2976:main) audio initialized
(3005:main) initializing opengl extensions
(3020:main) Vendor: Tungsten Graphics, Inc
(3021:main) Renderer: Mesa DRI Intel(R) IGD GEM 20091221 2009Q4 x86/MMX/SSE2
(3022:main) Version: 1.4 Mesa 7.7.1
(3023:main) Extensions: 
GL_EXT_compiled_vertex_array GL_EXT_texture_env_add GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_draw_elements_base_vertex GL_ARB_fragment_program GL_ARB_half_float_pixel GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_provoking_vertex GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shading_language_120 GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_cull_vertex GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_blit GL_EXT_framebuffer_object GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
(3024:main) end of opengl info.
glClampColorARB not available
(3043:main) opengl extensions initialized
(3047:main) 2 CWD: /home/ethan/Polynomial-free-100_linux/bin
(3058:main) initializing seeds 
glGenBuffers: success
(101:World) World::World
(269:ShowCursor) ShowCursor()
(3070:main) seeds initialized, creating user interface
StyleManager::StyleManager
GLMTexture::LoadFromFile($$data/weird_border.png)
Loading truetype font ./data/DejaVuSans.ttf
creating texture
Unicode cache slots: 49
GLMTexture::LoadFromFile($$data/blob_16.png)
Loading truetype font ./data/DejaVuSans.ttf
creating texture
Unicode cache slots: 102
GLMTexture::LoadFromFile($$data/left_arrow.png)
GLMTexture::LoadFromFile($$data/left_arrow_1.png)
GLMTexture::LoadFromFile($$data/left_arrow_2.png)
GLMTexture::LoadFromFile($$data/button_border_circle8.png)
GLMTexture::LoadFromFile($$data/right_arrow.png)
GLMTexture::LoadFromFile($$data/right_arrow_1.png)
GLMTexture::LoadFromFile($$data/right_arrow_2.png)
Loading truetype font ./data/DejaVuSans.ttf
creating texture
Unicode cache slots: 80
GLMTexture::LoadFromFile($$data/slider_bg_line.png)
GLMTexture::LoadFromFile($$data/slider_button.png)
GLMTexture::LoadFromFile($$data/popup_box_2.png)
(458:LoadM3U) M3U entry ../music/000_drones-full-thunder.ogg
(461:LoadM3U) rel, abs=$$data/music_playlists/../music/000_drones-full-thunder.ogg
(458:LoadM3U) M3U entry ../music/005_ton_of_reverb.ogg
(461:LoadM3U) rel, abs=$$data/music_playlists/../music/005_ton_of_reverb.ogg
(458:LoadM3U) M3U entry ../music/010_Rocks_vs_eggs_3-hardy_2.ogg
(461:LoadM3U) rel, abs=$$data/music_playlists/../music/010_Rocks_vs_eggs_3-hardy_2.ogg
(458:LoadM3U) M3U entry ../music/0005_jingle.ogg
(461:LoadM3U) rel, abs=$$data/music_playlists/../music/0005_jingle.ogg
(458:LoadM3U) M3U entry ../music/030_five.ogg
(461:LoadM3U) rel, abs=$$data/music_playlists/../music/030_five.ogg
(458:LoadM3U) M3U entry ../music/040_all_good.ogg
(461:LoadM3U) rel, abs=$$data/music_playlists/../music/040_all_good.ogg
(458:LoadM3U) M3U entry ../music/045_dn6-4-eqs-clear_beat.ogg
(461:LoadM3U) rel, abs=$$data/music_playlists/../music/045_dn6-4-eqs-clear_beat.ogg
(458:LoadM3U) M3U entry ../music/050_mony-pony2.ogg
(461:LoadM3U) rel, abs=$$data/music_playlists/../music/050_mony-pony2.ogg
(458:LoadM3U) M3U entry ../music/060_verbo.ogg
(461:LoadM3U) rel, abs=$$data/music_playlists/../music/060_verbo.ogg
(458:LoadM3U) M3U entry ../music/090_live_piano_15_20.ogg
(461:LoadM3U) rel, abs=$$data/music_playlists/../music/090_live_piano_15_20.ogg
(458:LoadM3U) M3U entry ../music/100_live_32_38.ogg
(461:LoadM3U) rel, abs=$$data/music_playlists/../music/100_live_32_38.ogg
GLMTexture::LoadFromFile($$data/playlist_current.png)
GLMTexture::LoadFromFile($$data/playlist_delete_button.png)
bound scrollbar_size_in
GLMTexture::LoadFromFile($$data/slider_bg_line_vert.png)
bound scrollbar_size_in
bound scrollbar_size_in
bound scrollbar_size_in
Loading truetype font ./data/DejaVuSans.ttf
creating texture
Unicode cache slots: 84
bound scrollbar_size_in
bound scrollbar_size_in
Loading truetype font ./data/DejaVuSans.ttf
creating texture
Unicode cache slots: 45
GLMTexture::LoadFromFile($$data/uparrow8x8_0.png)
GLMTexture::LoadFromFile($$data/downarrow8x8_0.png)
Loading truetype font ./data/DejaVuSans.ttf
creating texture
Unicode cache slots: 88
(793:UpdateParamsView) 
(951:OnMusicVisualizerChanged) OnLevelChanged(3)
(62:LoadList) Files:
(67:LoadList) 003_Waves.lua
(67:LoadList) 004_Super_Waves.lua
(67:LoadList) 000_None.lua
(67:LoadList) 001_Laser_Show_1.lua
(67:LoadList) 002_Laser_Show_2.lua
(793:UpdateParamsView) 
(3072:main) user interface created, entering event loop 
VFS translate './data/init.lua' unchanged
(584:OpenFile) OGGDataStream::OpenFile ./data/music_playlists/../music/000_drones-full-thunder.ogg
(589:OpenFile) ov_open_callbacks
(598:OpenFile) ov_info
(600:OpenFile) ov_comment
(612:OpenFile) OGGDataStream::OpenFile success ./data/music_playlists/../music/000_drones-full-thunder.ogg
(326:CallGlobal) Error 2 running lua function 'on_audio_frame' : attempt to call a nil value
(3725:Update) last ShapeMaker::Update()
(41:TextureFramebuffer) TextureFramebuffer::TextureFramebuffer
glGenTextures: success
glBindTexture: success
glTexImage2D: success
glTexParameteri: success
creating half-float texture: success
glGenFramebuffersEXT: success
glBindFramebufferEXT: success
glGenRenderbuffersEXT: success
glBindRenderbufferEXT: success
glRenderbufferStorageEXT: success
glFramebufferRenderbufferEXT: success
glFramebufferTexture2DEXT: success
glCheckFramebufferStatusEXT: success
creating framebuffer: success
(110:EnterLevel) entering level ./data/levels//000_Twisted_way.txt
StyleManager::StyleManager
(150:LoadLevel) World::LoadLevel
VFS translate './data/init.lua' unchanged
running 000_script.lua 
main.lua loaded!
(41:TextureFramebuffer) TextureFramebuffer::TextureFramebuffer
glGenTextures: success
glBindTexture: success
glTexImage2D: success
glTexParameteri: success
creating half-float texture: success
glGenFramebuffersEXT: success
glBindFramebufferEXT: success
glFramebufferTexture2DEXT: success
glCheckFramebufferStatusEXT: success
creating framebuffer: success
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={-30,22,-70},type="TextBillboard",color={0.25,0.35,1},text="* GAMEPLAY: YOUR GOAL IS TO TOP THE SCORES, BY USING THE ITEMS BELOW.\n* WHEN YOU'RE DONE LOOKING AROUND, PRESS ESC AND SET DIFFICULTY TO INSANE, YOU'LL\n   NEVER BE ABLE TO GET VERY BIG SCORE ON EASY, BECAUSE ON EASY YOU DONT GET ENOUGH ENEMIES.\n* THE \"PER PAST 5 MINUTES\" PHRASE ACTUALLY HAS SOME MEANING.\n* WATCH HOW SCORE CHANGES, FIND A WAY TO EXPLOIT SCORING FUNCTION. GOOD LUCK!",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-43.29166313972,-35.61789432132,-74.716723560904}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={-15,17,-70},type="TextBillboard",color={0.3,0.4,0.5},text="Nom-Noms, nazi robots whom eats ghosts and try to shot you. ",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-48.6374987625,-39.77959539862,-60.430280327144}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={33,17,-70},type="TextBillboard",color={3,0.4,0.1},text="Kill them.",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-75.937139402436,-42.51273177622,-21.044227010024}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={-15,12,-70},type="TextBillboard",color={0.3,0.4,0.5},text="Ghosts - friends whom repair you and give you speed boost. ",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-45.4521966853,-43.08719135792,-58.451978754984}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={32.2,12,-70},type="TextBillboard",color={0.4,1,0.1},text="Fly through.",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-72.29684331457,-45.77477546256,-19.722359659816}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={0,7,-70},type="TextBillboard",color={0.3,0.4,0.5},text="Flowers - friends you can hide in. ",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-50.79803230808,-47.24889243522,-44.165535521224}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={28,7,-70},type="TextBillboard",color={0.4,1,0.1},text="Fly through.",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-66.722822681376,-48.84322198882,-21.190337752904}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={-25,2,-70},type="TextBillboard",color={3,0.4,0.1},text="<-- Fly through this wormhole when you want to go to the next arena!",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-33.39416739758,-49.13297986452,-62.700803385064}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={-25,-3,-70},type="TextBillboard",color={0.3,0.4,0.5},text="Wormhole to next animator. Fly through.",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-30.20886532038,-52.44057582382,-60.722501812904}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={-15,-8,-70},type="TextBillboard",color={0.3,0.4,0.5},text="Rings that deflect bullets weirdly.",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-32.7109883765,-56.31757519512,-50.538772466344}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={-25.8,-13,-70},type="TextBillboard",color={0.3,0.4,0.5},text="Fast bullets.",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-23.383267155314,-59.01021546946,-57.422332890536}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={-9.6,-13,-70},type="TextBillboard",color={0.3,0.4,0.5},text="Autoaim.",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-32.596895871293,-59.9326489969,-44.129539896008}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={2.6,-13,-70},type="TextBillboard",color={0.3,0.4,0.5},text="Speed boost. ",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-39.535554533943,-60.62732115954,-34.11891801124}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={13,-13,-70},type="TextBillboard",color={0.4,1,0.1},text="Collect.",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-45.450476672596,-61.21950070802,-25.585273125864}}
NewBillboard called
NewBillboard calculations done
NewBillboard table created
NewBillboard table updated
about to call NewGameObject with following params{offset={-30,-18,-70},type="TextBillboard",color={0.3,0.4,0.5},text="Near the attractor, your ship flies 2x faster.\nWith speed boost, it flies 3x faster. With both, 6x",fadetime=1,align={0,0.5},align_to_view=false,orientation={-0.412392,-0.213452,0.81283,-0.35168},scale=0.1,lifetime=1000,pos={-17.80924652212,-62.07866199572,-58.890310983624}}
glGenBuffers: success
(71:SubdivideFaces) Vertices: 42
(72:SubdivideFaces) Faces: 80
(73:SubdivideFaces) Edges: 120
(71:SubdivideFaces) Vertices: 162
(72:SubdivideFaces) Faces: 320
(73:SubdivideFaces) Edges: 480
(71:SubdivideFaces) Vertices: 642
(72:SubdivideFaces) Faces: 1280
(73:SubdivideFaces) Edges: 1920
(71:SubdivideFaces) Vertices: 2562
(72:SubdivideFaces) Faces: 5120
(73:SubdivideFaces) Edges: 7680
(71:SubdivideFaces) Vertices: 10242
(72:SubdivideFaces) Faces: 20480
(73:SubdivideFaces) Edges: 30720
glBindBuffer: success
glBufferData: success
(938:OnLevelChanged) OnLevelChanged(0)
(793:UpdateParamsView) 
GLMTexture::LoadFromFile($$data/nebulabrot_composite_final_8.png)
Shader '$$data/background_v.glsl' compiled successfully
Shader '$$data/background_f.glsl' compiled successfully
glCreateProgram failed. Wow.
Shader '$$data/music_visualizer_waves_1_v.glsl' compiled successfully
Shader '$$data/test_f.glsl' compiled successfully
glCreateProgram failed. Wow.
./Polynomial32[0x80e71e8]
[0x7c0400]
/usr/lib/dri/i915_dri.so(_tnl_draw_prims+0x648)[0x6709dd8]
/usr/lib/dri/i915_dri.so(_tnl_vbo_draw_prims+0x79)[0x670a869]
/usr/lib/dri/i915_dri.so(+0x112f31)[0x6701f31]
/usr/lib/dri/i915_dri.so(+0x109c17)[0x66f8c17]
./Polynomial32[0x818a6d9]
./Polynomial32[0x8193631]
./Polynomial32[0x8195211]
./Polynomial32[0x80a6ad8]
./Polynomial32[0x80a4ad6]
./Polynomial32[0x80a61b2]
./Polynomial32[0x80a2fec]
./Polynomial32[0x81f974e]
./Polynomial32[0x81ede41]
./Polynomial32[0x81e7318]
./Polynomial32[0x81eb77e]
./Polynomial32[0x81ebf0a]
./Polynomial32[0x81e73b0]
./Polynomial32[0x80ebc4b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x35d2bd6]
./Polynomial32[0x80523e1]
Backtrace:
./Polynomial32() [0x80e71e8]
[0x7c0400]
/usr/lib/dri/i915_dri.so(_tnl_draw_prims+0x648) [0x6709dd8]
/usr/lib/dri/i915_dri.so(_tnl_vbo_draw_prims+0x79) [0x670a869]
/usr/lib/dri/i915_dri.so(+0x112f31) [0x6701f31]
/usr/lib/dri/i915_dri.so(+0x109c17) [0x66f8c17]
./Polynomial32() [0x818a6d9]
./Polynomial32() [0x8193631]
./Polynomial32() [0x8195211]
./Polynomial32() [0x80a6ad8]
./Polynomial32() [0x80a4ad6]
./Polynomial32() [0x80a61b2]
./Polynomial32() [0x80a2fec]
./Polynomial32() [0x81f974e]
./Polynomial32() [0x81ede41]
./Polynomial32() [0x81e7318]
./Polynomial32() [0x81eb77e]
./Polynomial32() [0x81ebf0a]
./Polynomial32() [0x81e73b0]
./Polynomial32() [0x80ebc4b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x35d2bd6]
./Polynomial32() [0x80523e1]
Killed
ethan@LigerBOX:~/Polynomial-free-100_linux/bin$ 

```

I'm using Ubuntu 10.04 on an Asus EeePC.

---

### Post by Perfect Storm on 2011-03-22
From the homepage:
> System requirements: GeForce 8 series or later, Radeon HD 2000 series or later, with at least 256MB of video memory. Intel's integrated graphics (GMA and the like) mostly does not work due to it's slow speed at anything other than textured triangles.


You need something better than your intel onboard card to run this game.

---

### Post by Ligerzero_942 on 2011-03-23
Darn, thought the game would be small enough to work on the netbook. Thanks anyway.

---

