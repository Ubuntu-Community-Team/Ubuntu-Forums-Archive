---
title: "Doom 3 &quot;unable to initialize OpenGL&quot;"
date: 2007-04-21
forum: Gaming &amp; Leisure
---

### Post by shmeeter on 2007-04-21
and "couldn't get a visual."

Hi all!

I was hoping for some help here.  I can't get Doom 3 running, and if I can it would be good for my bragging rights, and good for Linux/Ubuntu whenever I promote Linux.  Plus a lot of fun!

Here is some various outputs.

Doom3 terminal output:
```

ian@deja-vu:~$ doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth1 - 10.0.0.100/255.255.255.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/ian/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 640x480
Couldn't get a visual
idRenderSystem::Shutdown()
Fatal X Error:
  Major opcode of failed request: 105
  Minor opcode of failed request: 0
  Serial number of failed request: 49
BadValue (integer parameter out of range for operation)
Fatal X Error:
  Major opcode of failed request: 2
  Minor opcode of failed request: 0
  Serial number of failed request: 53
BadWindow (invalid Window parameter)
Fatal X Error:
  Major opcode of failed request: 4
  Minor opcode of failed request: 0
  Serial number of failed request: 54
BadWindow (invalid Window parameter)
Sys_Error: Unable to initialize OpenGL

```

Here is fglrxinfo output:
```

ian@deja-vu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

Here is glxinfo output:
```

ian@deja-vu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  6 1 None

```

Here is my xorg.conf file:
```

ian@deja-vu:~$ cat /etc/X11/xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "ServerLayout"

# changed as per DDC from
#       InputDevice     "Configured Mouse"
# to
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
# changed as per DDC from
#       InputDevice     "Synaptics Touchpad"
# to
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse" "SendCoreEvents"
        InputDevice    "Synaptics Touchpad" "CorePointer"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
        Load  "synaptics"
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

# commented out as per DoubleDangerClub
#       Option          "CorePointer"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

# commented out as per DoubleDangerClub
#       Option          "SendCoreEvents"        "true"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
# added as per DDC
        Option      "SHMConfig" "on"
# customizations added by me
        Option      "MaxTapTime" "0"    #disables tap-to-click
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x800" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

# added by ian as per web instructions at help.ubuntu.com/community/BinaryDriverHowto/ATI
Section "Extensions"
        Option  "Composite" "0"
EndSection

```

Thanks a lot in advance for any help!
Shmeeter

---

### Post by noerrorsfound on 2007-05-12
Well, since trying to help even if you fail is better than not trying at all, I searched Google to try and find a possible solution.

Type this into the terminal:
```
export LD_PRELOAD=/usr/lib/libGL.so.1
```

Now try to run Doom 3 again. Good luck!

---

### Post by shmeeter on 2007-05-16
I don't know what I did, but Doom 3 now runs great!  (greatly?  heh heh...)

Thanks for the reply, by the way.  I tried the preload thing, and it didn't work.

On desktop:
Dapper didn't work, even with fglrx ATI driver.  Upgraded to Feisty, put fglrx in, tried to install Doom 3, and everything was peachy!

On laptop:
Dapper didn't work.  All kinds of stuff didn't work.  The desktop experience convinced me to upgrade to Feisty on laptop, as well, even though this made me nervous for several reasons.  Install went okay, everything worked.  Except Doom!  Tried manual install - nope.  Tried googling my error (some script error, spat some number at me and said that the directory was missing some shell script component or something.  I forget really...) - nope.  Decided that I was going to work at a manual install, no matter how long it took, following the desktop as a model - nope.  Couldn't find a file or something...  Tried to run the install script again - it worked!

I don't know if some Feisty upgrade in the middle did the trick or if my manual install attempt made a difference, but it works now.

The only reason I ever boot to Windows now?  MS Office and burning DVDs.  Open office is cool, but the compatibility is just not there, and if I need to do something for school, I have to use what they use on campus.  And DVDs?  I just haven't looked yet, but I hear burning DVDs is WAY easier in Windows these days...

Ciao!

---

