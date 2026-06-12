---
title: "3ddesktop, beryl, and other meanderings"
date: 2007-06-17
forum: Desktop Effects &amp; Customization
---

### Post by pardesi on 2007-06-17
how can i increase  the size of the windows when i use 3-d desktop

---

### Post by mahiyar on 2007-06-17
Beryl settings manager > Visualization > 3D effects play around with the settings there (if i remember there is something like windows width)

---

### Post by pardesi on 2007-06-17
thanks but i don't have beryl installed it is with the "3d-Desktop" the old one.....:(

---

### Post by mahiyar on 2007-06-17
Sorry mate cant help you there.

---

### Post by ruscoe on 2007-06-17
Are you using the 3D Desktop package from Synaptic? If I remember, that's a program that takes a static shot of each of your workspaces and lets you rotate them in a "carousel" layout when you run it. It isn't a compositing window manger like Beryl.

In Terminal, run 3ddesktop -h

It'll give you a list of options you can run 3D Desktop with. One of them allows you to activate the carousel layout without zooming out. I think this is what you mean by making the windows appear bigger.

---

### Post by eoghanmurray on 2007-06-17
If you have simply enabled Desktop Effects in Feisty Fawn, you won't be able to change the settings. I recommend you install Beryl, which has far more settings and effects.

