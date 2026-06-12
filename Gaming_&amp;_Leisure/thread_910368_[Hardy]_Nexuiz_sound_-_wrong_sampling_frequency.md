---
title: "[Hardy] Nexuiz sound - wrong sampling frequency?"
date: 2008-09-04
forum: Gaming &amp; Leisure
---

### Post by dgel on 2008-09-04
Hi,

I'm trying to get sound in nexuiz to work right. I use libsdl1.2-debian for sound output, for compatibility reasons with other games, but doing so apparently breaks nexuiz which works fine otherwise.
The problem is that the sound is too slow. However, when I set the number of speakers lower, it speeds up again. at 1 or 2 speakers it is fine, but I have 6 speakers and want to use them.
So, does anyone know a way around this?

btw, console output for nexuiz is this:
```

Nexuiz Linux 21:39:39 Jun 15 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data.pk3 (4066 files)
Added packfile /usr/share/games/nexuiz/data/music.pk3 (10 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
execing config.cfg
execing config_update.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Initializing Video Mode: fullscreen 1280x1024x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
GL_VENDOR: DRI R300 Project
GL_RENDERER: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE TCL
GL_VERSION: 1.3 Mesa 7.0.3-rc2
GL_EXTENSIONS: GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_MESAX_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_gpu_program_parameters GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
SDL_EXTENSIONS: 
0 SDL joystick(s) found:
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
Shader 'textures/Reaptxt/sun' already defined
S_Startup: initializing sound output format: 44100Hz, 16 bit, 6 channels...
Wanted audio Specification:
	Channels  : 6
	Format    : 0x8010
	Frequency : 44100
	Samples   : 4096
Obtained audio specification:
	Channels  : 6
	Format    : 0x8010
	Frequency : 44100
	Samples   : 4096
Sound format: 44100Hz, 6 channels, 16 bits per sample
S_SetChannelLayout: using ALSA speaker layout for 3D sound
Found 1 cdrom drives.
No CD in drive 0.
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized
Client using an automatically assigned port
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:54194
Fake CD track 1 playing...

```

---

### Post by detrate on 2008-09-05
You may have better assistance in the [Official Support Forum](http://alientrap.org/forum/viewforum.php?f=3).

---

