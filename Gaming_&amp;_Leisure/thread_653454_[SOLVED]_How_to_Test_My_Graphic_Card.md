---
title: "[SOLVED] How to Test My Graphic Card?"
date: 2007-12-29
forum: Gaming &amp; Leisure
---

### Post by kirtan on 2007-12-29
I have installed Xubuntu 7.10 and installed Cedega 6.0.2 

and its says 3D Accrelaration and Open GL Test Failed 

but In ubuntu 7.10 It was Working Perfectly it did Not Failed in Ubuntu 7.10

Plz Help me To Solve my Problem 

any Command that can test ..Graphic card Rendering is Correct or Not

---

### Post by tgalati4 on 2007-12-29
In a terminal, post the output of:

>glxinfo

---

### Post by kirtan on 2007-12-29
```
kirtan@Kirtan-Desktop:~$ glxinfo
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
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x65 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by tgalati4 on 2007-12-30
You don't have direct rendering turned on.

Post the output of:

>lspci

and

>cat /etc/X11/xorg.conf

---

### Post by kirtan on 2007-12-30
```
kirtan@Kirtan-Desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
05:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
05:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

```

```
kirtan@Kirtan-Desktop:~$ cat /etc/X11/xorg.conf
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

Section "Files"
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
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Boardname       "Intel 810"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  0
        Vendorname      "Intel"
        Option          "XaaNoPixmapCache"
EndSection

Section "Monitor"
        Identifier      "T710BH"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Monitor         "T710BH"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1400    1050
                Modes           "1024x768@85"   "1024x768@75"   "832x624@75"   "1024x768@70"    "800x600@60"    "1024x768@60"   "800x600@85"    "1024x768@43"  "800x600@75"     "1152x864@75"   "800x600@72"    "1280x960@60"   "800x600@56"   "1280x1024@60"   "640x480@85"    "1400x1050@60"  "640x480@75"    "640x480@72"   "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "dri"
        Load            "v4l"
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by tgalati4 on 2007-12-30
You have an Intel i915 graphics card.  Xubuntu loaded the i810 driver.  Try changing to the "intel" driver.

Section "Device"
        Identifier      "Intel Corporation **82915G**/GV/910GL Integrated Graphics Controller"
        Boardname       "Intel 810"
        Busid           "PCI:0:2:0"
**        Driver          "i810"   # Change this to "intel"**
        Screen  0
        Vendorname      "Intel"
        Option          "XaaNoPixmapCache" # try taking this statement out
EndSection


---------------------------------

Go into you BIOS and set the memory sharing for Video to maximum typically 128 or 224 MB.  If you don't allocate enough memory to the graphics card, 3D won't work.

---

### Post by kirtan on 2007-12-30
Thanks for Support 
but 
How do i Do that?


I selected intel 915 graphic card but it loads Driver of i810

---

### Post by tgalati4 on 2007-12-30
>sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
>sudo nano /etc/X11/xorg.conf

(make your changes, Control-O, Control-X, when done).

Also a simple method is to boot your machine with the Live CD of 7.10 (which you said works OK) and print out /etc/X11/xorg.conf.  Then use this as a reference to what is used in Xubuntu.

---

### Post by kirtan on 2007-12-30
Thanks Mate my problem Solved With 

 Installing  
   * xlibmesa-dri
    * xlibmesa-gl
    * xlibmesa-glu
    * mesa-utils
    * libgl1-mesa-dri
    * libgl1-mesa-glx

thanks thanks thanks a lot

---

