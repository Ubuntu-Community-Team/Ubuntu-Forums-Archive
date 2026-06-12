---
title: "UT 2004 on 64-bit ubuntu? (search had no answers)"
date: 2008-04-15
forum: Gaming &amp; Leisure
---

### Post by Dark_Rider2k3 on 2008-04-15
I have been searching the forums, and google, and have had no luck in fixing my problem.

First, here are my system specs:

HP DV6646 US laptop
Nvidia GeForce GO 7150M graphics card
2 GB DDR2 RAM
AMD Turion 64 X2 Processor

93.5 Gigs of space allocated to Vista
approx. 10-15 gigs of space allocated to Ubuntu (i'm not 100% sure how much space I gave it.. but I do know that at most i'm using up 2 gigs of space on ubuntu sooo there is no way i'm running out of space)

I installed UT2004 fine, did the MegaPack and UT2004 Patch, but when I go to load up UT2004, I get nothing.

When I try to run it from the terminal, I get this:

Assertion failed: sizeof(*this)==GetClass()->GetPropertiesSize() [File:UnGame.cpp] [Line: 148]

History: 

Exiting due to error


does anyone know what is wrong?

Thanks a lot!!

---

### Post by Perfect Storm on 2008-04-16
Did you checked the ubuntu 64-bit guide sticky? There's a 64-bit guide on how to install ut2004.

---

### Post by Dark_Rider2k3 on 2008-04-16
wow, no I didn't :-o

shame on me :icon_frown:

well, i'll go do that now haha

thanks!

edit:

okay 1/2 that battle is over. UT2004 now loads, but crashes before I get to any screen (other then the initial splash that shows).with this error:

me@me-laptop:/usr/local/games/ut2004$ ut2004
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History: 

Exiting due to error

i'm not sure if you'd want it but here is my "glxinfo":

me@me-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_SGIX_fbconfig, GLX_ARB_get_proc_address
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shadow, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_ATI_texture_mirror_once, GL_EXT_texture_env_add, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by Cappy on 2008-04-16
You are using the open source drivers which aren't able to play 3D games.

Try enabling the restricted drivers (closed source) at System-->Administration-->Restricted Drivers Manager

---

### Post by Dark_Rider2k3 on 2008-04-16
okay I enabled the Nvidia-glx-new drivers, but got the same exact error

---

### Post by Cappy on 2008-04-16
Did you Alt+Control+Backspace (closes all programs and restarts X) or reboot?

If so, include your glxinfo in CODE tags again

---

### Post by Dark_Rider2k3 on 2008-04-16
yup I did..

here it is again:

```
jonjon@jonjon-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
jonjon@jonjon-laptop:~$ 



```

---

### Post by Perfect Storm on 2008-04-16
```
cat /etc/X11/xorg.conf
```

---

### Post by Dark_Rider2k3 on 2008-04-16
```
jonjon@jonjon-laptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "vesa"
        Busid           "PCI:0:18:0"
        Driver          "vesa"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1680x1050"
        Horizsync       31.5-65.5
        Vertrefresh     56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1680    1050
                Modes           "1280x800@60"   "1440x900@60"   "1280x720@60"  "1600x1024@60"   "1280x768@60"   "1680x1050@60"  "800x600@60"    "800x600@56"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "device" # 
        Identifier      "device1"
        Boardname       "vesa"
        Busid           "PCI:0:18:0"
        Driver          "vesa"
        Screen  1
EndSection
Section "screen" # 
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
EndSection
Section "monitor" # 
        Identifier      "monitor1"
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection
jonjon@jonjon-laptop:~$ 



```

---

### Post by Perfect Storm on 2008-04-16
```
sudo nano /etc/X11/xorg.conf
```

change,         Driver          "vesa"   to         Driver          "nvidia"

save: [ctrl]+[o]
exit: [ctrl]+[x]

restart X [ctrl]+[alt]+[backspace] or reboot

If it fails you can change the driver back to vesa in CLI.

---

### Post by Dark_Rider2k3 on 2008-04-16
ok well good and bad on this:

good: the drivers in xorg.conf are now showing as nvidia, and after restarting X, they are still as nvidia

bad:

1.

```
jonjon@jonjon-laptop:/usr/local/games/ut2004$ ut2004
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History: 

Exiting due to error
jonjon@jonjon-laptop:/usr/local/games/ut2004$ 

```

2. I cannot change my screen resolution back the model is showing up as: "Plug n' Play." I was originally setting it @ lcd panel 1024x768 (widescreen).

I tried changing it back, but upon doing that the drivers went back to VESA. When trying to use nvidia drivers w/ lcd panel 1024x768, it does not work and goes into that safe graphics mode.

Thanks for the help btw... It's too bad UT didn't install as easy as it did on my home pc :(

---

### Post by Dark_Rider2k3 on 2008-04-17
I hate to do this but...

*bump*

I cant' find anything for some odd reason.. it's like.. i've tried a lot of different problems..

but i'm wondering if it's my lcd monitor.. =/

---

### Post by doorknob60 on 2008-04-17
Graphic driver issues it looks like to me. I recommend trying Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Dark_Rider2k3 on 2008-04-18
WOW that fixed all of my issues!!!!

I'd like to say my problems are over but I do have 1 more, small problem.

the graphics for the background (when in settings mode) and the graphics for the rocket launcher are messed up. BTW, I have all settings maxed...

Other then that, the game runs great

THANKS A LOT

---

