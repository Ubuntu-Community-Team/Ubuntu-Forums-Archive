---
title: "Getting Stepmania to work"
date: 2006-06-07
forum: Gaming &amp; Leisure
---

### Post by hypersoar on 2006-06-07
I'm attempting to run Stepmania (DDR clone) on my newley installed Ubuntu machine. I followed teh directions of [this]("http://www.ubuntuforums.org/showthread.php?t=69144") how-to, but it still doesn't seem to work. The splash screen will show up, but when I try to move past that, it goes back to my desktop at a lower resolution (showing just the upper-left corner). 

My video card is a Radeon 9550. Here's my log:

```
00:00.280: StepMania 3.9 rc2a

00:00.280: Log starting 2006-06-07 01:12:15

00:00.281:  

00:00.281: Reading 'Data/Defaults.ini' failed: No such file or directory

00:00.283: Reading 'Data/Static.ini' failed: No such file or directory

00:00.640: Loading window: gtk

00:00.640: OS: Linux ver 020615

00:00.640: Crash backtrace component: x86 custom backtrace

00:00.640: Crash lookup component: dladdr

00:00.640: Crash demangle component: cxa_demangle

00:00.641: Runtime library: glibc 2.3.6

00:00.641: Threads library: NPTL 2.3.6

00:00.641: TLS is available

00:00.641: AnnouncerManager::AnnouncerManager()

00:00.641: Reading 'Data/Static.ini' failed: No such file or directory

00:00.708: ThemeManager::SwitchThemeAndLanguage: "default", ""

00:00.755: Initializing driver: ALSA

00:00.814: ALSA: Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).

00:00.814: ALSA Driver: 0: Intel ICH5 [ICH5], device 0: Intel ICH [Intel ICH5], 1/1 subdevices avail

00:00.814: ALSA Driver: 0: Intel ICH5 [ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958], 1/1 subdevices avail

00:00.815: ALSA error: pcm_hw.c:1217 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy)

00:00.877: Could only create 1 buffers; need at least 8 (failed with dsnd_pcm_open(hw:0): Device or resource busy).  Hardware ALSA driver can't be used.

00:00.877: Couldn't load driver ALSA: Not enough substreams for hardware mixing, using software mixing

00:00.877: Initializing driver: ALSA-sw

00:00.878: OS: Linux ver 020615

00:00.879: ALSA: Software mixing at 44100hz

00:00.879: Starting thread: Decode thread

00:00.879: Starting thread: RageSound_ALSA9_Software

00:00.879: Sound driver: ALSA-sw

00:00.880: Starting thread: MusicThread

00:00.880: Couldn't open file "Data/Coins.dat": No such file or directory

00:00.880: Initializing lights driver: Null

00:00.885: Reading 'Data/Keymaps.ini' failed: No such file or directory

00:00.885: Couldn't open mapping file "Data/Keymaps.ini": No such file or directory.

00:00.886: Reading 'Cache/index.cache' failed: No such file or directory

00:00.886: Cache format is out of date.  Deleting all cache files.

00:00.886: remove '/home/nathan/Desktop/StepMania-3.9-rc2a/./Cache/banners.cache'

00:00.890: remove '/home/nathan/Desktop/StepMania-3.9-rc2a/./Cache/Banners/1527817133'

00:00.890: remove '/home/nathan/Desktop/StepMania-3.9-rc2a/./Cache/Banners/1654699250'

00:00.890: remove '/home/nathan/Desktop/StepMania-3.9-rc2a/./Cache/Banners/543857581'

00:00.891: remove '/home/nathan/Desktop/StepMania-3.9-rc2a/./Cache/Banners/585729452'

00:00.891: Reading 'Cache/banners.cache' failed: No such file or directory

00:00.915: Found 0 songs in 0.000154 seconds.

00:00.915: Loading courses.

00:00.915: underrun (320 frames)

00:00.915: underrun (303 frames)

00:00.915: underrun (241 frames)

00:00.915: underrun (179 frames)

00:00.915: underrun (116 frames)

00:00.915: underrun (54 frames)

00:00.993: underrun (2560 frames)

00:00.993: underrun (2506 frames)

00:00.993: underrun (2444 frames)

00:00.993: underrun (2382 frames)

00:00.993: underrun (2319 frames)

00:00.993: underrun (2257 frames)

00:00.993: underrun (2194 frames)

00:00.993: underrun (2130 frames)

00:00.993: underrun (2067 frames)

00:00.993: underrun (2005 frames)

00:00.993: underrun (1942 frames)

00:00.993: underrun (1880 frames)

00:00.993: underrun (1817 frames)

00:00.993: underrun (1755 frames)

00:00.993: underrun (1692 frames)

00:00.993: underrun (1630 frames)

00:00.993: underrun (1567 frames)

00:00.993: underrun (1505 frames)

00:00.993: underrun (1442 frames)

00:00.993: underrun (1380 frames)

00:00.993: underrun (1317 frames)

00:00.993: underrun (1255 frames)

00:00.993: underrun (1192 frames)

00:00.994: underrun (1129 frames)

00:00.994: underrun (1065 frames)

00:00.994: underrun (1003 frames)

00:00.994: underrun (940 frames)

00:00.994: underrun (878 frames)

00:00.994: underrun (815 frames)

00:00.994: underrun (753 frames)

00:00.994: underrun (690 frames)

00:00.994: underrun (628 frames)

00:00.994: underrun (567 frames)

00:00.994: underrun (505 frames)

00:00.994: underrun (442 frames)

00:00.994: underrun (380 frames)

00:00.994: underrun (317 frames)

00:00.994: underrun (255 frames)

00:00.994: underrun (192 frames)

00:00.994: underrun (128 frames)

00:00.994: underrun (66 frames)

00:00.994: underrun (3 frames)

00:00.994: Course::LoadFromCRSFile( 'Courses/Samples/AllChallenge.crs' )

00:01.014: Course::LoadFromCRSFile( 'Courses/Samples/AllMusicRandom.crs' )

00:01.015: Course::LoadFromCRSFile( 'Courses/Samples/EndOfTheRoad.crs' )

00:01.022: Course::LoadFromCRSFile( 'Courses/Samples/PlayersBest1-4.crs' )

00:01.023: Course::LoadFromCRSFile( 'Courses/Samples/PlayersBest13-16.crs' )

00:01.024: Course::LoadFromCRSFile( 'Courses/Samples/PlayersBest5-8.crs' )

00:01.024: Course::LoadFromCRSFile( 'Courses/Samples/PlayersBest9-12.crs' )

00:01.044: Course::LoadFromCRSFile( 'Courses/Samples/PlayersWorst.crs' )

00:01.045: Course::LoadFromCRSFile( 'Courses/Samples/Random Caprice.crs' )

00:01.046: Course::LoadFromCRSFile( 'Courses/Samples/StaminaTester.crs' )

00:01.062: Course::LoadFromCRSFile( 'Courses/Samples/Tortoise and the Hare.crs' )

00:01.071: Course::LoadFromCRSFile( 'Courses/Samples/Tournamix 4 Sample.crs' )

00:01.072: Course file 'Courses/Samples/Tournamix 4 Sample.crs' contains a fixed song entry 'Help me Dr. Dick' that does not exist. This entry will be ignored.

00:01.072: Course file 'Courses/Samples/Tournamix 4 Sample.crs' contains a fixed song entry 'DOO-BE-DI-BOY (KCP MIX)' that does not exist. This entry will be ignored.

00:01.072: Course file 'Courses/Samples/Tournamix 4 Sample.crs' contains a fixed song entry 'Laugh and Beats' that does not exist. This entry will be ignored.

00:01.072: Course file 'Courses/Samples/Tournamix 4 Sample.crs' contains a fixed song entry 'Baby Got Back' that does not exist. This entry will be ignored.

00:01.073: Course::LoadFromCRSFile( 'Courses/Samples/TrickyRandom.crs' )

00:01.083: Writing Data/Catalog.xml ...

00:01.096: Done.

00:01.123: RageSound::LoadSound( 'Themes/default/Sounds/MemoryCardManager ready.ogg' )

00:01.133: RageSound::LoadSound( 'Themes/default/Sounds/MemoryCardManager error.ogg' )

00:01.134: RageSound::LoadSound( 'Themes/default/Sounds/MemoryCardManager too late.ogg' )

00:01.134: RageSound::LoadSound( 'Themes/default/Sounds/MemoryCardManager disconnect.ogg' )

00:01.181: Profile::LoadAllFromDir( Data/MachineProfile/ )

00:01.188: Reading 'Data/MachineProfile/Editable.ini' failed: No such file or directory

00:01.188: Loading Data/MachineProfile/Stats.xml

00:01.188: Done.

00:01.188: UnlockSystem::Load()

00:01.240: underrun (640 frames)

00:01.240: underrun (615 frames)

00:01.240: underrun (552 frames)

00:01.240: underrun (489 frames)

00:01.240: underrun (427 frames)

00:01.240: underrun (364 frames)

00:01.240: underrun (302 frames)

00:01.240: underrun (239 frames)

00:01.240: underrun (177 frames)

00:01.240: underrun (114 frames)

00:01.240: underrun (52 frames)

00:01.270: Last seen video driver: OpenGL

00:01.270: Card matches 'OpenGL'.

00:01.270: Video renderers: 'opengl'

00:01.327: RageDisplay_OGL::RageDisplay_OGL()

00:01.677: underrun (64 frames)

00:01.677: underrun (28 frames)

00:01.691: underrun (128 frames)

00:01.691: underrun (69 frames)

00:01.691: underrun (7 frames)

00:01.986: SDL version: 1.2.9

00:01.986: Got 32 bpp (8888), 24 depth, 0 stencil

00:01.987: Paletted textures disabled: GL_EXT_paletted_texture missing.

00:01.987: FPS: 1, CFPS 1, VPF: 0

00:01.987: OGL Vendor: Tungsten Graphics, Inc.

00:01.987: OGL Renderer: Mesa DRI R300 20040924 AGP 1x TCL

00:01.987: OGL Version: 1.2 Mesa 6.4.1

00:01.987: OGL Extensions: GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod

00:01.988: OGL Max texture size: 2048

00:01.988: GLU Version: 1.3

00:01.988: Display: :0.0 (screen 0)

00:01.988: Direct rendering: yes

00:01.988: X server vendor: The X.Org Foundation [7.0.0.0]

00:01.993: Server GLX vendor: SGI [1.2]

00:01.993: Client GLX vendor: SGI [1.4]

00:01.993: Fullscreen 640x480 16 color 16 texture 0Hz Vsync AA

00:01.993: RageInput::RageInput()

00:01.993: Found 0 joysticks


```

Thanks in advance for any help.

---

### Post by marcos89 on 2006-06-07
I got the game working using the linux binary they offer at the official website, i double clicked the Stepmania executable and it ran without ANY Problems :) 
Using FRESH Install of dapper drake.

---

### Post by hypersoar on 2006-06-09
bump

---

