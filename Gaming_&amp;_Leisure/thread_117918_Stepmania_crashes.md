---
title: "Stepmania crashes"
date: 2006-01-15
forum: Gaming &amp; Leisure
---

### Post by wr0x2 on 2006-01-15
I have Stepmania 3.9 here under breezy (precompiled executable) and whenever I try to play a song with background animation, stepmania crashes.

Also, SMO gives an error about not finding lualib.so when I try to start it. I've installed all of the lua50 libs and stuff from apt, so I'm not sure what the problem is here.

---

### Post by Perfect Storm on 2006-01-17
Can you post the terminal output?

---

### Post by anacron on 2006-01-17
I have exactly the same problem, all other stuff works well, no complaining about that.

here's the crashinfo that stepmania makes:
```
StepMania 3.9 crash report
--------------------------------------

Crash reason: Segmentation fault - address not mapped at 0x000000e4
Crashed thread: Main thread

Checkpoints:
Thread: Main thread
        ../../src/IniFile.cpp:10 Reading 'Themes/default/BGAnimations/_black/BGAnimation.ini'
        ../../src/IniFile.cpp:10 Reading 'Themes/default/BGAnimations/ScreenGameplay song finished/BGAnimation.ini'
        ../../src/IniFile.cpp:10 Reading 'Themes/default/BGAnimations/ScreenGameplay song finished/BGAnimation.ini'
        ../../src/RageTextureManager.cpp:108 RageTextureManager::LoadTexture(Songs/DDR Video Games 4th Mix/GGXXMay/GGXXMayBG.png).
        ../../src/RageTextureManager.cpp:108 RageTextureManager::LoadTexture(Songs/DDR Video Games 4th Mix/GGXXMay/GuiltyGearX.avi).
Thread: Decode thread
        ../../src/arch/Sound/RageSoundDriver_Generic_Software.cpp:198 
        ../../src/arch/Sound/RageSoundDriver_Generic_Software.cpp:198 
        ../../src/arch/Sound/RageSoundDriver_Generic_Software.cpp:198 
        ../../src/arch/Sound/RageSoundDriver_Generic_Software.cpp:198 
        ../../src/arch/Sound/RageSoundDriver_Generic_Software.cpp:198 
Thread: RageSound_ALSA9_Software
Thread: MusicThread
        ../../src/GameSoundManager.cpp:89 
        ../../src/GameSoundManager.cpp:93 
        ../../src/GameSoundManager.cpp:87 
        ../../src/GameSoundManager.cpp:89 
        ../../src/GameSoundManager.cpp:93 

Thread: Main thread
08379424: 
08377f04: MovieTexture_FFMpeg::CreateDecoder() 
0837774a: MovieTexture_FFMpeg::MovieTexture_FFMpeg(RageTextureID) 
08375ed9: MakeRageMovieTexture(RageTextureID) 
0849497b: RageTextureManager::LoadTextureInternal(RageTextureID) 
08494a8d: RageTextureManager::LoadTexture(RageTextureID) 
084bfc69: Sprite::LoadFromTexture(RageTextureID) 
b7c19e6b: (libz.so.1)
082cc144: RageTextureID::RageTextureID(RageTextureID const&) 
084be881: Sprite::SongBGTexture(RageTextureID) 
b7c19de1: (libz.so.1)
b7c19e6b: (libz.so.1)
0838b909: BGAnimation::LoadFromMovie(CStdStr<char>) 
083f839c: Background::CreateSongBGA(CStdStr<char>) const 
083fa1dd: Background::LoadFromSong(Song const*) 
081df9a7: ScreenGameplay::LoadNextSong() 
081d8c27: ScreenGameplay::Init() 
081d17b9: ScreenGameplay::ScreenGameplay(CStdStr<char>, bool) 
0815da6f: Screen::Create(CStdStr<char>) 
08519dc0: ScreenManager::MakeNewScreen(CStdStr<char>) 
08519e74: ScreenManager::PrepNewScreen(CStdStr<char>) 
082aac75: ScreenStage::HandleScreenMessage(ScreenMessage) 
08321d1c: PlayerOptions::Approach(PlayerOptions const&, float) 
08519bda: ScreenManager::Update(float) 
0836749c: 
08365a42: main 
b7a52ea2: (libc.so.6)
0815c351: 

Static log:
StepMania 3.9
Log starting 2006-01-17 14:09:50
Loading window: gtk
OS: Linux ver 020614
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.3.5
Threads library: NPTL 2.3.5
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.10rc1 (Mon Sep 12 08:13:09 2005 UTC).
ALSA Driver: 0: NVidia CK804 [CK804], device 0: Intel ICH [NVidia CK804], 1/1 subdevices avail
ALSA Driver: 0: NVidia CK804 [CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958], 1/1 subdevices avail
Couldn't load driver ALSA: Not enough substreams for hardware mixing, using software mixing
ALSA: Software mixing at 48000hz
Sound driver: ALSA-sw
Video renderers: 'opengl'
SDL version: 1.2.8
Got 32 bpp (8880), 24 depth, 0 stencil
Paletted textures disabled: GL_EXT_paletted_texture missing.
OGL Vendor: NVIDIA Corporation
OGL Renderer: GeForce 6600 GT/PCI/SSE2/3DNOW!
OGL Version: 2.0.1 NVIDIA 81.74
OGL Extensions: GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
OGL Max texture size: 4096
GLU Version: 1.3
Display: :0.0 (screen 0)
Direct rendering: yes
X server vendor: The X.Org Foundation [6.8.2.0]
Server GLX vendor: NVIDIA Corporation [1.3]
Client GLX vendor: NVIDIA Corporation [1.3]
Fullscreen 1280x1024 16 color 16 texture 60Hz Vsync AA
Found 1 joysticks
   0: 'WiseGroup.,Ltd MP-8866 Dual USB Joypad' axes: 6, hats: 0, buttons: 12
WARNING: The graphic 'Themes/Trance Machina - Zen Rebirth/Graphics/MenuElements icon single 2x1.png' has frame dimensions that aren't even numbers.
WARNING: 
WARNING: The entire image is 82x20 and frame size is 41.0x20.0.
WARNING: 
WARNING: Image quality will be much improved if you resize the graphic to 84x20, which is a frame size of 42x20.
WARNING: The graphic 'Themes/Trance Machina - Zen Rebirth/Graphics/ZR-Music/Element-GrooveRadar Labels 1x5.png' has frame dimensions that aren't even numbers.
WARNING: 
WARNING: The entire image is 86x126 and frame size is 86.0x25.2.
WARNING: 
WARNING: Image quality will be much improved if you resize the graphic to 86x130, which is a frame size of 86x26.
WARNING: The graphic 'Themes/Trance Machina - Zen Rebirth/Graphics/ZR-Music/Element-Difficulty Frame p1.png' has frame dimensions that aren't even numbers.
WARNING: 
WARNING: The entire image is 77x40 and frame size is 77.0x40.0.
WARNING: 
WARNING: Image quality will be much improved if you resize the graphic to 78x40, which is a frame size of 78x40.
WARNING: The graphic 'Themes/Trance Machina - Zen Rebirth/Graphics/DifficultyMeter bar 2x1.png' has frame dimensions that aren't even numbers.
WARNING: 
WARNING: The entire image is 22x8 and frame size is 11.0x8.0.
WARNING: 
WARNING: Image quality will be much improved if you resize the graphic to 24x8, which is a frame size of 12x8.
WARNING: The graphic 'Songs/DDR Video Games 4th Mix/GGXXMay/GGXXMayBG.png' has frame dimensions that aren't even numbers.
WARNING: 
WARNING: The entire image is 444x333 and frame size is 444.0x333.0.
WARNING: 
WARNING: Image quality will be much improved if you resize the graphic to 444x334, which is a frame size of 444x334.
WARNING: RageBitmapTexture: Couldn't load : No such file or directory
WARNING: The graphic 'Themes/Trance Machina - Zen Rebirth/Graphics/HoldJudgment 1x2.png' has frame dimensions that aren't even numbers.
WARNING: 
WARNING: The entire image is 60x27 and frame size is 60.0x13.5.
WARNING: 
WARNING: Image quality will be much improved if you resize the graphic to 60x28, which is a frame size of 60x14.
Players joined: P1
Language: english
Current renderer: OpenGL
Theme: Trance Machina - Zen Rebirth

Partial log:
00:55.115: Sprite::LoadFromTexture( Themes/Trance Machina - Zen Rebirth/Graphics/ZR-Transitions/Element-Topbar.png )
00:55.116: Sprite::LoadFromTexture( Themes/Trance Machina - Zen Rebirth/Graphics/ZR-Transitions/Element-Bottombar.png )
00:55.117: Sprite::LoadFromTexture( Themes/Trance Machina - Zen Rebirth/Graphics/ZR-Transitions/Element-Rock.png )
00:55.125: Sprite::LoadFromTexture( Themes/default/BGAnimations/_black.png )
00:55.128: RageSound::LoadSound( 'Songs/DDR Video Games 4th Mix/GGXXMay/GGXXMay.mp3' )
00:55.137: Sprite::LoadFromTexture( Songs/DDR Video Games 4th Mix/GGXXMay/GGXXMayBG.png )
00:55.137: Sprite::LoadFromTexture( Songs/DDR Video Games 4th Mix/GGXXMay/GuiltyGearX.avi )
00:55.149: Movie Songs/DDR Video Games 4th Mix/GGXXMay/GuiltyGearX.avi has handler 'DX50', type 'divx'
00:55.149: Initializing driver: FFMpeg
00:55.149: MovieTexture_FFMpeg::MovieTexture_FFMpeg(Songs/DDR Video Games 4th Mix/GGXXMay/GuiltyGearX.avi)

-- End of report

```

there seems to be some problems with my theme too but i'll just ignore that, changing theme doesn't help anyways.

---

### Post by wr0x2 on 2006-01-26
Well, if anyone finds a solution to the video thing that's great, but it's not that important. What I'm really interested in is getting Stepmania online to work.

I haven fixed the library issues with it. Again, everything seems to be installed, but SM doesn't recognize it. If you have any idea, please post.

---

### Post by anacron on 2006-01-28
amm last time I did try stepmania online it worked just fine, only thing that didn't work, was the fullscreen mode. Songs which had videos worked perfectly though the video didin't come out, you could still play the songs...

---

### Post by wr0x2 on 2006-01-28
EDIT: Got smo working by spending an extra five minutes on google. If anyone knows a solution to the video issue, please post it.

---

