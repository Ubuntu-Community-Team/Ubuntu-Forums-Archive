---
title: "Beryl issue with ATI X700 on Ubuntu Edgy AMD64"
date: 2007-03-19
forum: Desktop Environments
---

### Post by coosa on 2007-03-19
Dear all,
I had installed my *ATI* Driver successfully (Having *ATI Radeon X700*) on *Ubuntu Edgy AMD64 - Desktop Edition*; I have then installed *Beryl* and every thing worked just fine;
For my *ATI* Driver installation, I simply followed the walkthrough described under this link:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) while I also just followed the *Ubuntu* Guide walk through in this link for my *Beryl* Installation:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29). 
All of the sudden a couple of days later after I rebooted my PC (I removed *Eclipse* and I see no relationship, but it's the last thing I did before rebooting), *Beryl* wasn't working;
I remarked then that my *ATI* Driver has no more *direct rendering* both under my default *gnome* and my new created *xgl* desktop sessions.
So i restored back the old *xorg* drivers and reinstalled the *ATI* driver again till I had it again  working with *direct rendering* as I could verify it with the command:
```
glxinfo |grep rendering
```by getting the output:
**[color=#0000BF]direct rendering: Yes[/color]**
However, When I reinstalled *Beryl* again and created a new *xgl* session for desktop, it doesn't have a *direct rendering* any more and obviously Beryl isn't working as well!
The weird thing is that at my default *gnome* session, it has a *direct rendering*; when I log off and change my session to *xgl* and then run the same command again in my terminal under this new created *xgl* session, it states after checking for *direct rendering* that:
[b][color=#0000BF]Xlib: extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No[/color][/b]
Under the *GLX* Session; Executing:
```
glxinfo
```outputs:

[b][color=#0000BF]name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
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
OpenGL renderer string: RADEON X700
OpenGL version string: 1.2 (2.0.6334 (8.34.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon[/color][/b]

By typing in my terminal under the default *gnome* desktop ```
beryl --replace &
``` I get then:

[b][color=#0000BF][1] 6671
 **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
[/color][/b]
I recall now that under the *ATI* installation guide, changes should have been done for the *xorg.conf* file as follows:
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
``` So I wonder if there is a relationship!
After executing the command:
```
beryl --replace &
``` I get under the *xgl* session the following output:
[b][color=#0000BF]
[1] 5696
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0[/color][/b]

And once typed in the command, my panel disappears as I can't see any menus any more; so I can only open a new terminal instance from the current opened one and type in my terminal:
```
sudo shutdown -r now
```to restart!

So I'm confused; I guess that Beryl is not working under the *xgl* Session since the *direct rendering* is disabled, but why is it then enabled under my default *gnome* session?!I wonder how I could resolve this issue since every thing was just working fine and perfectly.

Attached: /var/log/Xorg.0.log

---