The following guide is from [http://www.ubuntuguide.org](http://www.ubuntuguide.org).

**If you have an ATi Graphics Card:**
Step 1 : Edit your sources.list file adding
Type the following to enter your sources.list file:
```
sudo gedit /etc/apt/sources.list
```

Add to the file:
```
deb http://ubuntu.beryl-project.org feisty main 
```

to the bottom of it.
Then save the file and exit text editor.

Step 2 : Add the GPG key. Open terminal and type

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add - 
```

Step 3 :

```
sudo apt-get update
```

Step 4 :

```
cp -p /etc/X11/xorg.conf /etc/X11/xorgold.conf
sudo gedit /etc/X11/xorg.conf 
```

(Note any changes so you can revert back if needed).

Under Section "Module", make sure that the following lines are included, and add them if they are not:

```
Load "dri"
Load "vbe"
Load "glx"
```

Also ensure the bottom of the file has:
```

Section "DRI"
 Mode 0666
EndSection

```
Step 5 : Reboot the system (Please don't restart only X. I had odd things happen to me when I skipped rebooting until my next proper restart).

Step 6 : In a terminal:

```
sudo apt-get install beryl
```

Step 7 : type into terminal

```
beryl-manager --no-force-window-manager
```

(this will start beryl but wont activate it yet).

Step 8 : Right click on the diamond near the clock - select advanced beryl options and change the window manager to metacity(GNOME) also change rendering path to copy. Also under advanced change rendering platform to force AIGLX.

Step 9 : Right click the diamond again. This time - select window manager - Beryl.

If it all works and you can spin the cube ok etc. you can try changing the rendering path back to automatic. If it all freaks out just reboot and start beryl again with:

```
beryl-manager --no-force-window-manager
```

Step 10 : Assuming it all worked ok you need beryl to start automatically on boot : Click System-Preferences-sessions. Click add and type

```
beryl-manager
```

Now reboot - beryl should all be sweet. 

-----------------------------------------------

**If you have a Nvidea Graphics Card**

    * Ensure all packages up to date 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

    * Back up xorg.conf 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
gksudo gedit /etc/X11/xorg.conf
```

    * Install Nvidia Driver for Graphics Card*
          o System -> Administration -> Restricted Driver Manager 

Enable Nvidia Drivers

Restart X-Windows and confirm Nvidia Drivers are working correctly

    * Install Beryl 

```
sudo apt-get install beryl emerald-themes beryl-manager
```

    * Start Beryl 

```
beryl-manager
```

    * Start Emerald (if it doesn't start on its own) 

```
emerald --replace
```

    * Have Beryl and Emerald load on login
          o System -> Preferences -> Sessions
          o Startup Programs -> New 

```
beryl-manager
```

and

```
emerald --replace
```

    *
          o If, on reboot, program menus aren't displaying in the correct layer (you can't see them when you select them because they are displaying behind the window) then right click on the 'Beryl Manager' icon in the panel (the red gem icon) and select 'Reload Window Manager'. The problem should be solved the next time you reboot. 

    *
          o If when you start Beryl you find your windows have no title bar (with the minimise, maximise and close buttons) or borders, you may need to add the following line to the device section of the file /etc/X11/xorg.conf (See this page [http://forum.beryl-project.org/viewtopic.php?f=35&t=1631](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631) for details): 
```

Option "AddARGBGLXVisuals" "True"
```

and change to

DefaultDepth 24  

in the "Screen" section.

Also if you are using a NVIDIA GeForceGo graphics card you may also need to add

```
Option "DisableGLXRootClipping" "True"
```

in the device section of your xorg.conf

If that still doesn't help you then right click on the beryl diamond icon by the clock and select advanced beryl options-rendering platform and choose "force AIGLX"

This should get everything going.

---

### Post by pardesi on 2007-06-17
thansk and yes i have ATI graphics card but what is "add the GPG key" in step 2

also is it safe to use beryl i have
ATI 200 radeon series
1 GB RAM

also i raed somwhere that a change in settings is need for beryl after each kernel update otherwise the sysytem crashes....i am a noob help me out

---

### Post by pardesi on 2007-06-17
also i am unable to use desktop effects in ubuntu although i have installed the restricted drivers so is it safe for me to proceed

---

### Post by eoghanmurray on 2007-06-17
It's fine to run Beryl with as little as 128MB RAM and still get good results (10fps plus). The graphics card is fine, and you need a 400MHz processor or higher to practcally use Beryl (Pentium 2 or higher).

Enjoy!

Here's a picture of my PC running it (I'm on a 7 year old laptop: desktop PC motherboard gone lol) That shows you can run it on anything basically.

---

### Post by pardesi on 2007-06-17
that was more tahn inspiring let's do it...:p:p:p

---

### Post by eoghanmurray on 2007-06-17
lol it takes under 10 mins including reboots.

---

### Post by pardesi on 2007-06-17
also what is GDG key in your second line icouldn't understand

---

### Post by eoghanmurray on 2007-06-17
Doesn't matter about that. All you need to do is type wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add - into a terminal and press ENTER. That'll do it. I got the guide from a forum on the Internet. ([www.ubuntuguide.org](www.ubuntuguide.org))

---

### Post by pardesi on 2007-06-17
thanks i will keep u posted

---

### Post by pardesi on 2007-06-17
no it shows the following error
```
pardesi@pardesi-desktop:~$ wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
--01:50:10--  http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
           => `-'
Resolving ubuntu.beryl-project.org... 80.77.247.17, 82.140.42.54, 88.191.250.18, ...
Connecting to ubuntu.beryl-project.org|80.77.247.17|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
01:50:11 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.

```

---

### Post by eoghanmurray on 2007-06-17
Well, I get this:

ME@******************:~$ wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
--21:23:46--  [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)
           => `-'
Resolving ubuntu.beryl-project.org... 88.191.250.18
Connecting to ubuntu.beryl-project.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,415 (2.4K) [application/x-troff-me]

100%[====================================>] 2,415         --.--K/s             

21:23:46 (668.28 KB/s) - `-' saved [2415/2415]

OK

Make sure you copy and paste ONLY, and ALL OF this:
```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

---

### Post by pardesi on 2007-06-17
you mean only the code or the entire text leaving your instructions

---

### Post by eoghanmurray on 2007-06-17
wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -


Just that, not this sentence.

---

### Post by pardesi on 2007-06-17
wel the computer shows this now
```
pardesi@pardesi-desktop:~$ cp -p /etc/X11/xorg.conf /etc/X11/xorgold.conf
cp: cannot create regular file `/etc/X11/xorgold.conf': Permission denied

```

---

### Post by eoghanmurray on 2007-06-17
Nothing wrong with that, Proceed with the installation. That happened with me too and it went perfectly after that. It has absolutely not effect.

---

### Post by pardesi on 2007-06-17
also please check what your composite value is when u give the code

```
sudo gedit /etc/X11/xorg.conf
```
 towards the end

mine is "0"

---

### Post by pardesi on 2007-06-17
hey i am:( waiting

---

### Post by eoghanmurray on 2007-06-17
I can't reply right now as my battery is about to die - and text editor has been forced to quit, so won't start up again. I'll post in the morning.

Good luck. Keep trying.

---

### Post by pardesi on 2007-06-17
ok thanks ....will see tomorrow

---

### Post by eoghanmurray on 2007-06-18
OK I'm back ask away.

---

### Post by pardesi on 2007-06-18
hi everything turned out to be ...
i could do nothing
the following error came

```
pardesi@pardesi-desktop:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```
here check my

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)
```

```
pardesi@pardesi-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)
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
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_ATI_vertex_streams, 
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

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
```

```
xorg.conf
```

```
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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
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
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "StudioWorks"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RC410 [Radeon Xpress 200]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RC410 [Radeon Xpress 200]"
	Monitor    "StudioWorks"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection
```
help well what card are u using and what's ur composite

---

### Post by eoghanmurray on 2007-06-18
```
Section "Extensions"
	Option	    "Composite" "0"
EndSection
```

Remove that and save. The last lines of that file should read:

```
Section "DRI"
	Mode	0666
EndSection
```

The rest of your ifles are OK as far as I can tell.

---

### Post by pardesi on 2007-06-18
so should i repeat the process of installation all again as i had removed beryl...or should i start from somewhere middle

---

### Post by eoghanmurray on 2007-06-18
restart the installation again - see [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29) for more.

---

### Post by eoghanmurray on 2007-06-18
Are you doing it?

---

### Post by pardesi on 2007-06-18
yes just finished now with the second option loaded witha  xgl session evrything was blurred...let me see

---

### Post by eoghanmurray on 2007-06-19
OK - if you've got it all running that's OK. If you don't have it running, tell me. If it's all blurred, it might be a glitch with the blur effect - login as your user account in Failsafe GNOME ( it happened to me too and this worked) - and go to Beryl Manager (Applications > System Tools > Beryl Manager) - go to the Visual Effects tab and uncheck the Blur Effect checkbox.

Good luck! ;)

---

### Post by pardesi on 2007-06-19
yes let me see

---

### Post by pardesi on 2007-06-19
hey i did it but unable to view any 3D effects...will try doing somethin

---

### Post by pardesi on 2007-06-20
yse got wobbly windows the desktop rotates while switching workspaces ...dissolving windows..
:p:p
but how did u acheive the state in the phot u sent me...i seee all my shotcuts disbled...

also any beautifying tips

---

### Post by eoghanmurray on 2007-06-21
Sorry I haven't been on lately - had a power cut due to maintenance by NIE (Ireland Electrical Grid thing) - anyway...

Good that you got it running. You'll never go back to 2D.
When you say about getting to my state in my screenshot. I'll go through the steps to get it transparent etc.

<**These steps assume you have the default layout (bar at top, bar at bottom, menu at top left etc**>
1 - Right click the Beryl manager icon (in the system tray), and select 'Beryl Settings Manager'.

2 - Click the tab labelled 'Desktop' at the top of the window.

3 - Select 'Desktop Cube' - make sure the checkbox is checked.

**We are going to make the cube transparent.**
a - Click the transparency tab.
b - Check the 'Transparent Cube' checkbox.
c - Set the transparency for the cube moving, and when it is stationary. (I have it set to 60% for in motion ans 97% for stationary)
d - Press Ctrl+Alt+Left Mouse Button to see the transparent cube.

**We are going to set the backdrop (skydome) - in the screenshot, it is an image of space.**
a - Click the 'Skydome' tab.
b - Check the 'Skydome' and 'Animate Skydome' checkboxes.
c - Download this image: [http://www.kepu.gov.cn/zlg/yuzhou/images/m-xilie/m91.jpg]("http://www.kepu.gov.cn/zlg/yuzhou/images/m-xilie/m91.jpg")
d - In Beryl Settings manager, navigate to this image using the 'Skydome Image' field.
e - Click 'Open'.
f - Click Ctrl+Alt+Left Mouse Button to see the space image and move the cube to see it move.

**We are going to make the windows stand out from the cube.**
a - In the top tab menu, select 'Visual Effects'
b - Check the 3D effects checkbox.
c - Press Ctrl+Alt+Left Mouse Button to see the 3D effects.

**To customize the close/open animations, and ones for minimize etc, go to Visual Effects, and click 'Animations', and customize the options there.**

Enjoy! :D

---

### Post by pardesi on 2007-06-22
thanks u were brilliant...all along helping,..=D>=D>:-({|=..probably u were more interseted on me having beryl than i was;)

but,
what do you mean when u say windows stand out from a cube ...
do u mean floating windows
i see no change when that is checked and when that is not checked(3d desktop)

how do you float your cube with skydome in the background..like those in the screenshots...
i want my cube to be smalll so that my background is the skydome image and i have the cube in front of me andd can see all sides of cube they have been made transparent and when i click on a cube's side that side rotates and comes...i sthat possible

---

### Post by eoghanmurray on 2007-06-22
OK - deal with floating cube first. This will get the cube smaller and will allow you to see the skydome more clearly.
<I assume you have already followed my previous instructions to make the cube transparent and make the skydome image.>

1 - Open Beryl Settings Manager
2 - Select the 'Deskop' tab at the top.
3 - Select 'Rotate Cube' in the list to the left. (Make sure box is checked)
4 - Expand the 'General' list (click it)
5 - Go to the 'Zoom' parameter, and drag it to the maximum setting (which is 15).
6 - Click Ctrl+Alt+Left mouse button to see the cube further out.

To make to windows stand out from the cube on rotate:

1 - Go to the 'Visual Effects' tab at the top of BSM.
2 - Click '3D Effects' in the left menu.
3 - Set the following parameters:
Space Between Windows: 0.0400
3D Animation Speed: 0.0050
Window Width: 0.2900
Enable Window Depth: Unchecked

You can tweak these to suit your liking, but these are my perfect settings.
[COLOR="Red"][I]
**Top Tip**
To keep the cube zoomed-out without holding the left mouse button, click Ctrl+Alt+Middle Mouse Button, which will allow you to see the cube and let go of the mouse. Useful for a unique screensaver.[/I][/COLOR]

---

### Post by pardesi on 2007-06-23
brilliant everything's gotten do well:p:p
well is it possible to have 3-d windows like in vista without rotating the cube

---

### Post by eoghanmurray on 2007-06-23
Well, yes. But not in the Flip-3D way like Vista, because Micro$oft would sue Ubuntu and Canonical for all it's got and more.
However, if you click 'Alt+TAB', you see the window switcher like normal.
Now, press 'WindowsKey+TAB'. Now you see your windows rotating in a circle. Open several windows to do this.

Also, jam your mouse into the top right corner of the screen - all your windows float into the centre, (not minimized ones), and allow you to choose.

**The tricks above need several windows to look good.**

---

### Post by eoghanmurray on 2007-06-23
Actually, I think you might like to see some new effects - they are a beta-y thing, so might not work on all PCs, but they're fine on mine.

Go to **System > Administration > Synaptic Package Manager**.
Click on the list to the right side.
Type:
```
beryl-plugins-unsupported
```

A rectangle should be selected.To the right it should say 'Collection of extra plugins for beryl'.
To the bottom, it should say:
```
Collection of extra plugins for Beryl
The Beryl Project brings 3D desktop visual effects that improve
usability of the X Window System and provide increased productivity
though plugins and themes contributed by the community giving a
rich desktop experience.

The plugins in this package are supported by the Beryl Project,
but are not considered stable enough to go into the main
beryl-plugins package. Only install these plugins if you don't
mind some additional instability.
```

Right click the checkbox which is a white colour (you will notice some are green) - and select 'Mark for Installation'. Now, click Ok to all prompts, and click the **Apply** button to the top of the page.

---

### Post by pardesi on 2007-06-23
how is that u keep on beautifying my desktop....:D
the zoom in pluginn is great well don't emrald themes provide u with icons...?

---

### Post by eoghanmurray on 2007-06-23
You mean WinKey+Scroll? It is good.
Assuming, you have Emerald Themer installed (emerald-themes), you can add themes. If you get this file:
[http://themes.beryl-project.org/download.php?id=78]("http://themes.beryl-project.org/download.php?id=78")
you get a vista-like theme. It's called Vista-ish and should open automatically in Emerald. Emerald doesn't handle icons, but if you go to [http://www.gnome-look.org]("http://www.gnome-look.org"), you can get good icon sets.

Enjoy!

---

### Post by pardesi on 2007-06-23
brilliant i think we  have discussed so much about beryl right from the basics of installation to beautification....i think this should be a really good tutorial how to what to and what not to while using beryl...
also it gives u all problems..
wonderful:rolleyes::mrgreen:
so brilliant job everything is fine hope to have more of you
=D>=D>

---

### Post by pardesi on 2007-06-24
here's a screenshot of mine desktop cube

---

### Post by eoghanmurray on 2007-06-24
That looks good. One tip though, if you disable the cube caps you can see more, and I think it looks cleaner.

**How to Disable Cube Caps**
1 - Open Beryl Settings Manager
2 - Click 'Desktop' in the top tab menu.
3 - Click 'Desktop Cube' in the selection menu to the left.
4 - In the area to the right, select the 'Caps' tab.
5 - Deselect the 'Draw Caps' checkbox.
This will disable the desktop caps.

**How to change the caps image**
In the same area, and in the box that allows you to select multiple items, which is labbelled Image Files on Top, delete the option there and add your own custom image by the browse command.
Do the same for the bottom of the cube.

To make the images perfectly fit the cube, select 'Scale Images on (Top/Bottom).

---

### Post by eoghanmurray on 2007-06-24
**What I've Done with my Desktop**
This is my desktop, with every effect I can think of enabled.

- It's snowing. (WinKey+F3)*
- It's raining on the cube. (Shift+F9)
- Mozilla Firefox is in the negative. (Winkey+n) (or WinKey+m for whole screen)
- Desktop cube is zoomed out.
- Emerald Themes are enabled and Vista-ish is loaded.

*Requires the 'beryl-plugins-unsupported' package.

---

### Post by pardesi on 2007-06-24
everything except rain is perfect ...
when rain is switched on computer becomes sluggish though it rains and the skydome becomes white rest all working greta..cheers beryl cheers ubuntu...cheers eoghanmurray..
:D:D

but once i download vista-ish how do i apply it i already have my decoratorar as  emrald

thanks for those cube caps ....they really made the situation messy

---

### Post by eoghanmurray on 2007-06-24
Yeah, once your graphics card is overpowered it may blank out some features, and your one isn't terrifically powerful.
OK. Downloading Emerald themes is very easy.
[http://themes.beryl-project.org/download.php?id=78]("http://themes.beryl-project.org/download.php?id=78")
Click that link, and select 'Open with Emerald Theme Manager (default)'.
The file will download, and you will see Emerald Theme manager. Scroll to the bottom of the window, and click 'Vista-ish'. That should apply it.

Alternately, save it to disk, open ETM, and drag it into the window.

---

### Post by eoghanmurray on 2007-06-24
I assume you know how to shade a window smoothly with Beryl?

Just scroll on the title bar of the window.

My name's Eoghan Murray btw (it's irish lol) and hence my username.

---

### Post by bodhi.zazen on 2007-06-24
Since this thread morphed from a discussion of 3ddesktop to beryl I moved it.

Enjoy !

---

### Post by eoghanmurray on 2007-06-24
no problem - it's OK. Do I need to re-bookmark.

lol btw I just got IE7 working on my Windows machine to test my website on. they spent $20,000,000 on that!!!

---

### Post by pardesi on 2007-06-24
shading is great where did u get thsi all...
but that emerald is just not giving up when i open it with emerald theme manager  the style dosen't show up at  all do i have to open any repository to allow this to happen

---

### Post by eoghanmurray on 2007-06-24
You don't need repositories - are you ure that when you scroll down to the bottom of the Emerald window it's not there?

---

### Post by eoghanmurray on 2007-06-24
You should see this: it's so you can run Windows under Ubuntu - it works with Beryl too. I've got it running on one side of my cube.

Edit: soz, forgot link
[http://ubuntuforums.org/showthread.php?t=433359&highlight=flash+pro+8](http://ubuntuforums.org/showthread.php?t=433359&highlight=flash+pro+8)

---

### Post by pardesi on 2007-06-25
thanks for the site ...but will try later because i dual boot XP-ubuntu:(

yes i don't get vista-ish when i scroll down:(

so r you able to get beryl in windows....

---

### Post by pardesi on 2007-06-25
i just go the sun solaris 10 cd i had ordered (it's free) thinking of installing that on VM ware;)

---

### Post by eoghanmurray on 2007-06-25
You can sort of get 'Beryl' on Windows XP. For the Cube (albeit very basic - no multiple desktops - just four  - clones on each side of the cube) - and you can not see the top of the cube. No transparency. No live display - freezes the display before rotating. 

It's called Yodm3D.
[http://yodm-3d.uptodown.com/en/](http://yodm-3d.uptodown.com/en/)

That's all I can think of. It's terrible, but if you really want it you could try it.

You should see this: It lets you run Windows under Ubuntu - run all your apps:

[http://ubuntuforums.org/showthread.php?t=433359&highlight=flash+pro+8](http://ubuntuforums.org/showthread.php?t=433359&highlight=flash+pro+8)

Have fun! :p

---

### Post by pardesi on 2007-06-25
yse VM Ware mat try this but is of not that much of use to me as anyway i dual boot...
sun solaris runs on virtual station may also try that it is  really a very advanced OS...:D

---

### Post by smayoye on 2007-06-25
Hey am new in this forum, how do I post a new topic??

---

### Post by bodhi.zazen on 2007-06-25
> **smayoye said:**
> Hey am new in this forum, how do I post a new topic??

Welcome to Ubuntu :)

[list=number][*]Log-in[*]Go to the forum where you want to start a new thread (Absolute Beginner Talk ?)[*]Click on the "Make New Post" button on the bottom left[*]Fill out title ...[/list]

---

### Post by pardesi on 2007-06-25
> **smayoye said:**
> Hey am new in this forum, how do I post a new topic??

yet another so called "off topic" discussion we are meandering more than...;)

---

