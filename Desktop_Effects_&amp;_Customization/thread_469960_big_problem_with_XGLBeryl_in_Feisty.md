---
title: "big problem with XGL/Beryl in Feisty"
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by tll_2k on 2007-06-10
I'm trying to get ubuntu and beryl up and running on my brother's Acer Aspire 5050 laptop. It has an ATI Radeon Mobility X1100 graphics card. I use these guides:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

I tried using this one first, but i couldn't get my shutdown and restart buttons to show up, even with its fix:

[http://ubuntuforums.org/showthread.php?t=399643]("http://ubuntuforums.org/showthread.php?t=399643")

Whenever I first booted into the XGL session, it worked fine. After i restarted, though, it messed up. heres what it looks like:

[IMG]http://i17.photobucket.com/albums/b53/tll_2k/problem.png[/IMG]

i can boot just fine into a non xgl session, but I'd really like to have beryl working on this computer. In a non XGL session, fglrxinfo:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```
And glxinfo:

```
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

```

Someone suggested making sure the restricted drivers are enabled. When I try, I get the following error:
```
Your hardware does not need any restricted drivers.
```
But it's ATI, so it really does, right? Maybe that's the source of the problem? Any ideas?

Thanks in advance
       Tyler


P.s. For some reason, it seems that I can't get the links to those guides working. sorry... [EDIT] Nevermind. they work now.[/EDIT]

---

### Post by tll_2k on 2007-06-10
post was moved to a different forum, so bump?

---

### Post by nine01a on 2007-06-10
I have the same problem =(

---

### Post by nine01a on 2007-06-10
Mmm. I just got Beryl working. Basically, you just need to downgrade all of the Beryl components to 0.2.0 instead of 0.2.1. I did that using Synaptics and you may have to add the beryl-project repo to your /etc/apt/sources.list if you haven't already done so.

No more garbled display and it's pretty sexy.

Hope this helps

You can find a screenshot [here]("http://rootshell.be/~ngozach/beryl_demonstration.png").

---

### Post by tll_2k on 2007-06-10
I think I already did that. How can you check which version you have installed?

---

### Post by nine01a on 2007-06-10
```
sudo dpkg -l | grep beryl
``` should show you and it should look something like this: ```
nine01a@nine01a:~$ sudo dpkg -l | grep beryl
ii  beryl                                      0.2.0~0beryl1                          Compositing window manager, decorator and th
ii  beryl-core                                 0.2.0~0beryl1                          Compositing window manager - Beryl Project
ii  beryl-manager                              0.2.0~0beryl1                          Tray application launcher tool - Beryl Proje
ii  beryl-plugins                              0.2.0~0beryl1                          Collection of plugins for Beryl
ii  beryl-plugins-data                         0.2.0~0beryl1                          Plugins data - Beryl Project
ii  beryl-settings                             0.2.0~0beryl1                          Plugin and configuration tool - Beryl Projec
ii  beryl-settings-bindings                    0.2.0~0beryl1                          Plugin and configuration tool - Beryl Projec
ii  beryl-ubuntu                               0.2.1+git20070318-0ubuntu2             Simplified Plugin and configuration tool - B
ii  emerald                                    0.2.0~0beryl1                          Decorator for beryl
ii  emerald-themes                             0.2.0~0beryl1                          Package of themes for Emerald
ii  heliodor                                   0.2.0~0beryl1                          Heliodor window decorator and libraries for 
ii  libberyldecoration0                        0.2.0~0beryl1                          Settings library for plugins - Beryl Project
ii  libberylsettings0                          0.2.0~0beryl1                          Settings library for plugins - Beryl Project
ii  libberylsettings0-gconf                    0.2.0~0beryl1                          Settings library for plugins - Beryl Project
ii  libemeraldengine0                          0.2.0~0beryl1                          Decoration engines for beryl

```

---

### Post by tll_2k on 2007-06-10
yep 2.0. I just tried installing the video card drivers from ati's website. I logged in once, and it worked! but when i logged out and back in, I got the same thing again... I have run out of ideas...

---

### Post by tll_2k on 2007-06-11
anyone else have any ideas

---

### Post by scottDkoDer on 2007-07-04
OK.  I'll try to keep this short but I'm feeling a mini how-to coming on.  And I need some input.

I was trying to stream nsv, and found mplayer command-line to be the best solution.  I had beryl running with AIGLX and found the video playback to be sub-par with issues.  Wanted fglrx compiz fusion after seeing youtube vid.  So started googling and found that xgl relied heavily on xorg server and had compatibility issues with version 7.2.  Solution?  Downgrade xorg to v7.1.  

NOTE: Read all of this first and realize you can easily break your system just as you got it running.  I'm also assuming your using an ATI card with fglrx drivers working.


To do this edit your source.list file ```
sudo gedit /etc/apt/sources.list
``` and change the following line from this > deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted to this. > deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
Now update and install xorg v7.1 ```
sudo aptitude update
sudo aptitude install xorg=1:7.1.1ubuntu6
```Next follow this tutorial to install compiz [HTML]:http://ubuntuforums.org/showthread.php?t=482773[/HTML]  Even if you want to use Beryl in order to get XGL running properly (oops i mean buggily/at all).  Follow that and you should get compiz fusion running.  In order to get Beryl running it's back to your sources.list file. Comment out the "eyecandy" part and put in the stable repos > deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

Hope this helps.

Now, I got it running but a couple of issues/caveats.

CONS:

1. No buttons on panel.  Everything is fine upon start, but after starting an app there is no corresponding button in panel to minimize to.  The only way after minimize is system monitor.

2. I am using Big Desktop Dual Head Setup with res of 2048x768.  When I play any video it plays great but treats both monitors as one big screen. This may seem silly but it skews the video ratio and I can't go fullscreen on just one monitor.  Every thing maximizes to both screens.  In short, the system treats both monitors as one screen; it cannot tell where one ends and the other starts.

PROS:

1. Now I can stream nsv videos better than ever, but #2 CON remains in effect.

Any takers??

---

### Post by zero244 on 2007-07-05
There is probably something your overlooking. The previous poster is correct if you want to use XGL you need to use version 0.2.0 of beryl. Later versions dropped the xgl server.
What is in the driver line of your device section in your xorg.conf.
I bought a new nvidia card that was defective for 3D rendering. I could not get beryl to run stable at all.
I replaced the defective card with a new card and beryl has run astonishingly stable with not one problem or crash since.
So I can attest that beryl can run well.
The fact that you are missing the title bars might be fixed with a addition  to your xorg.conf file.
To get beryl running well you may have to do your homework. Some people spend 10 minutes and have it running perfectly.
Beryl for the complex amazing things it does is really pretty easy to setup and configure.
Good Luck I hope you can get it running. It does make computing more interesting.
Plus if you can get it working right its an accomplishment on your part.

---

### Post by scottDkoDer on 2007-07-05
I could go through different cards all night, but I'm trying to help the community by testing my particular system / driver / program configuration against various configurations.  I have successfully used beryl on fglrx and AIGLX within Edgy and Feisty. my Sys Conf is:

> P4 2.8 Ghz
1.0 GB RAM
ATI 9600 RADEON 256 MB

btw, What's your PC conf zero244??

---

