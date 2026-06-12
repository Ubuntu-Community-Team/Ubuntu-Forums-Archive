---
title: "3D Accel or not?"
date: 2006-11-05
forum: Gaming &amp; Leisure
---

### Post by Fittersman on 2006-11-05
how do i know if my 3D accelleration is enabled or not?

---

### Post by John.Michael.Kane on 2006-11-05
You can try running:
```
glxinfo
```

You should see **direct rendering: Yes**

Also might help if you told us your hardware spec's.

---

### Post by Liz on 2006-11-06
mines not working. 
i have a NV11DDR [GeForce2 MX 100 DDR/200

i used the this link ([https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper))
and did the first method, but that didnt work. it crashed my x till i removed it and made a clean copy. 

ive tried the one from the cdrom, and that didnt work either. which is why i found this link and did method one. 

anyone else get this card working? or would it be recommended that i upgrade?

---

### Post by Fittersman on 2006-11-06
```
cleippi@FamilyComputer:~$ glxinfo
name of display: :20.0
Xlib:  extension "XFree86-DRI" missing on display ":20.0".
display: :20  screen: 0
**direct rendering: No**
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

```

that is what i get when i type that in, how do i change it do it is direct rendering: yes?

---

### Post by CatKiller on 2006-11-07
> **Fittersman said:**
> that is what i get when i type that in, how do i change it do it is direct rendering: yes?

Install the appropriate drivers for your graphics card.

---

### Post by CatKiller on 2006-11-07
> **Liz said:**
> mines not working. 
i have a NV11DDR [GeForce2 MX 100 DDR/200

i used the this link ([https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper))
and did the first method, but that didnt work. it crashed my x till i removed it and made a clean copy.

This worked first time on my friend's computer, that has that graphics card:

**Install the driver**: Open Synaptic and select the nvidia-glx-legacy package for installation. Click apply.

**Enable the driver**: Use ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``` to make a backup of your xorg.conf file and then open it for editing. Find the **Driver** line in the **"Device"** section and change it to **Driver     "nvidia"**. Save and close GEdit.

**Restart X** with **Ctrl-Alt-Backspace**.

Given that you're claiming to not be running Dapper Drake (6.06 LTS), should you be following instructions that say > <!> This guide works ONLY on Ubuntu Dapper Drake 6.06 LTS?

---

### Post by Fittersman on 2006-11-07
"Install the appropriate drivers for your graphics card."


where and how?

---

### Post by WhiteDawn on 2006-11-07
> **Fittersman said:**
> "Install the appropriate drivers for your graphics card."


where and how?

if you have a nvidia card 
```

sudo apt-get install nvidia-glx

```
should work, after doing so change the xorg config so that driver says nvidia, instead of nv
xorg config is located in /etc/X11/xorg.conf
if lazy, typing this should alow you to easly edit it
```

sudo gedit /etc/X11/xorg.conf

```
but i am baisicly repeating what the above guy sayed....

---

### Post by Fittersman on 2006-11-07
i have a radeon 7500

---

### Post by CatKiller on 2006-11-07
> **Fittersman said:**
> i have a radeon 7500

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Fittersman on 2006-11-07
k i went there and followed the directions but ubuntu keeps trying to use the crappy intel video card instead of my radeon one i think how can i make it use the radeon one??

---

### Post by CatKiller on 2006-11-07
> **Fittersman said:**
> k i went there and followed the directions but ubuntu keeps trying to use the crappy intel video card instead of my radeon one i think how can i make it use the radeon one??

Use the appropriate BusID for your Radeon in your xorg.conf. For example, PCI:1:0:0 is common for an AGP card. **lspci | grep VGA** should tell you what the BusIDs are for each of your adaptors, but you'll possibly have to convert the values from hexadecimal to decimal. There may be a command to tell you the BusID directly in a form that xorg.conf will understand, but I don't know what it is.

Or you could disable the onboard graphics in your motherboard's BIOS if you don't use it for anything.

---

### Post by Fittersman on 2006-11-07
well previously i have done alot of editing to the xorg.conf file to get my system to work and i beleive it is working off the radeon card because i have the bus id specified but for some reason it never shows up in the list, only my other card shows up and im using the vesa command in the driver spot (i beleive this is why the 3d acceleration doesnt work)

```
Section "Device"
        Identifier      "RADEON 7500 SERIES"
        Driver          "vesa"
        BusID           "PCI:1:9:0"
EndSection

```

how can i get the 3d acceleration to work on ubuntu?

---

### Post by CatKiller on 2006-11-07
If you mean that it doesn't show up in the **dpkg-reconfigure xserver-xorg** tool, I think it only shows you the primary card - it can't really handle more than one, so it picks the one that your motherboard likes more.

The VESA driver will not give you 3D acceleration. You should (I think) be able to change the Driver line to "ati" to have it pick the most appropriate open source driver for your Ati card.

---

### Post by Fittersman on 2006-11-08
when i type in glxinfo now i get a different response but direct rendering is still a no (after i changed vesa to ati)


```
cleippi@FamilyComputer:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow

```

---

### Post by CatKiller on 2006-11-08
> **Fittersman said:**
> when i type in glxinfo now i get a different response but direct rendering is still a no (after i changed vesa to ati)

I've not used the ati driver, so I can't give you specific advice. You say you've modified your xorg.conf - you could either do a ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure it with more default settings. Or you could manually edit it some more. If I was forced to speculate, I'd suggest that you make sure that all the appropriate modules are being loaded - in particular the **dbe** and **dri** modules.

**man radeon** and the [DRI Wiki]("http://dri.freedesktop.org/wiki/") may tell you more, or they may not. I can't really help you more than that, I'm afraid.

---

### Post by Liz on 2006-11-09
[QUOTE=CatKiller;1727434]This worked first time on my friend's computer, that has that graphics card:

**Install the driver**: Open Synaptic and select the nvidia-glx-legacy package for installation. Click apply.

**Enable the driver**: Use ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``` to make a backup of your xorg.conf file and then open it for editing. Find the **Driver** line in the **"Device"** section and change it to **Driver     "nvidia"**. Save and close GEdit.

i am running dapper 6.06 lts. 
and it still didnt work. crashed x till i reconfigured xorg.conf

did it twice just in case i did something wrong the first time.

good news !!!
i didnt have universe enabled in synaptic, so when i did, it upgraded the correct files that i needed to enable my card to work. have been playing wow for the last few days now without a problem. 
im so please :D

---

