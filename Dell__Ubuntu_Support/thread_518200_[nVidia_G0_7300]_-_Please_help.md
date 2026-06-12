---
title: "[nVidia G0 7300] - Please help"
date: 2007-08-05
forum: Dell  Ubuntu Support
---

### Post by COKE CAN on 2007-08-05
I have searched google, linuxforums, here, and more.

I installed the nVidia driver with no problems a year ago when running Dapper Drake running 7.04 now on a Dell E1505

I have tried installing through Automatix2
I have followed installing all packages through apt-get and installing the driver from nVidia's site

Everything I do doesn't work

I end up with a blue text-based screen that says something along the lines of "X failed to start.  There is a problem with xorg..."

I can't ever get out of it 

I mean, my resolution is fine, but my computer goes nuts when screensavers come on.

I turn the driver on in the restricted drivers section and restart to the same blue screen.

Below are some things that might help:

```
thegoodpirate@laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
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
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
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
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x25 16 tc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x26 16 tc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x27 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x29 16 dc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x2a 16 dc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

```
thegoodpirate@laptop:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "dbe"
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
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

I really do not want to redo everything all over again...

---

### Post by MepisReign on 2007-08-05
What I would do is type on a Terminal:

sudo gedit /etc/X11/xorg.conf

Under Device replace "nv" for "nvidia"

Save the file

I would reboot now, others may tell you to restart X

Once you are in the OS, type on the Terminal

sudo nvidia-settings
There make the changes that u may require and don't forget to click on Save to X configuration file, at this point u may able to run OpenGL screensavers.

Let us know about the result

Regards,

MepisReign

---

### Post by COKE CAN on 2007-08-05
I am staring at the blue screen again, it states:

```
Failed to start X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?
```

---

### Post by COKE CAN on 2007-08-05
I edited out the driver and put it back to nv

Now, the restricted driver for nVidia is not turned on.  Should it be before changing the xorg.conf file?

---

### Post by COKE CAN on 2007-08-05
*edit*

It appears that the file did not save with "nv"

---

### Post by MepisReign on 2007-08-05
That is definitely a Driver problem, you could try

sudo dpkg-reconfigure xserver-xorg

Uninstall the Automatix nvidia driver and then on Synaptic, install

nvidia-glx-new (remember to enable the restricted repos)

Then follow the instructions on my previous post

So far that is what I can tell you, maybe someone else with more experience could give us a hand here?

Regards,

MepisReign

---

### Post by MepisReign on 2007-08-05
> **COKE CAN said:**
> I edited out the driver and put it back to nv

Now, the restricted driver for nVidia is not turned on.  Should it be before changing the xorg.conf file?

If "nv" is displayed you can be sure that the system doesn't have 3D acceleration enabled, we need "nvidia" there.

---

### Post by COKE CAN on 2007-08-05
> **MepisReign said:**
> That is definitely a Driver problem, you could try

sudo dpkg-reconfigure xserver-xorg

Uninstall the Automatix nvidia driver and then on Synaptic, install

nvidia-glx-new (remember to enable the restricted repos)

Then follow the instructions on my previous post

So far that is what I can tell you, maybe someone else with more experience could give us a hand here?

Regards,

MepisReign

More info:

Since I redid everything for the fifth time yesterday nothing for nVidia was enabled by me.

I am now enabling the driver in the restricted drivers console

I will edit the xorg.conf file and reboot

---

### Post by COKE CAN on 2007-08-05
Looks like enabling the driver in the restricted drivers console edited the xorg.conf for me

---

### Post by COKE CAN on 2007-08-05
Restarted the machine and now I am able to get into X

It states when I log in that restricted drivers are in use and cannot be supported.  I have yet to get this far before.

What does that mean and what do I do now?

---

### Post by MepisReign on 2007-08-05
> **COKE CAN said:**
> Restarted the machine and now I am able to get into X

It states when I log in that restricted drivers are in use and cannot be supported.  I have yet to get this far before.

What does that mean and what do I do now?

Just accept that statement and actually use the driver, u may click on the notification icon on the panel and state by clicking on Yes that u want to use the "unsupported and restricted" driver, that will be all ;)

Greetz!

MepisReign

---

### Post by COKE CAN on 2007-08-05
> **MepisReign said:**
> Just accept that statement and actually use the driver, u may click on the notification icon on the panel and state by clicking on Yes that u want to use the "unsupported and restricted" driver, that will be all ;)

Greetz!

MepisReign

Yay!  Tried a 3D screensaver and it doesn't spaz anymore!

Thanks MepisReign!

---

### Post by MepisReign on 2007-08-05
I'm glad that helped you, that's why we all are here for :)

:guitar:

---

