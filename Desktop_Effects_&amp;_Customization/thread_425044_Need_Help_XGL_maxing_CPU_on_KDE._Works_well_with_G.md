---
title: "Need Help: XGL maxing CPU on KDE. Works well with Gnome"
date: 2007-04-27
forum: Desktop Effects &amp; Customization
---

### Post by Zappatta on 2007-04-27
Hello Everybody.

I've installed Feisty on my laptop computer, and after following a few rather simple guides I've even managed to get Beryl working on it.

After getting Beryl to work, I've decided i want to switch from gnome to KDE, which I'm more fond of. 

I've also followed several guides, and created a new session in which XGL loads KDE instead of Gnome.

When selecting the xgl and KDE session, everything seems to load fine but works VERY VERY slow.  After a short investigation I've found out that the xgl process keeps taking 95-97% of the CPU at any given time. Needless to say, this makes working on the computer impossible.

This does not happen to me when i load XGL and Gnome. 

I could really use some help with this issue.

I've included relevant configuration files at the end of this post. They should include all the information i think is relevant. Nevertheless, I have a Radeon mobility 9600 GPU, and am using the fglrx driver.

Thanks!

:guitar: 

Here is the relevant startxgl file I've created
```

#!/bin/sh
export KDEWM="/usr/bin/compizrc"
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
# Nvidia users should change xv:pbuffer for xv if it doesnt work directly (it does for me)
DISPLAY=:1
exec startkde

```

and now here is my kde-xgl.desktop file:
```

[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=startxgl-kde
TryExec=startxgl-kde
Name=KDE with XGL support
Name[en_CA]=KDE with XGL support
Name[en_GB]=KDE with XGL support 

```

and now here is my xorg.conf
```

Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x- ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us,il"
    Option        "XkbVariant"    ","
    Option        "XkbOptions"    "grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
    Option      "SHMConfig"          "true"
    Option         "RBCornerButton"     "7"
    Option         "LBCornerButton"     "6"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
    Driver        "fglrx"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Extensions"
    Option    "Composite"    "false"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1400x1050"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1400x1050"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1400x1050"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1400x1050"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1400x1050"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1400x1050"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection

```

and finally, here is what i get by running glxinfo (on gnome)
```

name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ": 1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700
OpenGL version string: 1.2 (2.0.6334 (8.34.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon 

```

---

### Post by Zappatta on 2007-05-11
at the startxgl-kde script, I was setting KDE to use compiz as the window manager, and not beryl. This was the cause of the problem.

To solve this, I've changed the line

```
export KDEWM="/usr/bin/compizrc"
```
to
```
export KDEWM="/usr/bin/beryl-manager"
```

Hope this helps someone.

Cheers!

---

