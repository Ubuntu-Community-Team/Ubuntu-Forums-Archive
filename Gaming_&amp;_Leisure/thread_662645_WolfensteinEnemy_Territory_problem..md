---
title: "Wolfenstein:Enemy Territory problem."
date: 2008-01-09
forum: Gaming &amp; Leisure
---

### Post by rhc on 2008-01-09
When i click to et.x86 in Wolfenstein Enemy Territory.

it says
> 
/Games/Enemy$ ./et.x86
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/furkan/.etwolf/etmain
/home/furkan/Games/Enemy/etmain/pak2.pk3 (22 files)
/home/furkan/Games/Enemy/etmain/pak1.pk3 (10 files)
/home/furkan/Games/Enemy/etmain/pak0.pk3 (3725 files)
/home/furkan/Games/Enemy/etmain/mp_bin.pk3 (6 files)
/home/furkan/Games/Enemy/etmain

----------------------
3763 files in pk3 files
^3WARNING: profile.pid found for profile 'Rhc' - system settings will revert to defaults
execing default.cfg
couldn't exec language.cfg
execing profiles/Rhc/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Xlib: extension "XFree86-VidModeExtension" missing on display ":1.0".
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


************************************************** *********
You are using software Mesa (no hardware acceleration)!
Driver DLL used: libGL.so.1
If this is intentional, add
"+set r_allowSoftwareGL 1"
to the command line when starting the game.
************************************************** *********
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Xlib: extension "XFree86-VidModeExtension" missing on display ":1.0".
Received signal 11, exiting...

WHat is the problem?

Can you see?

---

### Post by FriedChips on 2008-01-09
looks like you don't have the proper drivers installed for your graphics card. Can you post the output of:
```
/sbin/lspci | grep VGA
cat /etc/X11/xorg.conf | grep Driver
glxinfo | grep Direct
```

---

### Post by rhc on 2008-01-09
> furkan@Furkan:~$ /sbin/lspci | grep VGA
bash: /sbin/lspci: No such file or directory
furkan@Furkan:~$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "fglrx"
furkan@Furkan:~$ glxinfo | grep Direct

This is the output.
And i want to give you a link :)
I searched hours for best driver,at least by Envy i did it.

[http://ubuntuforums.org/showthread.php?t=662598](http://ubuntuforums.org/showthread.php?t=662598)

---

### Post by FriedChips on 2008-01-09
Sorry about that I screwed up two of those commands try these two for me:
```
glxinfo
```
that one will be pretty lengthy but grep didn't find what I wanted though "glxinfo | grep direct" will probably work. Looking for the line that says direct rendering: yes/no :)
the lspci command I didn't realize wasn't in /sbin/ in ubuntu ( used to fedora stuff :) )
```
lspci | grep VGA
```
should work as it should be in $PATH anyway.

Well, ATI cards can be a pain to get working right, I sold mine in lou of a geforce card... But I'll help as best as I can or at least get you pointed in the right direction ( hopefully ;) ). Also why don't you go ahead and post your whole xorg.conf file
```
cat /etc/X11/xorg.conf
```

---

### Post by rhc on 2008-01-09
For  "lspci | grep VGA" 


> lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]



For "glxinfo"

> glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon



"cat /etc/X11/xorg.conf"

> cat /etc/X11/xorg.conf
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
        Option          "XkbLayout"     "tr"
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
        Identifier      "ATI Technologies Inc RV350 AP [Radeon 9600]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Monitor"
        Identifier      "F700B"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 AP [Radeon 9600]"
        Monitor         "F700B"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1024x768"      "832x624"      "800x600"        "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "Disable"
EndSection


---

### Post by FriedChips on 2008-01-09
[QUOTE=rhc]direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)[/QUOTE]
that is why it is not working. It appears that your drivers are still not functioning properly. Probably the best way to go is to reinstall ubuntu ( this could be avoided but would be quite time consuming to troubleshoot ) and use the restricted driver manager to install the drivers.

Fried.

---

### Post by rhc on 2008-01-09
> **FriedChips said:**
> that is why it is not working. It appears that your drivers are still not functioning properly. Probably the best way to go is to reinstall ubuntu ( this could be avoided but would be quite time consuming to troubleshoot ) and use the restricted driver manager to install the drivers.

Fried.

Should i format the machine?
How can i reinstall ubuntu without formatting?

---

### Post by FriedChips on 2008-01-09
boot from liveCD and choose the install from the desktop. When it asks about partitions, choose custom and it will take you to a screen that lists your partitions. From here right click on your ubuntu "/" partition and select "format" and mount as or use as "/". this will allow you to only wipe out and reinstall ubuntu and leave any other partition. e.g. a windows partition or whatever else is there... If you have valuable data saved to the Ubuntu partition you should first burn it to a CD or transfer it to a windows/other partition.

---

### Post by frodon on 2008-01-10
BTW, are you using compiz ?

If i remember well to get compiz working with ATI cards, xserver-xgl is installed and XGL don't allow direct rendering to be enabled.

---

### Post by FriedChips on 2008-01-10
I am pretty sure that direct rendering is still required for XGL, XGL is basically a replacement for xorg because of incompatibility. I believe recently this incompatibility was worked out with ATI's drivers so XGL is no longer necessary. Someone correct me if I am wrong.

---

### Post by rhc on 2008-01-10
Yeah it was true frodon.
It was the Xgl that ruins everything,
Is Xgl only one file or it comes with another lib file or something?
I will uninstall it from Synaptic.
Btw,no way to use Xgl with the games? Or another thing  instead of Xgl to use high effects?

---

### Post by frodon on 2008-01-10
Like mentioned in previous post it seems that latest ATI drivers allow to get compiz working without XGL however it is in general a bad idea to run compiz while gaming, it is known to decrease performances.

To get back to the normal xserver with direct rendering just uninstall the "xserver-xgl" package in synaptic and reboot (or kill your xserver).

---

### Post by rhc on 2008-01-10
And with new At&#305; drivers,maybe " metacity --replace"  won't be a true solution either.
Surely there ll be a performance lowdown like you said.

---

### Post by CodyCreepcore on 2009-12-27
i get this problem

```
x@x-desktop:~/Desktop$ et
ET 2.55 linux-i386 May 27 2003
----- FS_Startup -----
Current search path:
/home/x/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
3761 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
X Error of failed request: BadMatch (invalid parameter attributes)
  Major opcode of failed request: 1
  Minor opcode of failed request: 0
  Serial number of failed request: 41
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 42
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 43
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 8
  Minor opcode of failed request: 0
  Serial number of failed request: 44
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 12
  Minor opcode of failed request: 0
  Serial number of failed request: 45
X Error of failed request: BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request: 136
  Minor opcode of failed request: 7
  Serial number of failed request: 50
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 154
  Minor opcode of failed request: 26
  Serial number of failed request: 50
Received signal 11, exiting...
Segmentation fault

```

display goes to 800 x 600 and stays on desktop

---

