---
title: "ati drivers ok,glxgears-fgl_glxgears ok, 3d games black screen;("
date: 2005-04-22
forum: Gaming &amp; Leisure
---

### Post by iomicifikko on 2005-04-22
hi all, i have a problem with 3d games, if i try to run a 3d game i get just a black screen (or window).

i have a mobility radeon 9700, follow all the steps to get it working with fglrx drivers, glxgears and fgl_glxgears work both at good fps, everything is ok but the games dont run;). i have warty installed too and everything is ok there,sigh i tryed to change different options but nothing.

i report my xorg (hoary) and my Xf86config (warty), maybe someone of u find something interesting;)

xorg:

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load "GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
# Load "extmod" but omit DGA extension
# (the DGA extension is broken in the fglrx driver)
  SubSection "extmod"
    Option "omit xfree86-dga"
  EndSubSection

	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection

#Section "Device"
#	Identifier	"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
#	Driver		"fglrx"
#	BusID		"PCI:1:0:0"
#EndSection

Section "Device"
    Identifier                          "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x06419064"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                    "0"
    Option "BlockSignalsOnLock"       "on"
    Option "backingstore" "true"
    #Option "UseInternalAGPGART"   "no" 
    Option "UseInternalAGPGART"      "yes"
    Option "ForceGenericCPU"           "no"
    Option     "AGPMode" "4"
    Option     "AGPFastWrite" "True"
    Option     "EnablePageFlip" "True"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e50
    Screen 0
EndSection


Section "Monitor"
	Identifier	"Monitor Generico"
        HorizSync   28-64
        VertRefresh 43-60
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Monitor		"Monitor Generico"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection



---->i have tryed all the possibilities with useinternalAGPGART  on/off and loading agpgart kernel module or not.


xf86config:


# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection

Section "Files"


    RgbPath	"/usr/X11R6/lib/X11/rgb"

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection


# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"Keyboard"

    Option "AutoRepeat" "500 30"


    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"it"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

    Option "Emulate3Buttons"    "true"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"


EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "MinSpeed"            "0.11"
        Option          "MaxSpeed"           "0.11"
EndSection

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   28-64
    VertRefresh 43-60
    Option "DPMS"
    Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841


# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    Option     "AGPMode" "4"
    Option     "AGPFastWrite" "True"
    Option     "EnablePageFlip" "True"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e50
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes      "1280x800" "1152x864" "1024x768" "800x600"
        ViewPort    0 0  # initial origin if mode is smaller than desk
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

    Screen "Screen0"



    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Synaptics Touchpad"
EndSection

### EOF ###



fglrxinfo layout:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)



glxinfo layout:

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)
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
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ATI_draw_buffers,
    GL_ATI_element_array, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
    GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_texgen_reflection,
    GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_EXT_vertex_shader,
    GL_HP_occlusion_test, GL_NV_texgen_reflection, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_SGI_color_matrix, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_lod,
    GL_SGIS_generate_mipmap, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None



sorry for the long msg, any help appreciated, thanks all, byez

---

### Post by Burgundavia on 2005-04-22
This may actually be a sound issue. Try 'killall esd' before you run the game.

Corey

---

### Post by iomicifikko on 2005-04-26
[QUOTE=Burgundavia]This may actually be a sound issue. Try 'killall esd' before you run the game.

Corey[/QUOTE]

u are right!

thank u very much my friend, i was so engaged trying to find the right graphic configuration that i didnt think  that could be a sound problem.

do u know how i could actually solve the problem , maybe changing from libesd0 to libesd-alsa0?

thanks again bye!

---

### Post by iomicifikko on 2005-04-27
ok solved the problem following the cool sound howto in the unofficial starter guide, i jad to change just a value in asound.conf: hw:0,0 instead of hw:1,0

bye

---

