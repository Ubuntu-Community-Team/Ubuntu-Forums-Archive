---
title: "[SOLVED] Compiz-fusion/Beryl session really messed up (visually)"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by mahasmb on 2007-08-23
I haven't found anyone else on the forums with my problem... so here it is.

I use a separate session (LUCKILY) to use Beryl and Compiz-fusion. After installing some Compiz-fusion updates, and logging into that session my whole screen looked... well really messed up. **The screen is really blurry with the pixels arranged in a way making it impossible for me to read anything.** It's impossible to use like this. But... if I know exactly where everything is I can somehow find the restart button to logout and restart etc. I wish I could take a picture but I can't.

Anyone have any idea how to fix this?

---

### Post by mahasmb on 2007-08-23
I was able to take a few pictures. Here's one. All seems to work fine... It's just that I can barely see the screen properly. Also, that dialog box keeps on popping up no matter what session I'm in. What's the best choice for it?

I'm currently on my Xclient session (I think that's what it's called), the session that's messed up is my XGL-Beryl session that I created to test out Beryl and Compiz-fusion on.

---

### Post by EXCiD3 on 2007-08-24
My friend just had that problem a while ago. He recommended double checking you graphics card drivers are installed correctly. He was using an ATI card at the time, which could be the problem.

---

### Post by mahasmb on 2007-08-24
How would I do that?

---

### Post by mahasmb on 2007-08-24
How do I double check that my video card drivers are installed corectly???

---

### Post by mysticmatrix on 2007-08-24
Login to a normal gnome session
Then post the output of following commands;

```
lspci
```
and
```
glxinfo
```

---

### Post by mahasmb on 2007-08-24
Thank you!

Here it is.


```
maha@maha-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
0a:00.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0a:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0a:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
maha@maha-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
maha@maha-laptop:~$ 

```

---

### Post by mysticmatrix on 2007-08-25
You don't have your graphics drivers installed. Use this thread to install them
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by mahasmb on 2007-08-25
I LOVE this place!

MysticMatrix, you rock. Problem fixed

I swear, getting useful help for Windows XP problems is so very hard to do no matter what forums I sign up for and no matter how much money and time I waste.

---

