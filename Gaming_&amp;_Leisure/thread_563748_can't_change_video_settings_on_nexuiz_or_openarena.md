---
title: "can't change video settings on nexuiz or openarena"
date: 2007-09-30
forum: Gaming &amp; Leisure
---

### Post by angryfirelord on 2007-09-30
I recently installed Gutsy Beta with the 8.41.7 video drivers (I use an X1600). In Feisty, I never had this issue, but in Gutsy, when I try to change any type of video setting in nexuiz or openarena, it crashes.
Output for Nexuiz:
```
Console initialized.
Nexuiz Linux 09:52:45 Jul  6 2007
Trying to load library... "libz.so.1" - loaded.
Compressed files support enabled
Added packfile /usr/share/games/nexuiz/data/data20070531.pk3 (3665 files)
Added packfile /usr/share/games/nexuiz/data/music20070531.pk3 (10 files)
Trying to load library... "libcurl.so.4" - loaded.
cURL support enabled
Initializing client
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Ogg Vorbis support enabled
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Starting video system
Video: fullscreen 800x600x32x60hz
Linked against SDL version 1.2.11
Using SDL library version 1.2.11
checking for OpenGL 1.1.0...  enabled
GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Mobility Radeon X1600
GL_VERSION: 2.0.6849 Release
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_KTX_buffer_region GL_NV_blend_square GL_NV_texgen_reflection GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_WIN_swap_hint WGL_EXT_swap_control 
SDL_EXTENSIONS: 
Checking OpenGL extensions...
checking for glDrawRangeElements...  enabled
checking for GL_ARB_multitexture...  enabled
checking for GL_ARB_texture_env_combine...  enabled
checking for GL_ARB_texture_env_dot3...  enabled
checking for GL_EXT_texture3D...  enabled
checking for GL_ARB_texture_cube_map...  enabled
checking for GL_ARB_texture_non_power_of_two...  not detected
checking for GL_EXT_compiled_vertex_array...  enabled
checking for GL_EXT_texture_edge_clamp...  enabled
checking for GL_EXT_texture_filter_anisotropic...  enabled
checking for GL_EXT_blend_minmax...  enabled
checking for GL_EXT_blend_subtract...  enabled
checking for glStencilOpSeparate...  enabled
checking for GL_EXT_stencil_two_side...  not detected
checking for GL_ARB_vertex_buffer_object...  enabled
checking for GL_ARB_shader_objects...  enabled
checking for GL_ARB_shading_language_100...  enabled
checking for GL_ARB_vertex_shader...  enabled
checking for GL_ARB_fragment_shader...  enabled
0 SDL joystick(s) found:
OpenGL Backend starting...
glDrawRangeElements detected (max vertices 2147483647, max indices 16384)
GLSL shader support detected: texture units = 8 texenv, 16 image, 8 array
OpenGL backend started.
Trying to load library... "libjpeg.so.62" - loaded.
JPEG support enabled
Trying to load library... "libpng12.so.0" - loaded.
PNG support enabled
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
SndSys_Init: using the SDL module
Sound format: 48000Hz, 2 channels, 16 bits per sample
Found 1 cdrom drives.
No CD in drive 0.
CDAudio_Init: No CD in player.
Can't get initial CD volume
CD Audio Initialized
Draw_CachePic: failed to load gfx/m_white
Fake CD track 1 playing...
Client using port 0
Client opened a socket on address local:2
Client opened a socket on address 0.0.0.0:32938
VID_Restart: changing from fullscreen 800x600x32bpp, to fullscreen 1024x768x32bpp.
OpenGL Backend shutting down
Video: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.11
Using SDL library version 1.2.11
Segmentation fault (core dumped)

```
Output for openarena:
```
ioQ3 1.33+oa linux-i386 Jul  5 2007
----- FS_Startup -----
Current search path:
/home/master/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (96 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (7 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (932 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (187 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (25 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (748 files)
/usr/share/games/openarena/baseoa
/usr/lib/games/openarena/baseoa

----------------------
1995 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
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
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: ATI Mobility Radeon X1600
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Mobility Radeon X1600
GL_VERSION: 2.0.6849 Release
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_KTX_buffer_region GL_NV_blend_square GL_NV_texgen_reflection GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_WIN_swap_hint WGL_EXT_swap_control 
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/player_gargoyle.shader'
...loading 'scripts/player_kyonshi.shader'
...loading 'scripts/player_major.shader'
...loading 'scripts/player_tux.shader'
...loading 'scripts/ammo.shader'
...loading 'scripts/beams.shader'
...loading 'scripts/ctf.shader'
...loading 'scripts/decals.shader'
...loading 'scripts/details.shader'
...loading 'scripts/detailtest.shader'
...loading 'scripts/evil8.shader'
...loading 'scripts/flaretest.shader'
...loading 'scripts/iconsprites.shader'
...loading 'scripts/item_health.shader'
...loading 'scripts/liquid_lavas.shader'
...loading 'scripts/liquid_water.shader'
...loading 'scripts/map_chpwatery2.shader'
...loading 'scripts/newmenu.shader'
...loading 'scripts/oactf.shader'
...loading 'scripts/oaflares.shader'
...loading 'scripts/oagfx.shader'
...loading 'scripts/oalite.shader'
...loading 'scripts/oanew.shader'
...loading 'scripts/oapowerups.shader'
...loading 'scripts/oasky.shader'
...loading 'scripts/oa_fogs.shader'
...loading 'scripts/oquartz.shader'
...loading 'scripts/q3map2_void3.shader'
...loading 'scripts/q3map2_void4.shader'
...loading 'scripts/qtex.shader'
...loading 'scripts/shells.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/temporary.shader'
...loading 'scripts/weaponhits.shader'
...loading 'scripts/weaponry.shader'
...loading 'scripts/weapon_chaingun.shader'
...loading 'scripts/weapon_gauntlet.shader'
...loading 'scripts/weapon_grenadelauncher.shader'
...loading 'scripts/weapon_machinegun.shader'
...loading 'scripts/weapon_muzzles.shader'
...loading 'scripts/weapon_plasma.shader'
...loading 'scripts/weapon_railgun.shader'
...loading 'scripts/weapon_rocketlauncher.shader'
----- finished R_Init -----
------ Initializing Sound ------
Allocated 96 sources.
OpenAL info:
  Vendor:     OpenAL Community
  Version:    1.1
  Renderer:   Software
  Extensions: ALC_EXT_capture AL_EXT_capture AL_EXT_vorbis AL_EXT_MP3 AL_LOKI_quadriphonic AL_LOKI_play_position AL_LOKI_WAVE_format AL_LOKI_IMA_ADPCM_format AL_LOKI_buffer_data_callback ALC_LOKI_audio_channel 
Sound initialization successful.
--------------------------------
Loading vm file vm/ui.qvm...
VM file ui compiled to 585869 bytes of code
ui loaded in 1363392 bytes on the hunk
7 arenas parsed
3 arenas ignored to make count divisible by 4
6 bots parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: ubuntu-laptop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 4: 800 600
Received signal 11, exiting...
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Shutdown tty console

```
Here is my xorg.conf:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        #Option     "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        #Option     "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        #Option     "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    30.0 - 90.0
        VertRefresh  50.0 - 60.0
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI RADEON X1600"
        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "off"
        Option      "OpenGLOverlay" "on"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI RADEON X1600"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

#Section "Extensions"
#       Option      "Composite" "0"
#EndSection


```
Thoughts?

---

