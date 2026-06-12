---
title: "Gutsy, Xgl and ATI fglrx"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by michael37 on 2007-10-07
I had a fairly decently working Feisty setup, but upgrade to Gutsy broke a lot of things...   Compiz doesn't work, and even gnome session do not load right.

With the new Xgl, it starts by default.  The new control scripts are in /usr/share/xserver-xgl

As a result, I get two X sessions (as expected, Xorg on :0 and Xgl on :1)

However, my glxinfo looks outright wierd.  What does it mean??

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6473 (8.37.6))


Well, if you wanna see the full set, check this out:
$ glxinfo -display :0
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
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)


$ glxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
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
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6473 (8.37.6))

---

### Post by ruscoe on 2007-10-07
Not meant to derail the thread, but does anybody know when we're likely to see AIGLX support in the fglrx driver?

I heard it was coming up towards the end of this year and I would prefer it over using XGL.

---

### Post by Alexander Heß on 2007-10-07
AIGLX support is supposed to be included in the 8.42 release which should come this month. That is if they don't screw up their &#8220;one release per month&#8221; schedule.

---

### Post by ruscoe on 2007-10-07
Fingers crossed then. Thanks for the info.

---

### Post by michael37 on 2007-10-07
Woohoo!!! I just got it working... gonna work on writing a quick HOWTO.

I gotta tell ya, it probably is not that hard if you have a brand new Gutsy install.  If you have had working fglrx+Xgl config in Feisty, you need to find and backrev nearly all the changes MANUALLY before anything works.

---

### Post by Aramil Moonmist on 2007-10-15
link to the how to plz?

---

### Post by michael37 on 2007-10-16
Well, let's try here and see if I can help you... If yes, I will create a Wiki page.

[SIZE="7"]Before we begin -- supported hardware list[/SIZE]

*Taken from fglrx driver description for Gutsy.*

This version of the ATI driver officially supports:

 * FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400,
           V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128,
           X1-128, X1-256p
 * FireMV: 2200 (Single card PCI-e configuration)
 * Mobility FireGL: V5000, T2
 * Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300,
                    9800, 9600, 9550, 9500
 * Radeon Xpress: 200M series, 1250 IGP, 200 series
 * Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550,
           X300, 9800, 9700, 9600, 9550, 9500

ATI All-in-Wonder variants of the above cards/chips are also supported,
but video capture is not.

[SIZE="7"]If you are doing fresh install of Gutsy[/SIZE]

[LIST=1]
[*]Enable fgrlx driver.

Install linux-restricted-modules and restricted-manager provied in the restricted repositories:
```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". 

[*]Install xserver-xgl package
```
sudo apt-get install xserver-xgl
```
[*]Install compiz
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
```
[*]Reboot
[*]Log in.  3D effects should be enabled!
[*]Customize Compiz Fusion.
Select System &#8594; Preferences &#8594; Advanced Desktop Effects Settings
In the new window, General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size.  Set it to 4.
The other two options have to be left at 1.

Continue customization per Forlong's guide at [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

[/LIST]

---

### Post by michael37 on 2007-10-17
[SIZE="7"]If you are upgrading from Feisty 7.04 or earlier versions and you have run Xgl before.[/SIZE]

When upgrading, you may experience blank screen, a screen with no windows and toolbars, a screen with only a background, or any other mess.  It is caused by the customized scripts for Xgl which do not work with Gutsy.  So, we need to clean up.

If you really can't log into a working X session and open a terminal, simply press "Ctrl-Alt-F1" to get into the text prompt and follow the removal steps (1-4) from the text interface.  After a reboot, the graphics should work better.

[LIST=1]
[*]Remove compiz
```

sudo echo "activate sudo"
sudo apt-get --purge remove compiz*
sudo apt-get --purge remove libcompiz*
sudo apt-get --purge remove libdecoration0
sudo apt-get --purge remove compizconfig-settings-manager 
sudo apt-get --purge remove python-compizconfig

```
[*]Remove Xgl
```

sudo apt-get --purge remove xserver-xgl

```
[*]Clean up
```

sudo apt-get autoremove

```
[*]Remove customizations
```

rm -rf ~/.compiz
rm -rf ~/.config/compiz
rm -rf ~/.gconf/apps/compiz
sudo rm -i /usr/local/bin/startxgl.sh
sudo rm -i /usr/share/xsessions/xgl.desktop

```
When asked to remove the files, type YES.  If the files were present and you removed them, proceed to the next item.  Otherwise, undo customizations to /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom that you have made from [ this section of the guide](https://help.ubuntu.com/community/CompositeManager/Xgl#head-0e4ffce2a76cdb03b8dbd57642f13fac385afef0)
[*]Reboot
[*]Login back in and find yourself in a 3D effect devoid session.  You may not even be running a windows manager.  If you can't move windows and don't see window decorations, press "Alt-F2" and type ```
metacity --replace
```
[*]Verify that everything else is working properly, e.g. Firefox opens, Wired and/or Wireless Network connects, etc.  This is the best time to troubleshoot everything else until we enable 3D effects.
[*]Enable fgrlx driver.

Install linux-restricted-modules and restricted-manager provided in the restricted repositories:
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver".
[*]Reboot if necessary.
[*]After reboot, log back in.
Open terminal and run
```

fglrxinfo -display :0

```
and verify that you see something like this:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

```
[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/attention.png[/IMG]If you don't have command fglrxinfo, you either don't have a supported ATI card or you missed a step or two.  Go back through all steps.  
[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/attention.png[/IMG]If you see "Mesa GLX Indirect" instead of "ATI Technologies", see Troubleshooting section below. If still unsure, post your /etc/X11/xorg.conf in this thread.  **DO NOT CONTINUE INSTALLATION UNTIL YOU FIX THIS ISSUE AND GET RID OF MESA.**
[*]=================================
[*]Are you ready to get back into the wobbly windows and Desktop Cube?
[*]=================================
[*]Install Xgl.
```
sudo apt-get install xserver-xgl
```
[*]Install compiz
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0

```
[*] Reboot
[*] Log in. 3D effects should be enabled!  You no longer need to select a special Xgl session.
[*]Customize Compiz Fusion.
Select **System &#8594; Preferences &#8594; Advanced Desktop Effects Settings**
In the new window,** General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size**.  Set it to **4**.
The other two options have to be left at **1**.

Continue customization per Forlong's guide at [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)
[/LIST]

[SIZE="4"]Troubleshooting[/SIZE]

[SIZE="3"]**Solving the 'Mesa nightmares' mystery.  This is becoming a hot topic in this guide.**[/size]

A common problem in step 10 is fgrlxinfo output like this:
```

# fglrxinfo -display :0
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```.
That means you are not using the restricted driver.  Enable it via Restricted Driver Manager -- see step 8.  Just in case, run command 
```

sudo aticonfig --initial

```
then reboot.
-----------
More Mesa troubleshooting.  Some people reported broken drivers.  This has nothing to do with compiz or Xgl -- it's a matter of having a broken driver installed.  Technically speaking, there are two drivers for the video card.  One driver is a part of the kernel, and one driver is for X.  They need to both work and match.

* **Kernel driver**

Verify that the most recent kernel is installed:
```

uname -r

```
should **2.6.22-14-generic**
and both packages are installed:
```

dpkg -l linux-restricted-modules-2.6.22-14-generic
dpkg -l linux-image-2.6.22-14-generic

```

Check if your kernel module is loaded:
```

lsmod | grep fglrx

```
should return something like: 
fglrx                 765588  51 

You can also check if you are using the right version of the kernel driver:
```

modinfo fglrx

```
should return something like this:
[indent]
filename:       /lib/modules/2.6.22-14-generic/volatile/fglrx.ko
depends:        agpgart
vermagic:       2.6.22-14-generic SMP mod_unload 586 
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
parm:           firegl:charp
[/indent]

If you don't have fglrx kernel module loaded, please report the problem in this thread.  I don't have generic instructions for you yet.

If you are running a wrong version of kernel, your install may have a bigger issue than non-working 3D effects.  Please address those issues first.

* **X driver**

See if your X driver is installed 
```

dpkg -l xorg-driver-fglrx

```
You should have version 7.1.0-8.37.6+2.6.22.4-14.9 installed.  If you got something else, I recommend to uninstall it and reinstall it:
Typical output is:
ii  xorg-driver-fg 7.1.0-8.37.6+2 Video driver for ATI graphics accelerators

```

sudo apt-get --purge remove xorg-driver-fglrx
sudo apt-get install xorg-driver-fglrx

```

Once done, reboot and get back into X session.  Go back to step 8 and enable the restricted driver.  You may need yet another reboot after enabling the driver.

If that didn't help, you are running into the dreaded "Mesa issue".  Gutsy "Restricted Driver Manager" does everything possible to avoid it.  I have never run into the "Mesa issue", so I don't know how to troubleshoot it.  Please refer to this [excellent updated Wiki page](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide) or  [thread=143283]Fixing the "Mesa Issue" for ATI Cards[/thread] thread -- the original post is very outdated, but the troubleshooting section at the end is good.
-----------
[SIZE="3"]**Mesa nightmares continued.**[/size]
If you have any questions, please post output of commands
fglrxinfo -display :0
fglrxinfo -display :1
-----------
[SIZE="3"]**Envy and/or newer drivers from ATI**[/size]

Some users report using Envy or alternative mechanisms to install newer drivers.  This is very dangerous.  As [this press-release](http://www.phoronix.com/scan.php?page=article&item=887&num=1) indicates, *many with older GPUs had immediately upgraded with some then having a foul experience.*  In this guide, "older" means anything but 2000HD series!!! That's what most of us run.  So, if you have have a video card from the supported hardware section (see my previous post), then you must not upgrade to the newer driver.

[SIZE="4"]References[/SIZE]
[SIZE="5"]DO NOT FOLLOW THESE LINKS BLINDLY.  MOST ARE WRITTEN FOR FEISTY AND THIS GUIDE UNDOES WHAT IS SUGGESTED IN THESE GUIDES.
[/SIZE]
[http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://help.ubuntu.com/community/RestrictedDrivers/ATI](https://help.ubuntu.com/community/RestrictedDrivers/ATI)
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by toupeiro on 2007-10-17
Great howto!   Kudo's!!

---

### Post by sewmyheadon on 2007-10-17
Hey Michael,

I just upgraded to the Release Candidate (can't wait for the actual release tomorrow) on my Dell Inspiron 9300 notebook.

As you experienced, Compiz no longer worked.  

I had previously installed Compiz Fusion on Feisty and had it working quite nicely.  Once the Gutsy upgrade was complete, I could see and access my desktop, but couldn't get Desktop Effects to work.

So, I followed your instructions and have it working like a charm now.  It didn't preserve my settings, but that didn't matter.

Thanks!

eric

---

### Post by michael37 on 2007-10-17
> **sewmyheadon said:**
> Hey Michael,

I just upgraded to the Release Candidate (can't wait for the actual release tomorrow) on my Dell Inspiron 9300 notebook.

As you experienced, Compiz no longer worked.  

I had previously installed Compiz Fusion on Feisty and had it working quite nicely.  Once the Gutsy upgrade was complete, I could see and access my desktop, but couldn't get Desktop Effects to work.

So, I followed your instructions and have it working like a charm now.  It didn't preserve my settings, but that didn't matter.

Thanks!

eric

Glad it works for you.  I guess I should have clarified that step 4 does remove all your custom settings, but that's an unfortunate consequence of not having a standardized version of compiz in Feisty nor common set of compiz plugins.

I tried to preserve the settings for myself, but it caused more harm than good.  Hopefully, we won't need to wipe all our settings again this since a decent version of Compiz Fusion is standard for Gutsy RC.

---

### Post by Tachyon1000 on 2007-10-17
> **michael37 said:**
> [SIZE="7"]If you are upgrading from Feisty 7.04 or earlier versions and you have run Xgl before.[/SIZE]

When upgrading, you may experience blank screen, a screen with no windows and toolbars, a screen with only a background, or any other mess.  It is caused by the customized scripts for Xgl which do not work with Gutsy.  So, we need to clean up.

If you really can't log into a working X session and open a terminal, simply press "Ctrl-Alt-F1" to get into the text prompt and follow the removal steps (1-4) from the text interface.  After a reboot, the graphics should work better.

[LIST=1]
[*]Remove compiz
```

sudo echo "activate sudo"
sudo apt-get --purge remove compiz*
sudo apt-get --purge remove libcompiz*
sudo apt-get --purge remove libdecoration0
sudo apt-get --purge remove compizconfig-settings-manager 
sudo apt-get --purge remove python-compizconfig

```
[*]Remove Xgl
```

sudo apt-get --purge remove xserver-xgl

```
[*]Clean up
```

sudo apt-get autoremove

```
[*]Remove customizations
```

rm -rf ~/.compiz
rm -rf ~/.config/compiz
rm -rf ~/.gconf/apps/compiz
sudo rm -i /usr/local/bin/startxgl.sh
sudo rm -i /usr/share/xsessions/xgl.desktop

```
When asked to remove the files, type YES.  If the files were present and you removed them, proceed to the next item.  Otherwise, undo customizations to /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom that you have made from [ this section of the guide](https://help.ubuntu.com/community/CompositeManager/Xgl#head-0e4ffce2a76cdb03b8dbd57642f13fac385afef0)
[*]Reboot
[*]Login back in and find yourself in a 3D effect devoid session.  You may not even be running a windows manager.  If you can't move windows and don't see window decorations, press "Alt-F2" and type ```
metacity --replace
```
[*]Verify that everything else is working properly, e.g. Firefox opens, Wired and/or Wireless Network connects, etc.  This is the best time to troubleshoot everything else until we enable 3D effects.
[*]Enable fgrlx driver.

Install linux-restricted-modules and restricted-manager provided in the restricted repositories:
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver".
[*]Reboot if necessary.
[*]After reboot, log back in.
Open terminal and run
```

fglrxinfo -display :0

```
and verify that you see something like this:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

```
[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/attention.png[/IMG]If you don't have command fglrxinfo, you either don't have a supported ATI card or you missed a step or two.  Go back through all steps.  If unsure, post your /etc/X11/xorg.conf in this thread.
[*]=================================
[*]Are you ready to get back into the wobbly windows and Desktop Cube?
[*]=================================
[*]Install Xgl.
```
sudo apt-get install xserver-xgl
```
[*]Install compiz
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0

```
[*] Reboot
[*] Log in. 3D effects should be enabled!  You no longer need to select a special Xgl session.
[/LIST]

If you have any questions, please post output of commands
fglrxinfo -display :0
fglrxinfo -display :1
as well as contents of your /etc/X11/xorg.conf file.

[SIZE="4"]References[/SIZE]
[SIZE="5"]DO NOT FOLLOW THESE LINKS BLINDLY.  MOST ARE WRITTEN FOR FEISTY AND THIS GUIDE UNDOES WHAT IS SUGGESTED IN THESE GUIDES.
[/SIZE]
[http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://help.ubuntu.com/community/RestrictedDrivers/ATI](https://help.ubuntu.com/community/RestrictedDrivers/ATI)
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

That's a lot of stuff considering my experience when I upgraded from Feisy about a week ago was that everything just worked.  Granted I had no compiz or such in Feisty.  I was just using radeon driver and metacity, so I think to the degree that one has tricked out their feisty is to the degree that one might have problems doing a standard dist upgrade via the update manager.

---

### Post by iobelisk on 2007-10-17
Hi. I am having a weird problem with this whole thing. 

I have the ATI restricted driver installed. I have XGL installed and running. But when I enable desktop effects (via appearance under system/preferences), one of my desktops on the workspace switched vanishes and a lot of the effects are not active even though I enable them through the gnome compiz manager. Some effects though, like wobbling for example, work.

my output for glxinfo is:

```
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
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

I am running Gutsy on an acer laptop with an ATI x700 card.

What is XFree86-DRI? For some reason 3D rendering is not active on my computer. Could this be the problem? I'd much appreciate any help. Thank you!

xorg.conf:
	```
Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility X700 (PCIE)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

output for fglrxinfo -display :1 --

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```

output for fglrxinfo -display :0 --
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.0.6473 (8.37.6)
```

---

### Post by michael37 on 2007-10-18
> **Tachyon1000 said:**
> That's a lot of stuff considering my experience when I upgraded from Feisy about a week ago was that everything just worked.  Granted I had no compiz or such in Feisty.  I was just using radeon driver and metacity, so I think to the degree that one has tricked out their feisty is to the degree that one might have problems doing a standard dist upgrade via the update manager.

The problems are due to customized Xgl and Compiz scripts that were required in Fiesty to get the alpha versions of Compiz running.

I have desktops which were a breeze to upgrade.

---

### Post by michael37 on 2007-10-18
> **iobelisk said:**
> Hi. I am having a weird problem with this whole thing. 

I have the ATI restricted driver installed. I have XGL installed and running. But when I enable desktop effects (via appearance under system/preferences), one of my desktops on the workspace switched vanishes and a lot of the effects are not active even though I enable them through the gnome compiz manager. Some effects though, like wobbling for example, work.


Weird problems indeed.   Your xglinfo output is perfect.

> **iobelisk said:**
> 
I am running Gutsy on an acer laptop with an ATI x700 card.

What is XFree86-DRI? For some reason 3D rendering is not active on my computer. Could this be the problem? I'd much appreciate any help. Thank you!

Badly misleading message.  ATI restricted driver uses alternative 3D rendering technologies.  This message is not only expected, but also indicated your system is running perfectly.

Your xorg.conf is healthy.
> **iobelisk said:**
> 
output for fglrxinfo -display :1 --

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```

output for fglrxinfo -display :0 --
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.0.6473 (8.37.6)
```
This is the ideal fglrxinfo output for the working system with fully functional Xgl.

So, where is your problem?  Got to be broken legacy compiz config.  Do steps 1, 4 and 15 from my upgrade guide.  Omit all other steps.

---

### Post by michael37 on 2007-10-18
> **iobelisk said:**
> Hi. I am having a weird problem with this whole thing. 


When you are done uninstalling and reinstalling, compiz, follow this short section from the bottom of [https://help.ubuntu.com/community/CompositeManager/CompizFusionATI](https://help.ubuntu.com/community/CompositeManager/CompizFusionATI)

Run ccsm
```

ccsm 

```

Click General Options Open the Desktop Size tab

    *      Horizonal Virtual Size: 4 Vertical Virtual Size: 1 Number of Desktops: 1

Click Back Check these plugins:

    *      Desktop Cube Rotate Cube

---

### Post by kg00005 on 2007-10-18
Hi,

I have an ATI RADEON X1300 Pro PCI-E card.

My output looks like this:
# fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

How can I replace Mesa driver to Ati?
Should I?

Regards,
G

---

### Post by DrQuincy on 2007-10-18
> **kg00005 said:**
> Hi,

I have an ATI RADEON X1300 Pro PCI-E card.

My output looks like this:
# fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

How can I replace Mesa driver to Ati?
Should I?

Regards,
G

I'm the same . . . someone PLEASE help!

---

### Post by iobelisk on 2007-10-18
> **michael37 said:**
> Weird problems indeed.   Your xglinfo output is perfect.


Badly misleading message.  ATI restricted driver uses alternative 3D rendering technologies.  This message is not only expected, but also indicated your system is running perfectly.

Your xorg.conf is healthy.

This is the ideal fglrxinfo output for the working system with fully functional Xgl.

So, where is your problem?  Got to be broken legacy compiz config.  Do steps 1, 4 and 15 from my upgrade guide.  Omit all other steps.

Hi. Thanks for your help. 

I guess I had been screwing around trying to get this to work before finding this thread and now everytime I try an apt-get I get this message:
```

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
 
This is in response to the install command via step 15. I also get this response for any apt-get or aptitude install or remove command I input into the terminal. Man. I guess I need to try fix this first before I can try the compiz installation (I had already uninstalled compiz earlier, but removed a few of the config files manually through nautilus)

Ps- just thought I'd add that installation via synaptic is all good.

Ps again- Oh. This error message seems to occur only when I have synaptic open at the same time as running the command in the terminal? I am not really sure. I will look into this after work today. Sorry for derailing this thread! But for the record, if my xorg.conf and everything else is okay, I have tried installing and reinstalling compiz a million times. Perhaps I did not remove all configs and settings? I will try it your way after work today and see what happens. Thanks!

---

### Post by X-dark on 2007-10-18
Thank you. This just worked.

---

### Post by H1tm3n on 2007-10-18
Anyone knows how do you enable enhanced compiz fusion effects, like windows dodge, cube rotating based on fixed ground rather than cube's middle point and such... :S

---

### Post by michael37 on 2007-10-18
> **H1tm3n said:**
> Anyone knows how do you enable enhanced compiz fusion effects, like windows dodge, cube rotating based on fixed ground rather than cube's middle point and such... :S

Well, are you sure none of these are in the available Ubuntu plugins?  
```

sudo apt-get compiz-fusion-plugins-main compiz-fusion-plugins-extra

```
Check if you have these installed, and if you have current versions.

If you need more plugins, see the Compiz Fusion wiki.
[http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

You will have to build them yourself (though I don't see Dodge -- I know what you are talking about, but I don't know where it is now)

---

### Post by michael37 on 2007-10-18
> **kg00005 said:**
> Hi,

I have an ATI RADEON X1300 Pro PCI-E card.

My output looks like this:
# fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

How can I replace Mesa driver to Ati?
Should I?

Regards,
G

I strongly recommend my howto in the guide -- pick the one depending whether you are upgrading from Feisty or Gutsy fresh install.  You are not using the restricted driver.  If you want any decent 3D performance, switch to restricted.  

NOTE: there is a bug in Gutsy -- suspend and hibernate on laptops doesn't work with restricted driver.

---

### Post by michael37 on 2007-10-18
> **DrQuincy said:**
> I'm the same . . . someone PLEASE help!

See my previous comment.  Use my howto -- you need the restricted driver.

---

### Post by michael37 on 2007-10-18
> **iobelisk said:**
> Hi. Thanks for your help. 

I guess I had been screwing around trying to get this to work before finding this thread and now everytime I try an apt-get I get this message:
```

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
 
This is in response to the install command via step 15. I also get this response for any apt-get or aptitude install or remove command I input into the terminal. Man. I guess I need to try fix this first before I can try the compiz installation (I had already uninstalled compiz earlier, but removed a few of the config files manually through nautilus)

Ps- just thought I'd add that installation via synaptic is all good.

Ps again- Oh. This error message seems to occur only when I have synaptic open at the same time as running the command in the terminal? I am not really sure. I will look into this after work today. Sorry for derailing this thread! But for the record, if my xorg.conf and everything else is okay, I have tried installing and reinstalling compiz a million times. Perhaps I did not remove all configs and settings? I will try it your way after work today and see what happens. Thanks!


YOU NAILED IT MAN!! You can't run Synaptic and apt-get at the same time.

For the same price, you can't run Update Manager, Synaptic or apt-get at the same time.

---

### Post by digital_exhaust on 2007-10-18
My,my,my... thank you.. very helpful info here.... 

Thanks..

---

### Post by orbital on 2007-10-19
Thanks Michael for this great how-to, compiz didn't work after upgrade but now it does.

---

### Post by foottechman on 2007-10-19
When I reboot, I only get about 3/4 of the screen to use than the other part is the color of the background.  Here are my files.

#fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

#fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))


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
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"glx"
	Load		"dbe"
	Load		"dri"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modelname	"Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x960@60"	"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Screen	1
	Vendorname	"ATI"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by BreuJa on 2007-10-19
Hello,

I just upgraded from Feisty to Gutsy by using the Update-Manager. 

Eyecatcher:
**I used Envy on Feisty to get my gfx up and running. Probably that was the cause for the gfx not running correctly after the upgrade.**

I faced the same problems as many others:
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```
```
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```
So in fact GFX was slow and the potential of my Gfx-Card unused. The card is shown by lspci as follows:
```
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
```
Since I upgraded to Gutsy I refered to the recommended method as shown by michael37. I can't remember that I played around with xserver-xgl in the past, but I followed the howto anyway.
However, it didn't change the situation. The restricted driver for my card was already used, when Gutsy booted for the first time.

The solution to my problem was to just deselect the restricted driver, which lead to the driver manager removing some packages (among them some kernel 2.6.20 stuff), then I just rebooted and enabled the driver again, which lead to the driver manager installing some fglrx package.
After a reboot everything was just fine. I just installed xserver-xgl and the compiz stuff as shown by michael37 and it worked flawlessly.

Kind regards.

---

### Post by michael37 on 2007-10-19
> **foottechman said:**
> When I reboot, I only get about 3/4 of the screen to use than the other part is the color of the background.  Here are my files.


EDIT:  Gutsy is different, yet again, Composite extension now works...  Let me think about it.

---

### Post by michael37 on 2007-10-19
> **BreuJa said:**
> Hello,

I just upgraded from Feisty to Gutsy by using the Update-Manager. 

Eyecatcher:
**I used Envy on Feisty to get my gfx up and running. Probably that was the cause for the gfx not running correctly after the upgrade.**

I faced the same problems as many others:
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```
```
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```
So in fact GFX was slow and the potential of my Gfx-Card unused. The card is shown by lspci as follows:
```
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
```
Since I upgraded to Gutsy I refered to the recommended method as shown by michael37. I can't remember that I played around with xserver-xgl in the past, but I followed the howto anyway.
However, it didn't change the situation. The restricted driver for my card was already used, when Gutsy booted for the first time.

The solution to my problem was to just deselect the restricted driver, which lead to the driver manager removing some packages (among them some kernel 2.6.20 stuff), then I just rebooted and enabled the driver again, which lead to the driver manager installing some fglrx package.
After a reboot everything was just fine. I just installed xserver-xgl and the compiz stuff as shown by michael37 and it worked flawlessly.

Kind regards.

That is correct, Envy interferes with proper functionality of Restriced Drivers Manager.  It's a known problem with Envy.  I never used Envy yourself, so I would appreciate more detailed instructions on how to get proper fgrlx drivers on computers where Envy was used in Feisty.  I kinda take it that if you use Envy, you know how to use it, which you clearly do :)

---

### Post by michael37 on 2007-10-19
> **foottechman said:**
> When I reboot, I only get about 3/4 of the screen to use than the other part is the color of the background.  Here are my files.

#fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

#fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))


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
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"glx"
	Load		"dbe"
	Load		"dri"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modelname	"Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x960@60"	"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Screen	1
	Vendorname	"ATI"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

Try running command "sudo aticonfig --initial".  Reboot.

Let us know how your xorg.conf looks after that command.

---

### Post by foottechman on 2007-10-19
I did a fresh install and have only done
"sudo apt-get install xserver-xgl" 
then rebooted.  The desktop effects now work though I lost my lower taskbar which may be normal as far as I know.  It is only working on normal effects and I haven't tried extra effects yet.  I'll see if that breaks it.

---

### Post by Eviltelm on 2007-10-19
what is the best for these effects, the ati driver from the site or the xorg-driver-fglrx?
Thanks

---

### Post by michael37 on 2007-10-19
> **Eviltelm said:**
> what is the best for these effects, the ati driver from the site or the xorg-driver-fglrx?
Thanks

Please clarify the question? The ati driver from which site?

---

### Post by Eviltelm on 2007-10-19
> **michael37 said:**
> Please clarify the question? The ati driver from which site?

If it works better with just using 'sudo apt-get install xorg-driver-fglrx' ou using the manual way with version 8.40...

---

### Post by michael37 on 2007-10-19
> **Eviltelm said:**
> If it works better with just using 'sudo apt-get install xorg-driver-fglrx' ou using the manual way with version 8.40...

The best option is going into Restricted Drivers Manager and enable ATI binary driver there.  That includes, but is not limited to, installing xorg-driver-fgrlx package.

I do not recommend using Envy (aka newer drivers like 8.40) unless you need it for a very certain bug or a very specific problem.  To date, Gutsy packages a fairly recent version of the binary driver, so you don't gain much from Envy and you lose ability to manage the driver using the Restricted Drivers Manager (e.g. for kernel upgrades).

---

### Post by cor2y on 2007-10-19
worked like a charm michael37 once i remembered to have emerald and compiz run at startup in sessions.
But by some fluke or through something i did i can not now access the emerald theme frontend anytime i run "emerald -replace" its just the last theme i used in feisty not the frontend theme selector.
What is the correct syntax to launch it?

---

### Post by TiMBuS on 2007-10-20
Hmm, I got a clean install of gutsy and installed everything from the repository, and halfway through making the alternate session I noticed the little light bulb in the corner and read it. So I deleted the session setup I was halfway through finishing, and rebooted. 
Xgl loads, but for some reason metacity is loading. I think compiz is crashing during init but I'm not sure.
It works if I open a terminal and type 'compiz --replace &' to manually start compiz. Are there any logs I can check to see what is going on?

Ninja Edit: I read the post above and it seems cor2y has to manually start compiz as well. Did you forget to mention this in your instructions or is this perhaps a common issue?

---

### Post by andrewpmoore on 2007-10-20
Hi,
I'm not having any luck getting this working, when I get to step 10 I've tried to follow the common problem section, but still no luck. Any help appriciated.

Output as follows:

andrew@desktop-linux:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

andrew@desktop-linux:~$ fglrxinfo -display :1
Error: unable to open display :1


xorg.conf
-----------

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
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	30.0	-	70.0
	Vertrefresh	50.0	-	160.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:1:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by TiMBuS on 2007-10-20
Seems like you've still got the mesa driver loaded, even though you have fglrx selected in your xorg.conf..

Have you selected the proprietary driver in the restricted drivers manager? And if so, have you rebooted since?

---

### Post by andrewpmoore on 2007-10-20
Hi, yes, I've tried unselecting it and selecting it again, but no luck, and done a reboot between each time.

---

### Post by michael37 on 2007-10-21
> **andrewpmoore said:**
> Hi, yes, I've tried unselecting it and selecting it again, but no luck, and done a reboot between each time.

Two questions: 
1. Have you used Envy or any form of non-Ubuntu-standard ATI driver on your computer?
2. Could you please post your X*.*.log from /var/log?

---

### Post by michael37 on 2007-10-21
> **TiMBuS said:**
> Hmm, I got a clean install of gutsy and installed everything from the repository, and halfway through making the alternate session I noticed the little light bulb in the corner and read it. So I deleted the session setup I was halfway through finishing, and rebooted. 
Xgl loads, but for some reason metacity is loading. I think compiz is crashing during init but I'm not sure.
It works if I open a terminal and type 'compiz --replace &' to manually start compiz. Are there any logs I can check to see what is going on?

Ninja Edit: I read the post above and it seems cor2y has to manually start compiz as well. Did you forget to mention this in your instructions or is this perhaps a common issue?

cor2y problem is totally different -- it's only about emerald.  His compiz is working fine.

What alternate session are you referring to?  In Gutsy, Xgl always run and no alternate sessions are ever needed.  Big difference from Feisty.

Try this command and see what is your WM default:

```

gconftool-2 -g /desktop/gnome/applications/window_manager/default

```

If it's not compiz, try to set it to compiz

```

gconftool-2 -s /desktop/gnome/applications/window_manager/default /usr/bin/compiz --type string

```

---

### Post by michael37 on 2007-10-21
> **cor2y said:**
> worked like a charm michael37 once i remembered to have emerald and compiz run at startup in sessions.
But by some fluke or through something i did i can not now access the emerald theme frontend anytime i run "emerald -replace" its just the last theme i used in feisty not the frontend theme selector.
What is the correct syntax to launch it?

Yes, it's the correct to launch it.  I think I know why your emerald doesn't work -- 'cause my guide doesn't reset its Feisty settings.  I don't use emerald myself (gtk-windows-decorator is good enough for me), so I didn't include a "cleanup" section for emerald settings.  

The good news is your emerald works at all.  The bad news is I have no idea how to reset those old settings.  Please experiment and post here what you found.  I'll update the howto with emerald cleanup instructions.

I would start with

sudo apt-get --purge remove emerald
sudo apt-get install emerald

---

### Post by michael37 on 2007-10-21
For benefit of those who keep running into the dreaded "Mesa issue", I added this paragraph to my how-to.

[INDENT]
If that didn't help, you are running into the dreaded "Mesa issue".  Gutsy "Restricted Driver Manager" does everything possible to avoid it.  I have never run into the "Mesa issue", so I don't know how to troubleshoot it.  Please refer to this [excellent updated Wiki page](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide) or  [thread=143283]Fixing the "Mesa Issue" for ATI Cards[/thread] thread -- the original post is very outdated, but the troubleshooting section at the end is good.
[/INDENT]

---

### Post by TiMBuS on 2007-10-21
Yeah, that was the problem.
Odd, the package should have changed it for me. Oh well thanks alot man.

And yeah, I was making an alternate session because thats how it was done in fiesty, but I saw the little lightbulb in the tray and read that I didn't need to make the alternate session so I deleted the files. No issue.

---

### Post by popophobia on 2007-10-21
Hi,
I'm a new user and just install the compiz package as above. However, after installation, Ubuntu seems to lost some of its original setting options (touchpad in particular).
Now I cannot disable tapping... Any ideas how to restore the options? Thanks.

---

### Post by cronqvist on 2007-10-22
Works like a Miracle! Had Desktop Effects enabled in my first try. Thank you!

---

### Post by itsbradman on 2007-10-22
I have the restricted repositories enabled but the restricted driver for my ATI card doesn't even show.  This is the output of fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1


And here is the error I get when running compiz in terminal:
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

Everything worked perfectly before I upgraded to gutsy.  Now with no compositing, I get no compiz, no awn, and no screenlets!!

---

### Post by itsbradman on 2007-10-22
oh, and I tried the mesa fix and had to reconfigure x after it, b/c x wouldn't start.

---

### Post by itsbradman on 2007-10-22
in addition, here is what I get when I try to run sudo aticonfig --intitial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfa289f2 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d8d92b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d36050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:01 3817545    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:01 3817545    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7d12000-b7d13000 rw-p b7d12000 00:00 0 
b7d13000-b7d15000 r-xp 00000000 08:01 2588979    /lib/tls/i686/cmov/libdl-2.6.1.so
b7d15000-b7d17000 rw-p 00001000 08:01 2588979    /lib/tls/i686/cmov/libdl-2.6.1.so
b7d17000-b7d18000 rw-p b7d17000 00:00 0 
b7d18000-b7d1c000 r-xp 00000000 08:01 3818279    /usr/lib/libXdmcp.so.6.0.0
b7d1c000-b7d1d000 rw-p 00003000 08:01 3818279    /usr/lib/libXdmcp.so.6.0.0
b7d1d000-b7d1f000 r-xp 00000000 08:01 3818130    /usr/lib/libXau.so.6.0.0
b7d1f000-b7d20000 rw-p 00001000 08:01 3818130    /usr/lib/libXau.so.6.0.0
b7d20000-b7e64000 r-xp 00000000 08:01 2588758    /lib/tls/i686/cmov/libc-2.6.1.so
b7e64000-b7e65000 r--p 00143000 08:01 2588758    /lib/tls/i686/cmov/libc-2.6.1.so
b7e65000-b7e67000 rw-p 00144000 08:01 2588758    /lib/tls/i686/cmov/libc-2.6.1.so
b7e67000-b7e6a000 rw-p b7e67000 00:00 0 
b7e6a000-b7e8d000 r-xp 00000000 08:01 2588980    /lib/tls/i686/cmov/libm-2.6.1.so
b7e8d000-b7e8f000 rw-p 00023000 08:01 2588980    /lib/tls/i686/cmov/libm-2.6.1.so
b7e8f000-b7f7c000 r-xp 00000000 08:01 3818310    /usr/lib/libX11.so.6.2.0
b7f7c000-b7f80000 rw-p 000ed000 08:01 3818310    /usr/lib/libX11.so.6.2.0
b7f80000-b7f8d000 r-xp 00000000 08:01 3819506    /usr/lib/libXext.so.6.4.0
b7f8d000-b7f8e000 rw-p 0000d000 08:01 3819506    /usr/lib/libXext.so.6.4.0
b7f8e000-b7f8f000 rw-p b7f8e000 00:00 0 
b7f8f000-b7f96000 r-xp 00000000 08:01 3818455    /usr/lib/libXrender.so.1.3.0
b7f96000-b7f97000 rw-p 00006000 08:01 3818455    /usr/lib/libXrender.so.1.3.0
b7f97000-b7f9c000 r-xp 00000000 08:01 622763     /usr/lib/libXrandr.so.2.1.0
b7f9c000-b7f9d000 rw-p 00005000 08:01 622763     /usr/lib/libXrandr.so.2.1.0
b7fa5000-b7faf000 r-xp 00000000 08:01 2375735    /lib/libgcc_s.so.1
b7faf000-b7fb0000 rw-p 0000a000 08:01 2375735    /lib/libgcc_s.so.1
b7fb0000-b7fb3000 rw-p b7fb0000 00:00 0 
b7fb3000-b7fcd000 r-xp 00000000 08:01 1163454    /lib/ld-2.6.1.so
b7fcd000-b7fcf000 rw-p 00019000 08:01 1163454    /lib/ld-2.6.1.so
bfa14000-bfa2a000 rw-p bfa14000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

---

### Post by Ozitraveller on 2007-10-22
Hi 

I have an ATI 9200SE video card. After I changed Preferences Effects to enable special effects, I get wobbly windows and I can drag between the desktops, so it seems ok. But I don't know how to see/use the cube.

Do I need to install anything else?

Could someone please point me to any docs about shortcut keys, and anything else useful.

Thanks

---

### Post by andrewpmoore on 2007-10-22
> **michael37 said:**
> Two questions: 
1. Have you used Envy or any form of non-Ubuntu-standard ATI driver on your computer?
2. Could you please post your X*.*.log from /var/log?


At the point you saw the logs I hadn't had envy on. I have since tried it (before reading this message of yours) but that didn't fix things, so I've removed it again.

Graphics card is a X1300 pro

If the X*.*.log files are of any use to help now, here they are:

Xorg.0.log
-------------

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux desktop-linux 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 22 13:07:46 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 1028,01dd rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:19:0: chip 8086,104c card 1028,01dd rev 02 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01dd rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2812 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2822 card 1028,01dd rev 02 class 01,04,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01dd rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,7183 card 1028,0302 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71a3 card 1028,0303 rev 00 class 03,80,00 hdr 00
(II) PCI: 03:02:0: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 03:02:1: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 03:02:2: chip 1106,3104 card 1106,3104 rev 63 class 0c,03,20 hdr 80
(II) PCI: 03:03:0: chip 14f1,2f20 card 14f1,200f rev 00 class 07,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfefffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdfb00000 - 0xdfbfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV516 [ATI Radeon X1300/X1550 Series] rev 0, Mem @ 0xc0000000/28, 0xdfde0000/16, I/O @ 0xdc00/8, BIOS @ 0xdfe00000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV516 [ATI Radeon X1300 Pro Secondary] rev 0, Mem @ 0xdfdf0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[1] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[2] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[3] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[4] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[5] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[6] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[7] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[8] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[9] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[10] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[11] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[14] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[15] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[16] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[17] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[18] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[19] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[20] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[21] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[22] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[23] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[24] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[1] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[2] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[3] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[4] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[5] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[6] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[7] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[8] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[9] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[10] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[11] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[14] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[15] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[16] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[17] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[18] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[19] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[20] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[21] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[22] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[23] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[24] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[5] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[6] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[7] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[8] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[9] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[10] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[11] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[12] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[20] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[21] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[22] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[23] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[24] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[25] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[26] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[27] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[28] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[29] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[30] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[31] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[32] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[33] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.37.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.37g1                           
(II) ATI Proprietary Linux Driver Build Date: May 25 2007 14:25:03
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.37.1.1.2.3-driver-lnx-x86-x86_64-346145
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x7183) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[5] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[6] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[7] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[8] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[9] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[10] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[11] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[12] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[20] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[21] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[22] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[23] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[24] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[25] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[26] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[27] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[28] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[29] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[30] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[31] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[32] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[33] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8209a20
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[5] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[6] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[7] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[8] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[9] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[10] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[11] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[12] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[23] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[24] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[25] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[26] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[27] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[28] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[29] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[30] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[31] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[32] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[33] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[34] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[35] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[36] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[37] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X1300/X1550 Series" (Chipset = 0x7183)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x0302)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfde0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV516
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	ABI class: X.Org Server Extension, version 0.3
(WW) fglrx(0): Unable to initialize PCS context in the kernel module
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: DEL  Model: d015  Serial#: 893796685
(II) fglrx(0): Year: 2007  Week: 25
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.639 redY: 0.332   greenX: 0.288 greenY: 0.597
(II) fglrx(0): blueX: 0.152 blueY: 0.081   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 119.0 MHz   Image Size:  473 x 296 mm
(II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) fglrx(0): Serial No: DT86776I5FAM
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: DELL E228WFP
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0010ac15d04d414635
(II) fglrx(0): 	19110103802f1e78ee8f30a355499827
(II) fglrx(0): 	145054a54b00714f8180010101010101
(II) fglrx(0): 	0101010101017c2e90a0601a1e403020
(II) fglrx(0): 	3600d9281100001a000000ff00445438
(II) fglrx(0): 	36373736493546414d0a000000fd0038
(II) fglrx(0): 	4b1e530e000a202020202020000000fc
(II) fglrx(0): 	0044454c4c20453232385746500a0080
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 32 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (470, 300) mm
(--) fglrx(0): DPI set to (90, 88)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) LoadModule: "glesx.so" (glesx)
(WW) LoadModule: given non-canonical module name "glesx.so"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[7] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[8] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[9] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[10] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[11] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[12] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[13] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[14] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[15] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[16] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[17] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[22] 0	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[26] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[27] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[28] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[29] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[30] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[31] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[32] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[33] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[34] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[35] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[36] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[37] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[38] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[39] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[40] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7c51000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7c51000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x0ffe0000
(II) fglrx(0): Splitting WC range: base: 0xc0000000, size: 0xffe0000
(II) fglrx(0): Splitting WC range: base: 0xc8000000, size: 0x7fe0000
(II) fglrx(0): Splitting WC range: base: 0xcc000000, size: 0x3fe0000
(II) fglrx(0): Splitting WC range: base: 0xce000000, size: 0x1fe0000
(II) fglrx(0): Splitting WC range: base: 0xcf000000, size: 0xfe0000
(II) fglrx(0): Splitting WC range: base: 0xcf800000, size: 0x7e0000
(II) fglrx(0): Splitting WC range: base: 0xcfc00000, size: 0x3e0000
(II) fglrx(0): Splitting WC range: base: 0xcfe00000, size: 0x1e0000
(II) fglrx(0): Splitting WC range: base: 0xcff00000, size: 0xe0000
(II) fglrx(0): Splitting WC range: base: 0xcff80000, size: 0x60000
(WW) fglrx(0): Failed to set up write-combining range (0xcffc0000,0x20000)
(WW) fglrx(0): Failed to set up write-combining range (0xcff80000,0x60000)
(WW) fglrx(0): Failed to set up write-combining range (0xcff00000,0xe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xcfe00000,0x1e0000)
(WW) fglrx(0): Failed to set up write-combining range (0xcfc00000,0x3e0000)
(WW) fglrx(0): Failed to set up write-combining range (0xcf800000,0x7e0000)
(WW) fglrx(0): Failed to set up write-combining range (0xcf000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xce000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xcc000000,0x3fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc8000000,0x7fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xc0000000,0xffe0000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1728,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1050) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1728 x 7141
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
(II) fglrx(0): GLESX enableFlags = 0
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
fbarea0->box.x1 0x00000000, fbarea0->box.y1 0x0000041d
fbarea0->box.x2 0x000006c0, fbarea0->box.y2 0x0000041f
icon[0].start=0x6f1000
fbarea1->box.x1 0x00000000, fbarea1->box.y1 0x0000041f
fbarea1->box.x2 0x000006c0, fbarea1->box.y2 0x00000421
icon[1].start=0x6f5000
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
```


Xorg.20.log

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux desktop-linux 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.20.log", Time: Wed Sep  5 20:17:41 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 1028,01dd rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:19:0: chip 8086,104c card 1028,01dd rev 02 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01dd rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2812 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2822 card 1028,01dd rev 02 class 01,04,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01dd rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,7183 card 1028,0302 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71a3 card 1028,0303 rev 00 class 03,80,00 hdr 00
(II) PCI: 03:02:0: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 03:02:1: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 03:02:2: chip 1106,3104 card 1106,3104 rev 63 class 0c,03,20 hdr 80
(II) PCI: 03:03:0: chip 14f1,2f20 card 14f1,200f rev 00 class 07,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfefffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdfb00000 - 0xdfbfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV516 [ATI Radeon X1300/X1550 Series] rev 0, Mem @ 0xc0000000/28, 0xdfde0000/16, I/O @ 0xdc00/8, BIOS @ 0xdfe00000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV516 [ATI Radeon X1300 Pro Secondary] rev 0, Mem @ 0xdfdf0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[1] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[2] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[3] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[4] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[5] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[6] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[7] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[8] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[9] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[10] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[11] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[14] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[15] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[16] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[17] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[18] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[19] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[20] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[21] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[22] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[23] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[24] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[1] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[2] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[3] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[4] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[5] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[6] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[7] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[8] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[9] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[10] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[11] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[14] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[15] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[16] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[17] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[18] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[19] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[20] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[21] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[22] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[23] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[24] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[5] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[6] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[7] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[8] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[9] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[10] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[11] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[12] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[20] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[21] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[22] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[23] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[24] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[25] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[26] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[27] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[28] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[29] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[30] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[31] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[32] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[33] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x7183) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[5] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[6] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[7] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[8] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[9] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[10] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[11] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[12] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[20] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[21] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[22] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[23] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[24] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[25] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[26] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[27] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[28] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[29] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[30] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[31] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[32] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[33] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e6aa0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[5] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[6] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[7] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[8] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[9] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[10] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[11] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[12] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[23] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[24] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[25] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[26] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[27] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[28] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[29] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[30] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[31] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[32] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[33] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[34] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[35] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[36] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[37] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X1300/X1550 Series" (Chipset = 0x7183)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x0302)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfde0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV516
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: DEL  Model: d015  Serial#: 893796685
(II) fglrx(0): Year: 2007  Week: 25
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.639 redY: 0.332   greenX: 0.288 greenY: 0.597
(II) fglrx(0): blueX: 0.152 blueY: 0.081   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 119.0 MHz   Image Size:  473 x 296 mm
(II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) fglrx(0): Serial No: DT86776I5FAM
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: DELL E228WFP
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0010ac15d04d414635
(II) fglrx(0): 	19110103802f1e78ee8f30a355499827
(II) fglrx(0): 	145054a54b00714f8180010101010101
(II) fglrx(0): 	0101010101017c2e90a0601a1e403020
(II) fglrx(0): 	3600d9281100001a000000ff00445438
(II) fglrx(0): 	36373736493546414d0a000000fd0038
(II) fglrx(0): 	4b1e530e000a202020202020000000fc
(II) fglrx(0): 	0044454c4c20453232385746500a0080
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 37 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1080 (pitch 0)
(**) fglrx(0): *Mode "1920x1080": 81.6 MHz (scaled from 0.0 MHz), 33.6 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   81.64  1920 1984 2176 2432  1080 1081 1084 1119 interlace +hsync
(**) fglrx(0):  Default mode "1920x1080": 66.3 MHz (scaled from 0.0 MHz), 27.8 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   66.33  1920 1960 2152 2384  1080 1081 1084 1113 interlace +hsync
(**) fglrx(0): *Mode "1776x1000": 69.2 MHz (scaled from 0.0 MHz), 31.1 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1776x1000"   69.18  1776 1824 2000 2224  1000 1001 1004 1037 interlace +hsync
(**) fglrx(0):  Default mode "1776x1000": 56.1 MHz (scaled from 0.0 MHz), 25.8 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "1776x1000"   56.08  1776 1800 1976 2176  1000 1001 1004 1031 interlace +hsync
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (470, 300) mm
(--) fglrx(0): DPI set to (103, 91)
(--) fglrx(0): Virtual size is 1920x1080 (pitch 1920)
(**) fglrx(0): *Mode "1920x1080": 81.6 MHz (scaled from 0.0 MHz), 33.6 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   81.64  1920 1984 2176 2432  1080 1081 1084 1119 interlace +hsync
(**) fglrx(0):  Default mode "1920x1080": 66.3 MHz (scaled from 0.0 MHz), 27.8 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   66.33  1920 1960 2152 2384  1080 1081 1084 1113 interlace +hsync
(**) fglrx(0): *Mode "1776x1000": 69.2 MHz (scaled from 0.0 MHz), 31.1 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1776x1000"   69.18  1776 1824 2000 2224  1000 1001 1004 1037 interlace +hsync
(**) fglrx(0):  Default mode "1776x1000": 56.1 MHz (scaled from 0.0 MHz), 25.8 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "1776x1000"   56.08  1776 1800 1976 2176  1000 1001 1004 1031 interlace +hsync
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[7] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[8] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[9] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[10] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[11] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[12] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[13] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[14] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[15] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[16] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[17] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[22] 0	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[26] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[27] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[28] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[29] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[30] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[31] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[32] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[33] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[34] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[35] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[36] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[37] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[38] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[39] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[40] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): GART is not initialized, disabling DRI
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
(WW) fglrx(0): Failed to set up write-combining range (0xc0000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1080) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1920 x 7111
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "AddARGBGLXVisuals" is not used
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
fbarea0->box.x1 0x00000000, fbarea0->box.y1 0x0000043b
fbarea0->box.x2 0x00000780, fbarea0->box.y2 0x0000043d
icon[0].start=0x7ef000
fbarea1->box.x1 0x00000000, fbarea1->box.y1 0x0000043d
fbarea1->box.x2 0x00000780, fbarea1->box.y2 0x0000043f
icon[1].start=0x7f3000
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 16 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```


and Xorg.21.log

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux desktop-linux 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.21.log", Time: Wed Sep  5 20:15:35 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 1028,01dd rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:19:0: chip 8086,104c card 1028,01dd rev 02 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01dd rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2812 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2822 card 1028,01dd rev 02 class 01,04,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01dd rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,7183 card 1028,0302 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71a3 card 1028,0303 rev 00 class 03,80,00 hdr 00
(II) PCI: 03:02:0: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 03:02:1: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 03:02:2: chip 1106,3104 card 1106,3104 rev 63 class 0c,03,20 hdr 80
(II) PCI: 03:03:0: chip 14f1,2f20 card 14f1,200f rev 00 class 07,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfefffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdfb00000 - 0xdfbfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV516 [ATI Radeon X1300/X1550 Series] rev 0, Mem @ 0xc0000000/28, 0xdfde0000/16, I/O @ 0xdc00/8, BIOS @ 0xdfe00000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV516 [ATI Radeon X1300 Pro Secondary] rev 0, Mem @ 0xdfdf0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[1] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[2] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[3] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[4] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[5] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[6] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[7] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[8] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[9] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[10] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[11] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[14] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[15] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[16] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[17] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[18] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[19] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[20] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[21] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[22] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[23] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[24] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[1] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[2] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[3] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[4] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[5] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[6] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[7] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[8] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[9] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[10] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[11] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[14] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[15] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[16] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[17] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[18] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[19] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[20] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[21] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[22] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[23] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[24] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[5] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[6] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[7] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[8] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[9] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[10] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[11] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[12] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[20] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[21] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[22] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[23] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[24] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[25] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[26] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[27] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[28] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[29] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[30] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[31] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[32] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[33] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x7183) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[5] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[6] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[7] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[8] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[9] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[10] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[11] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[12] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[20] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[21] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[22] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[23] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[24] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[25] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[26] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[27] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[28] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[29] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[30] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[31] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[32] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[33] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[34] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e6a98
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[5] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[6] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[7] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[8] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[9] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[10] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[11] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[12] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[23] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[24] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[25] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[26] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[27] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[28] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[29] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[30] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[31] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[32] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[33] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[34] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[35] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[36] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[37] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X1300/X1550 Series" (Chipset = 0x7183)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x0302)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfde0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV516
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: DEL  Model: d015  Serial#: 893796685
(II) fglrx(0): Year: 2007  Week: 25
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 47  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.639 redY: 0.332   greenX: 0.288 greenY: 0.597
(II) fglrx(0): blueX: 0.152 blueY: 0.081   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 119.0 MHz   Image Size:  473 x 296 mm
(II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) fglrx(0): Serial No: DT86776I5FAM
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: DELL E228WFP
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0010ac15d04d414635
(II) fglrx(0): 	19110103802f1e78ee8f30a355499827
(II) fglrx(0): 	145054a54b00714f8180010101010101
(II) fglrx(0): 	0101010101017c2e90a0601a1e403020
(II) fglrx(0): 	3600d9281100001a000000ff00445438
(II) fglrx(0): 	36373736493546414d0a000000fd0038
(II) fglrx(0): 	4b1e530e000a202020202020000000fc
(II) fglrx(0): 	0044454c4c20453232385746500a0080
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 37 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1080 (pitch 0)
(**) fglrx(0): *Mode "1920x1080": 81.6 MHz (scaled from 0.0 MHz), 33.6 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   81.64  1920 1984 2176 2432  1080 1081 1084 1119 interlace +hsync
(**) fglrx(0):  Default mode "1920x1080": 66.3 MHz (scaled from 0.0 MHz), 27.8 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   66.33  1920 1960 2152 2384  1080 1081 1084 1113 interlace +hsync
(**) fglrx(0): *Mode "1776x1000": 69.2 MHz (scaled from 0.0 MHz), 31.1 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1776x1000"   69.18  1776 1824 2000 2224  1000 1001 1004 1037 interlace +hsync
(**) fglrx(0):  Default mode "1776x1000": 56.1 MHz (scaled from 0.0 MHz), 25.8 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "1776x1000"   56.08  1776 1800 1976 2176  1000 1001 1004 1031 interlace +hsync
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (470, 300) mm
(--) fglrx(0): DPI set to (103, 91)
(--) fglrx(0): Virtual size is 1920x1080 (pitch 1920)
(**) fglrx(0): *Mode "1920x1080": 81.6 MHz (scaled from 0.0 MHz), 33.6 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   81.64  1920 1984 2176 2432  1080 1081 1084 1119 interlace +hsync
(**) fglrx(0):  Default mode "1920x1080": 66.3 MHz (scaled from 0.0 MHz), 27.8 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"   66.33  1920 1960 2152 2384  1080 1081 1084 1113 interlace +hsync
(**) fglrx(0): *Mode "1776x1000": 69.2 MHz (scaled from 0.0 MHz), 31.1 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1776x1000"   69.18  1776 1824 2000 2224  1000 1001 1004 1037 interlace +hsync
(**) fglrx(0):  Default mode "1776x1000": 56.1 MHz (scaled from 0.0 MHz), 25.8 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "1776x1000"   56.08  1776 1800 1976 2176  1000 1001 1004 1031 interlace +hsync
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +vsync
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   21.07  640 648 712 784  432 433 436 448 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfbf0000 - 0xdfbfffff (0x10000) MX[B]
	[7] -1	0	0xdfbeff00 - 0xdfbeffff (0x100) MX[B]
	[8] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[9] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[10] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[11] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[12] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[13] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[14] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[15] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[16] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[17] -1	0	0xdfde0000 - 0xdfdeffff (0x10000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[22] 0	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000ccb8 - 0x0000ccbf (0x8) IX[B]
	[26] -1	0	0x0000cce0 - 0x0000ccff (0x20) IX[B]
	[27] -1	0	0x0000ccc0 - 0x0000ccdf (0x20) IX[B]
	[28] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[29] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[30] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[31] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[32] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[33] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[34] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[35] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[36] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[37] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[38] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[39] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[40] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): GART is not initialized, disabling DRI
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
(WW) fglrx(0): Failed to set up write-combining range (0xc0000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1080) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1920 x 7111
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "AddARGBGLXVisuals" is not used
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
fbarea0->box.x1 0x00000000, fbarea0->box.y1 0x0000043b
fbarea0->box.x2 0x00000780, fbarea0->box.y2 0x0000043d
icon[0].start=0x7ef000
fbarea1->box.x1 0x00000000, fbarea1->box.y1 0x0000043d
fbarea1->box.x2 0x00000780, fbarea1->box.y2 0x0000043f
icon[1].start=0x7f3000
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support use Option "TexturedVideo".
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 16 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!





```



Sorry for the length of the post, any help would be great.

---

### Post by kystorms on 2007-10-22
ohhhh please help with this
i had the desktop customization... and then god only knows what i did and poof no more desktop customizing avilaable

here is the out puts i have gotton from what you wrote

fglrxinfo -display :0 (OUTPUT)
lisac@lisac-desktop:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1

lisac@lisac-desktop:~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
OpenGL version string: 1.2 (1.3 Mesa 7.0.1)


now my firefox, sooo slow.. .desktop is foobar.
thanks

---

### Post by athaki on 2007-10-22
Thank you for the how-to. I didn't realize how easy it has become to get xgl up and running on Gusty. :)

---

### Post by Apocalypse_666 on 2007-10-22
You tha man! I had it fixed within twenty minutes. Awesome howto. 
Just one thing remains: I have no splash screen when I log in, and it goes black for about 15 seconds before I go to my desktop. No big deal at all, but if you happen to know anything...

---

### Post by michael37 on 2007-10-22
> **Ozitraveller said:**
> Hi 

I have an ATI 9200SE video card. After I changed Preferences Effects to enable special effects, I get wobbly windows and I can drag between the desktops, so it seems ok. But I don't know how to see/use the cube.

Do I need to install anything else?

Could someone please point me to any docs about shortcut keys, and anything else useful.

Thanks

Click on System->Preference->Advanced Desktop Effects Settings

Click on "General Options", Desktop Size tab, and pick Horizontal Virtual Size 4, Vertical Virtual Size 1, Number of Desktops 1.

Enable Desktop Cube plugin, then enable Rotate Cube.

Enjoy -- and remember, all of this stuff is pretty new.  One change at a time -- so if something breaks, you know how to go back.

---

### Post by michael37 on 2007-10-22
> **itsbradman said:**
> in addition, here is what I get when I try to run sudo aticonfig --intitial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfa289f2 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d8d92b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d36050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:01 3817545    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:01 3817545    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7d12000-b7d13000 rw-p b7d12000 00:00 0 
b7d13000-b7d15000 r-xp 00000000 08:01 2588979    /lib/tls/i686/cmov/libdl-2.6.1.so
b7d15000-b7d17000 rw-p 00001000 08:01 2588979    /lib/tls/i686/cmov/libdl-2.6.1.so
b7d17000-b7d18000 rw-p b7d17000 00:00 0 
b7d18000-b7d1c000 r-xp 00000000 08:01 3818279    /usr/lib/libXdmcp.so.6.0.0
b7d1c000-b7d1d000 rw-p 00003000 08:01 3818279    /usr/lib/libXdmcp.so.6.0.0
b7d1d000-b7d1f000 r-xp 00000000 08:01 3818130    /usr/lib/libXau.so.6.0.0
b7d1f000-b7d20000 rw-p 00001000 08:01 3818130    /usr/lib/libXau.so.6.0.0
b7d20000-b7e64000 r-xp 00000000 08:01 2588758    /lib/tls/i686/cmov/libc-2.6.1.so
b7e64000-b7e65000 r--p 00143000 08:01 2588758    /lib/tls/i686/cmov/libc-2.6.1.so
b7e65000-b7e67000 rw-p 00144000 08:01 2588758    /lib/tls/i686/cmov/libc-2.6.1.so
b7e67000-b7e6a000 rw-p b7e67000 00:00 0 
b7e6a000-b7e8d000 r-xp 00000000 08:01 2588980    /lib/tls/i686/cmov/libm-2.6.1.so
b7e8d000-b7e8f000 rw-p 00023000 08:01 2588980    /lib/tls/i686/cmov/libm-2.6.1.so
b7e8f000-b7f7c000 r-xp 00000000 08:01 3818310    /usr/lib/libX11.so.6.2.0
b7f7c000-b7f80000 rw-p 000ed000 08:01 3818310    /usr/lib/libX11.so.6.2.0
b7f80000-b7f8d000 r-xp 00000000 08:01 3819506    /usr/lib/libXext.so.6.4.0
b7f8d000-b7f8e000 rw-p 0000d000 08:01 3819506    /usr/lib/libXext.so.6.4.0
b7f8e000-b7f8f000 rw-p b7f8e000 00:00 0 
b7f8f000-b7f96000 r-xp 00000000 08:01 3818455    /usr/lib/libXrender.so.1.3.0
b7f96000-b7f97000 rw-p 00006000 08:01 3818455    /usr/lib/libXrender.so.1.3.0
b7f97000-b7f9c000 r-xp 00000000 08:01 622763     /usr/lib/libXrandr.so.2.1.0
b7f9c000-b7f9d000 rw-p 00005000 08:01 622763     /usr/lib/libXrandr.so.2.1.0
b7fa5000-b7faf000 r-xp 00000000 08:01 2375735    /lib/libgcc_s.so.1
b7faf000-b7fb0000 rw-p 0000a000 08:01 2375735    /lib/libgcc_s.so.1
b7fb0000-b7fb3000 rw-p b7fb0000 00:00 0 
b7fb3000-b7fcd000 r-xp 00000000 08:01 1163454    /lib/ld-2.6.1.so
b7fcd000-b7fcf000 rw-p 00019000 08:01 1163454    /lib/ld-2.6.1.so
bfa14000-bfa2a000 rw-p bfa14000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

I am sorry you are experiencing problems.  I gave you a fair warning -- I have never troubleshooted Mesa problems, so no help in this thread.

---

### Post by michael37 on 2007-10-22
> **kystorms said:**
> ohhhh please help with this
i had the desktop customization... and then god only knows what i did and poof no more desktop customizing avilaable

here is the out puts i have gotton from what you wrote

fglrxinfo -display :0 (OUTPUT)
lisac@lisac-desktop:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1

lisac@lisac-desktop:~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX+/3DNow!+/SSE NO-TCL
OpenGL version string: 1.2 (1.3 Mesa 7.0.1)


now my firefox, sooo slow.. .desktop is foobar.
thanks

You OpenGL renderer is Mesa.  Please read the troubleshooting section about "Mesa nightmares"

---

### Post by michael37 on 2007-10-22
> **Apocalypse_666 said:**
> You tha man! I had it fixed within twenty minutes. Awesome howto. 
Just one thing remains: I have no splash screen when I log in, and it goes black for about 15 seconds before I go to my desktop. No big deal at all, but if you happen to know anything...

I have the same problem with one my LCD screens.  It can't seem to display the splash, but it displays desktop just fine.  I just wait :(

---

### Post by michael37 on 2007-10-22
> **Ozitraveller said:**
> Hi 

I have an ATI 9200SE video card. After I changed Preferences Effects to enable special effects, I get wobbly windows and I can drag between the desktops, so it seems ok. But I don't know how to see/use the cube.

Do I need to install anything else?

Could someone please point me to any docs about shortcut keys, and anything else useful.

Thanks

Here is another link that can help you customize Compiz.

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

I will add this link to the HOWTO.

---

### Post by michael37 on 2007-10-22
> **andrewpmoore said:**
> At the point you saw the logs I hadn't had envy on. I have since tried it (before reading this message of yours) but that didn't fix things, so I've removed it again.

Graphics card is a X1300 pro

If the X*.*.log files are of any use to help now, here they are:
........
Sorry for the length of the post, any help would be great.

This was excellent!  They key error message can be found in Xorg.0.log

```

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7c51000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *

```

Given that the version of "stock" fgrlx driver in Gutsy is 8.37.6 (see a snippet of the log from my laptop below) -- you DO have a bad driver!  It does not match kernel either.

```

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.37.6
(II) fglrx(0):     Date: May 25 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.

```

Here is what I would do (you are running Gutsy, ain't you?)
1. Verify that your kernel version is right
uname -r 
should be: 2.6.22-14-generic
2. Verify that packages are installed (first is the kernel itself, second contains our driver)
dpkg -l linux-image-2.6.22-14-generic
dpkg -l linux-restricted-modules-2.6.22-14-generic
3. Verify that you are booting into the right kernel
gedit /boot/grub/menu.list
The top section should be something like
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=blahblahblah ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

---

### Post by trv4gr on 2007-10-22
michael37, could you please post your xorg.conf file (and what ati card do you have).

I think an important part is missing from your instructions in the first page.

I personally have tried many many times in feisty to enable compiz/xgl with my ati 9800se but always failed.

Among the different guides there were several instructions to add certain commands in the xorg.conf file so as to configure some things in the driver, set some registers etc.

all those things resulted in me (and several others i suppose) to have a list of ~10 Option values like

>         Option          "AGPMask"       "0x00000010"    # For AGP v1-v2
        Option          "AGPv3Mask"     "0x00000010"    # For AGP v3
        Option "VideoOverlay" "off"
        Option "OpenGLOverlay" "off"

etc

After all that i do not know which of these lines are needed or not..

Well you get the point i think :)

---

### Post by michael37 on 2007-10-22
> **trv4gr said:**
> michael37, could you please post your xorg.conf file (and what ati card do you have).

I think an important part is missing from your instructions in the first page.
(....)
After all that i do not know which of these lines are needed or not..

Well you get the point i think :)

Thank you for a great suggestion.  Here it is.  It's divided per sections with my comments below each section.

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

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```
This is very generic, I don't modify the Files section.
```

Section "Module"
        Load    "i2c"
        Load    "bitmap"
	Load	"dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

```
I think these are defaults (except dbe (double buffering) -- someone told me it helps, but I am not sure).  Enabling more moduels doesn't hurt, but doesn't help either.  Feel free to experiment.
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

```
InputDevices are all defaults.
```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
  Option "UseInternalAGPGART" "no"
EndSection

```
The critical section.  It's very short.

I used to have two more options in this section, but subsequently removed them since they are already set by default.
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"

```

Section "Extensions"
	Option		"Composite"	"1"
EndSection

```
There are a lot of arguments whether Composite should be enabled and disabled in Gutsy.  It HAD to be disabled in Feisty.  In Gutsy, we use Xgl by default, and it implements Composite differently anyway.  Experiment with 1 and 0 here.
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

```
Can't be more boring.
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

```
DO NOT COPY THIS SECTION VERBATIM!!! This is specitic for my notebook screen.  If you have an LCD, you should have something that is relevant for your monitor.  If you need to change the resolution, run command
```
sudo dpkg-reconfigure -phigh xserver-xorg

```

```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```
*yawn* another default section.
```

Section "ServerFlags"
        Option      "Xinerama" "false"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
These two sections are important for fglrx.

---

### Post by ccannon on 2007-10-22
I'm hoping someone can help with my ATI problem, I can't get rid of the Mesa output.

Here is the requested output - thank you!
```

ccannon@Homer:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

```
ccannon@Homer:~$ fglrxinfo -display :1
Error: unable to open display :1
```
```
ccannon@Homer:~$ cat /etc/X11/xorg.conf

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
        Identifier      "Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
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
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Option          "VendorName"    "ATI Proprietary Driver"
        Option          "ModelName"     "Generic Autodetecting Monitor"
        Option          "DPMS"  "true"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]"
        Device          "aticonfig-Device[0]"
        Monitor         "aticonfig-Monitor[0]"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0       0
                Depth   24
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option          "Composite"     "1"
EndSection

```

---

### Post by michael37 on 2007-10-22
> **ccannon said:**
> I'm hoping someone can help with my ATI problem, I can't get rid of the Mesa output.

Here is the requested output - thank you!


Need more troubleshooting -- what does this command produce:

grep -C 8 'Kernel Module' /var/log/X*log

As I said in the earlier post, I have not run into 'Mesa nightmares', so I don't have first hand experience with it.  However, enough people ran into trouble with it that I decided to solve it once and for all :)

---

### Post by nahham on 2007-10-22
I am wondering if someone else has this problem:
Everything works fine for me expect for movie playback.  Certain movies with DivX5 and ffmpeg (as mentioned in the Audio/Video tab) codecs will have a green bar on top of the movie and the colors are also really bad.  If I disable XGL, then everything is fine.  Tried everything and don't seem to get it fixed while running XGL.  Any ideas?

nahham..

---

### Post by michael37 on 2007-10-22
> **nahham said:**
> I am wondering if someone else has this problem:
Everything works fine for me expect for movie playback.  Certain movies with DivX5 and ffmpeg (as mentioned in the Audio/Video tab) codecs will have a green bar on top of the movie and the colors are also really bad.  If I disable XGL, then everything is fine.  Tried everything and don't seem to get it fixed while running XGL.  Any ideas?

nahham..

First of all, check your xorg.conf.  You want to make to specify the following options in the "Device" section:

Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"

Just in case.  You need a X-server restart (Ctrl-Alt-Backspace) after you change xorg.conf.

Second, try playing your movies in VLC (sudo apt-get install vlc).  If the problem disappears (and I am 80% certain it will), the problem is with your movie player, not with Xgl.  IMHO I am less than impressed with Totem -- the default player.

---

### Post by nahham on 2007-10-22
I've tried all media players I can think of (mplayer, vlc, xine, movie player) all have the same problem.  I have also added 

```

Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"

```

to the device section and restarted X with no changes..

---

### Post by Goombie on 2007-10-22
Very nice howto you have here. Interestingly enough, it's almost exactly what I did to get my compiz working. Of course, I disabled it again because it broke my standby function, but still. :)

---

### Post by itsbradman on 2007-10-22
Thanks anyway!  All is ok, despite the lack of compiz.  I renofigured x and gnome came back no problem.  Guess I'll just wait for some fix to come about

---

### Post by michael37 on 2007-10-22
> **itsbradman said:**
> Thanks anyway!  All is ok, despite the lack of compiz.  I renofigured x and gnome came back no problem.  Guess I'll just wait for some fix to come about

Don't give up -- the 'Mesa nightmare' is fairly common and I am plugging away on a solution with a few users.  Stay tuned, maybe we'll have a solution for you.

---

### Post by nahham on 2007-10-22
Just as a follow-up to my earlier post.  Attached is how the video look like when compiz is enabled.

---

### Post by michael37 on 2007-10-22
> **nahham said:**
> Just as a follow-up to my earlier post.  Attached is how the video look like when compiz is enabled.

One of the weirder problems I've ever seen.  Something is not OK with your overlay settings (that's how movies display on your screen).

Backup your xorg.conf and try this:

sudo aticonfig --overlay-type=Xv

Maybe???

---

### Post by moairmoair on 2007-10-23
> **michael37 said:**
> If you are upgrading from Feisty 7.04 or earlier versions and you have run Xgl before.


Some of my applications  (Terminal, Places/HomeFolder ... ) become very slow to load after online upgrade to Gusty ( [http://ubuntuforums.org/showthread.php?p=3598763#post3598763](http://ubuntuforums.org/showthread.php?p=3598763#post3598763) ). There are suggestions  that it can be solved  by following your howto. I tried to do so but got the Mesa problem. The output of  fglrxinfo -display :0 and xorg.conf attached below. fglrxinfo -display :1 produces nothing. 

In addition to getting the 3D effects, any idea how to solve the slow loading problem?

Thanks

```

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1


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
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "int10"
        Load            "vbe"
        Load            "glx"
        Load            "GLcore"
        Load            "dri"
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
        Identifier      "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Boardname       "ATI Radeon"
        Busid           "PCI:1:0:0"
        Driver          "ati"
        Screen  0
        Vendorname      "ATI"
        Option          "MergedFB"      "off"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1024x768"
        Horizsync       31.5-48.0
        Vertrefresh     56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1024    768
                Modes           "1024x768@60"   "800x600@60"    "800x600@56"    "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
Section "device" #  
        Identifier      "device1"
        Boardname       "ATI Radeon"
        Busid           "PCI:1:0:0"
        Driver          "ati"
        Screen  1
        Vendorname      "ATI"
        Option          "MergedFB"      "off"
EndSection
Section "screen" #  
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
                Depth   24
                Modes           "640x480@60"
        EndSubSection
EndSection
Section "monitor" #  
        Identifier      "monitor1"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by latheesan on 2007-10-23
I've dont a clean install of Gutsy on my laptop, on top of windows

I got ATI Radeon Mobility X300 card, i saw on your list of supported card, so im quite happy about that, also a bit worried.

Last time i enabled ati drivers in restricted driver manager or installed ati drivers using Envy, all my effects stopped working. Every time i try to enable it, it kept giving me an error (which i forgot already, sorry).

So, my question is, if i followed your guide, will i be able to get most of the cool features compiz fusion offers,3D Cube for example (part of the reason why i installed Ubuntu in the first place).

I've already re-installed Guntsy like 5 times due to the stupid errors and the effects that stopped working after installing ati drivers. So, im actually running the Gutsy without any drivers and the extra effects that comes with Gutzy seems to work fine atm.

---

### Post by Legace on 2007-10-23
Yes, XGL will provide the support for the effects..

But, I think you should wait until ATI releases the restricted flgrx driver which supports the effects :)

---

### Post by ccannon on 2007-10-23
> **michael37 said:**
> Need more troubleshooting -- what does this command produce:

grep -C 8 'Kernel Module' /var/log/X*log

As I said in the earlier post, I have not run into 'Mesa nightmares', so I don't have first hand experience with it.  However, enough people ran into trouble with it that I decided to solve it once and for all :)

Thank You very much for you time, its people like you who will make Ubuntu successful.

Here is the requested output.
```

ccannon@Homer:~$ grep -C 8 'Kernel Module' /var/log/X*log
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7f93000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.37.6
(II) fglrx(0):     Date: May 25 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7f93000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
ccannon@Homer:~$
```

---

### Post by speedwell68 on 2007-10-23
> **michael37 said:**
> Well, let's try here and see if I can help you... If yes, I will create a Wiki page.

[SIZE="7"]Before we begin -- supported hardware list[/SIZE]

*Taken from fglrx driver description for Gutsy.*

This version of the ATI driver officially supports:

 * FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400,
           V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128,
           X1-128, X1-256p
 * FireMV: 2200 (Single card PCI-e configuration)
 * Mobility FireGL: V5000, T2
 * Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300,
                    9800, 9600, 9550, 9500
 * Radeon Xpress: 200M series, 1250 IGP, 200 series
 * Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550,
           X300, 9800, 9700, 9600, 9550, 9500

ATI All-in-Wonder variants of the above cards/chips are also supported,
but video capture is not.

[SIZE="7"]If you are doing fresh install of Gutsy[/SIZE]

[LIST=1]
[*]Enable fgrlx driver.

Install linux-restricted-modules and restricted-manager provied in the restricted repositories:
```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". 

[*]Install xserver-xgl package
```
sudo apt-get install xserver-xgl
```
[*]Install compiz
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
```
[*]Reboot
[*]Log in.  3D effects should be enabled!
[*]Customize Compiz Fusion.
Select System &#8594; Preferences &#8594; Advanced Desktop Effects Settings
In the new window, General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size.  Set it to 4.
The other two options have to be left at 1.

Continue customization per Forlong's guide at [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

[/LIST]

This worked a treat in a clean install of Gutsy AMD 64 using a ATI Radeon Xpress 1100.:KS

---

### Post by volty on 2007-10-23
I'm in a similar boat, but not quite the same one. I just got an old Dell 5150 laptop from teh gf, and it comes with a very outdated and no longer supported Mobility Radeon 9000. The issue is, the latest drivers to support this heap of crap are fglrx 8.28.8, which I downloaded.

I uninstalled the version that Gutsy installed automatically, and reinstalled this version using a .deb package from the fglrx site itself.

Right now, nothing seems to work. Using the "ati" driver sucks, using the "vesa" driver sucks, and using the "fglrx" driver sucks. All are chosen after Ctrl-Alt-F4 and using "sudo dpkg-reconfigure xserver-xorg" and sometimes i can get it to switch into low-visuals mode, or whatever, allowing gnome to finally start.

I've tried searching my *** off on the forums, and there are a few others of us, but nobody's gotten a decent fix. 

Anyway, the restricted drivers manager doesnt recognize that I need a restricted driver (although it did get the broadcom wireless card right off, woot!) Here's some outputs.

xorg.conf
```
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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Except looking in the xorg.0.log file, its using xorg.conf.failsafe, which is:
```
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
        Disable         "dbe"
        Disable         "dri"
        Disable         "glx"
        Disable         "vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth	16
		Modes   "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Obviously, the fglrx driver isnt even being used. 

Any ideas? I'm at wit's end, and about to stick feisty back on.

---

### Post by nahham on 2007-10-23
> **michael37 said:**
> One of the weirder problems I've ever seen.  Something is not OK with your overlay settings (that's how movies display on your screen).

Backup your xorg.conf and try this:

sudo aticonfig --overlay-type=Xv

Maybe???

Well I've tried that too, its no good.  Using the ati driver the movies display fine but without compiz fusion.  The proprietary is the only driver that gives me problems with the movie playback. I wish I got a laptop with an nividia chip.

---

### Post by awhite on 2007-10-23
I have the exact same issue you had at the start of this thread.  Two displays, No DRI on :1, DRI on :0 but 3D applications aren't working with it.

Compiz works fine.
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Series
OpenGL version string: 2.0.6747 (8.40.4)

As you can see I'm using the newest drivers.

If I disable xgl, I lose compiz but 3D applications work.  (I have one display with DRI)

Can compiz/fglrx/xgl work while still allowing 3D applications to run?  Or does xgl prevent 3D applications from accessing the DRI?

-Arlo

---

### Post by itsbradman on 2007-10-23
Will do.  If there is anything I can post in here, do let me know.

---

### Post by itsbradman on 2007-10-23
> **michael37 said:**
> Don't give up -- the 'Mesa nightmare' is fairly common and I am plugging away on a solution with a few users.  Stay tuned, maybe we'll have a solution for you.

Let me know if there is anything I can do to help.

---

### Post by jwm0z on 2007-10-23
> **michael37 said:**
> cor2y problem is totally different -- it's only about emerald.  His compiz is working fine.

What alternate session are you referring to?  In Gutsy, Xgl always run and no alternate sessions are ever needed.  Big difference from Feisty.

Try this command and see what is your WM default:

```

gconftool-2 -g /desktop/gnome/applications/window_manager/default

```

If it's not compiz, try to set it to compiz

```

gconftool-2 -s /desktop/gnome/applications/window_manager/default /usr/bin/compiz --type string

```

I also had the same issue where I could get compiz to work manually.  Following these instructions it now works on boot up.

---

### Post by myk.dinis on 2007-10-23
Xlib: extension "GLX" missing on display ":0:0".
Xlib: extension "GLX" missing on display ":0:0".
Error: couldn't find RGB GLX visual!

That's my current error!

Yay...

myk

---

### Post by michael37 on 2007-10-24
> **myk.dinis said:**
> Xlib: extension "GLX" missing on display ":0:0".
Xlib: extension "GLX" missing on display ":0:0".
Error: couldn't find RGB GLX visual!

That's my current error!

Yay...

myk

Please post your /etc/X11/xorg.conf

---

### Post by michael37 on 2007-10-24
> **awhite said:**
> I have the exact same issue you had at the start of this thread.  Two displays, No DRI on :1, DRI on :0 but 3D applications aren't working with it.

Compiz works fine.
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Series
OpenGL version string: 2.0.6747 (8.40.4)

As you can see I'm using the newest drivers.

If I disable xgl, I lose compiz but 3D applications work.  (I have one display with DRI)

Can compiz/fglrx/xgl work while still allowing 3D applications to run?  Or does xgl prevent 3D applications from accessing the DRI?

-Arlo

3D applications work for me.

Try running

glxheads :1
glxheads :0

Both should work (except the one with :0 will not display a Windows Decoration)

---

### Post by michael37 on 2007-10-24
> **awhite said:**
> I have the exact same issue you had at the start of this thread.  Two displays, No DRI on :1, DRI on :0 but 3D applications aren't working with it.

Compiz works fine.
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Series
OpenGL version string: 2.0.6747 (8.40.4)

As you can see I'm using the newest drivers.

If I disable xgl, I lose compiz but 3D applications work.  (I have one display with DRI)

Can compiz/fglrx/xgl work while still allowing 3D applications to run?  Or does xgl prevent 3D applications from accessing the DRI?

-Arlo

Using "newest" drivers may actually be your problem.  I do NOT recommend running Envy drivers unless you really need them.  They cause more problems than they solve.  Try removing the 8.40 driver in favor of the standard Gutsy 8.39 driver provided by restricted-modules and xorg-driver-fglrx package.

---

### Post by michael37 on 2007-10-24
> **nahham said:**
> Well I've tried that too, its no good.  Using the ati driver the movies display fine but without compiz fusion.  The proprietary is the only driver that gives me problems with the movie playback. I wish I got a laptop with an nividia chip.

I am sorry to say, but I think it's got to be a bug in the proprietary driver for your specific hardware package.  I looked through ccsm (Advanced Desktop Effects Settings) and don't see any compiz options that can help you.... well, maybe except "workarounds" plugin -- maybe try enabling it and see if that helps.

---

### Post by romana on 2007-10-24
I am running  : ATI Technologies Inc Radeon IGP 330M/340M/350M

Does anyone know how to get fglrx working for this card? I can get the ati drivers working, but desktop effects are out, and neverwinter nights is a cow. it should play nicely on this (i have had previous, lesser laptops with lesser ati cards using fglrx and neverwinter nights worked a treat), but for some reason, fglrx and xgl are nonos with this card. it seems to be common from what i have seen. 
( eg [http://ubuntuforums.org/showthread.php?t=580963](http://ubuntuforums.org/showthread.php?t=580963) )

help? desperately frustrated by it all. grumble.

---

### Post by michael37 on 2007-10-24
> **volty said:**
> I'm in a similar boat, but not quite the same one. I just got an old Dell 5150 laptop from teh gf, and it comes with a very outdated and no longer supported Mobility Radeon 9000. The issue is, the latest drivers to support this heap of crap are fglrx 8.28.8, which I downloaded.
(...)
Obviously, the fglrx driver isnt even being used. 

Any ideas? I'm at wit's end, and about to stick feisty back on.

I am afraid Feisty is your best choice.  Fighting with old custom drivers is awful -- you will have problems with AGPGART driver, xorg, etc etc etc.

---

### Post by michael37 on 2007-10-24
> **latheesan said:**
> I've dont a clean install of Gutsy on my laptop, on top of windows

I got ATI Radeon Mobility X300 card, i saw on your list of supported card, so im quite happy about that, also a bit worried.

Last time i enabled ati drivers in restricted driver manager or installed ati drivers using Envy, all my effects stopped working. Every time i try to enable it, it kept giving me an error (which i forgot already, sorry).

So, my question is, if i followed your guide, will i be able to get most of the cool features compiz fusion offers,3D Cube for example (part of the reason why i installed Ubuntu in the first place).

I've already re-installed Guntsy like 5 times due to the stupid errors and the effects that stopped working after installing ati drivers. So, im actually running the Gutsy without any drivers and the extra effects that comes with Gutzy seems to work fine atm.

The answer is definitely.  Do not use Envy (or uninstall it and wipe it and etc) and follow my HOWTO.  If you are system that messed up, I recommend fresh install.

---

### Post by michael37 on 2007-10-24
> **moairmoair said:**
> Some of my applications  (Terminal, Places/HomeFolder ... ) become very slow to load after online upgrade to Gusty ( [http://ubuntuforums.org/showthread.php?p=3598763#post3598763](http://ubuntuforums.org/showthread.php?p=3598763#post3598763) ). There are suggestions  that it can be solved  by following your howto. I tried to do so but got the Mesa problem. The output of  fglrxinfo -display :0 and xorg.conf attached below. fglrxinfo -display :1 produces nothing. 

In addition to getting the 3D effects, any idea how to solve the slow loading problem?

Thanks

```

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

```


You are not using the FGLRX driver.  Have you enabled it in step 8 via Restricted Drivers Manager?

1.  Verify that you are trying to use fglrx driver in /etc/X11/xorg.conf
2. Verify that fgrlx driver package is installed
dpkg -l xorg-server-fglrx

---

### Post by michael37 on 2007-10-24
> **ccannon said:**
> Thank You very much for you time, its people like you who will make Ubuntu successful.

Here is the requested output.
```

(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work

```

Please send me the output of 

uname -r
lsmod | grep fglrx
dpkg -l xorg-driver-fglrx
dpkg -l linux-restricted-modules-2.6.22-14-generic
dpkg -S /usr/lib/xorg/modules/drivers/fglrx_drv.so
modinfo fglrx
grep -A 3 'ATI Technologies' /var/log/messages

Please feel free to use PM since I am very interested in getting to the bottom of this particular problem.

---

### Post by maxxum on 2007-10-24
I followed your HOWTO. I am glad its working for so many others. No luck for me yet. I have ATI X300 card in my Dell 9150 desktop. As soon as I install xserver-xgl the system becomes unusable after the restart. The desktop appears but with rectangular and triangular huge black spots that appear and disappear. Sometimes they are white. Scrolling a few lines in firefox took 10 mins. The system is extremely slow. So far I have installed compiz manager, using fglrx and have installed xserver-xgl (which I am going to have to uninstall, it seems).

fglrxinfo: ```

display :0.0  screen 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6473 (8.37.6) 
```

sudo compiz```

Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did nore receive a reply. Possible causes include: the remote application did not send a reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (core) - Error: couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```
glxinfo```
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
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
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

### Post by myk.dinis on 2007-10-24
Well, did a full re-install of gutsy and it pretty much found everything like a charm...

I can't believe that the upgrade didn't do the trick...but hey...whaddya gonna do?

Cheers!
Myk

---

### Post by myk.dinis on 2007-10-24
Hey, I have a weird problem...

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

Any ideas? I followed the guide perfectly...

All I know is X is insanely slow now...and I'm not sure why...

The guide worked fine...the desktop was peppy and good! I have a x700 with 128MB and 2GB of RAM...
Wacky Wacky,...

But lke I was saying it ran fine then I decided that the cpu load was way too high and turned compiz (desktop effects) off and all of a sudden I had weird areas on the screen that didn't work and whatnot...

Very confused...

myk

---

### Post by michael37 on 2007-10-24
> **maxxum said:**
> I followed your HOWTO. I am glad its working for so many others. No luck for me yet. I have ATI X300 card in my Dell 9150 desktop. As soon as I install xserver-xgl the system becomes unusable after the restart. The desktop appears but with rectangular and triangular huge black spots that appear and disappear. Sometimes they are white. Scrolling a few lines in firefox took 10 mins. The system is extremely slow. So far I have installed compiz manager, using fglrx and have installed xserver-xgl (which I am going to have to uninstall, it seems).


Your config is fine -- 3D acceleration by the ATI binary driver is enabled on your video card.  Here are a few questions: what is resolution of your monitor?  Is it high?  Consider reducing it.  How much on-board memory do you have on your video card?  Or does it use shared main memory?  The 3D effects are very intensive on the video memory of the system.  I think you either have too little (or too slow?) video RAM or ATI binary driver doesn't work for you.

Here is what I would do.
1. Reduce your resolution.  See if it gets better.  If it's a memory problem, it would.
2. Upgrade to  8.40 ATI driver using [Envy](http://albertomilone.com/nvidia_scripts1.html).
[B]
For everyone else -- this is not a generic suggestion -- you must have problems like maxxum to consider these suggestions, especially Envy.[/B]

---

### Post by michael37 on 2007-10-24
> **myk.dinis said:**
> Hey, I have a weird problem...

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

Any ideas? I followed the guide perfectly...

All I know is X is insanely slow now...and I'm not sure why...

The guide worked fine...the desktop was peppy and good! I have a x700 with 128MB and 2GB of RAM...
Wacky Wacky,...

But lke I was saying it ran fine then I decided that the cpu load was way too high and turned compiz (desktop effects) off and all of a sudden I had weird areas on the screen that didn't work and whatnot...

Very confused...

myk

Your system is working fine.  AIGLX is not supposed to work on ATI cards -- it works only on Nvidia and Intel.  We use Xgl  for 3d effects instead (conversely, installing Xgl on an Intel video card will break everything).

---

### Post by michael37 on 2007-10-24
> **romana said:**
> I am running  : ATI Technologies Inc Radeon IGP 330M/340M/350M

Does anyone know how to get fglrx working for this card? I can get the ati drivers working, but desktop effects are out, and neverwinter nights is a cow. it should play nicely on this (i have had previous, lesser laptops with lesser ati cards using fglrx and neverwinter nights worked a treat), but for some reason, fglrx and xgl are nonos with this card. it seems to be common from what i have seen. 
( eg [http://ubuntuforums.org/showthread.php?t=580963](http://ubuntuforums.org/showthread.php?t=580963) )

help? desperately frustrated by it all. grumble.

I do not believe fglrx driver supports your hardware.  Keep using the radeon driver.

---

### Post by maxxum on 2007-10-24
> **michael37 said:**
> Your config is fine -- 3D acceleration by the ATI binary driver is enabled on your video card.  Here are a few questions: what is resolution of your monitor?  Is it high?  Consider reducing it.  How much on-board memory do you have on your video card?  Or does it use shared main memory?  The 3D effects are very intensive on the video memory of the system.  I think you either have too little (or too slow?) video RAM or ATI binary driver doesn't work for you.

Here is what I would do.
1. Reduce your resolution.  See if it gets better.  If it's a memory problem, it would.
2. Upgrade to  8.40 ATI driver using [Envy](http://albertomilone.com/nvidia_scripts1.html).
[B]
For everyone else -- this is not a generic suggestion -- you must have problems like maxxum to consider these suggestions, especially Envy.[/B]
The video card has 128MB if dedicated video memory. The monitor is Dell 2407 LCD which is a 24in and has 1920x1200 native resolution. I will try to run it at 1025x768 and report back but from what I remember, it didn't really help in the past. The refresh rate somehow becomes too low even though it shows it is at 60Hz. Also I will try the 8.40 ATI driver though I have read it is slow as well. :)
Maybe I shold invest 40 bucks in an Nvidia card and get rid of these issues forever! I hear that ATI is working on AIGLX drivers, so that hope stops me from buying a new card.

---

### Post by michael37 on 2007-10-24
> **maxxum said:**
> The video card has 128MB if dedicated video memory. The monitor is Dell 2407 LCD which is a 24in and has 1920x1200 native resolution. I will try to run it at 1025x768 and report back but from what I remember, it didn't really help in the past. The refresh rate somehow becomes too low even though it shows it is at 60Hz. Also I will try the 8.40 ATI driver though I have read it is slow as well. :)
Maybe I shold invest 40 bucks in an Nvidia card and get rid of these issues forever! I hear that ATI is working on AIGLX drivers, so that hope stops me from buying a new card.

Yes, AIGLX is supposed to come in 8.43 for your hardware.  8.42 has AIGLX support, but only for 2000HD cards.

---

### Post by ubuntu dave on 2007-10-24
> **michael37 said:**
> Yes, AIGLX is supposed to come in 8.43 for your hardware.  8.42 has AIGLX support, but only for 2000HD cards.

8.42.3 (latest ATI drivers) working with AIGLX on an x800xt here. I don't think the driver's only for 2000HD/+ cards.

---

### Post by vides2012 on 2007-10-24
:Kneeel: :Respect: :Worship: ...

omg it works!!!!

after a couple of days of suffering, finally it works!!!

I had Mesa issue, but your troubleshoot, and [this page]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") helped me through!

Thanks!

---

### Post by Baneat on 2007-10-24
E: Couldn't find package xserver-xgl

AARGH! Linux for human beings? help me out here, when I try to install the above package it's not found.I'm connected to the internet, by the way.

---

### Post by michael37 on 2007-10-24
> **Baneat said:**
> E: Couldn't find package xserver-xgl

AARGH! Linux for human beings? help me out here, when I try to install the above package it's not found.I'm connected to the internet, by the way.

Click on System->Administration->Software Sources
Check all four buttons in the first Ubuntu Software tab:
Main, Universe, Restricted, Multiverse

---

### Post by michael37 on 2007-10-24
> **ubuntu dave said:**
> 8.42.3 (latest ATI drivers) working with AIGLX on an x800xt here. I don't think the driver's only for 2000HD/+ cards.

From [the official press release](http://www.phoronix.com/scan.php?page=article&item=887&num=1), it has issues with older cards and it has major issues with 64-bit support.  IMHO the product is not ready.  Oh yeah, I am x86_64 user.

I'm waiting for 8.43 before I recommend a newer ATI driver to anyone.  In any case, the as-officially-supported-as-it-can-be 8.37 driver works for most users, Xgl works fine, is easy to configure, a custom driver is hard to install for anyone but expert users, so I strongly advise against newer drivers.

---

### Post by ahrr on 2007-10-25
Michael,

i see your the wizard here...so here is may situation:

i have a very fresh install of gutsy, internet working but no 3D.

when i want to enable ATI drivers i get:

The software source for the package

  xorg-driver-fglrx

is not enabled.

outputs of a set of commands you asked someone else are

* uname -r

2.6.22-14-generic

* lsmod | grep fglrx

no output (just like is ignored

* dpkg -l xorg-driver-fglrx

No packages found matching xorg-driver-fglrx.

*  dpkg -l linux-restricted-modules-2.6.22-14-generic
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-restrict 2.6.22.4-14.9  Non-free Linux 2.6.22 modules on x86/x86_64

*  dpkg -S /usr/lib/xorg/modules/drivers/fglrx_drv.so

dpkg: /usr/lib/xorg/modules/drivers/fglrx_drv.so not found.

*  modinfo fglrx

filename:       /lib/modules/2.6.22-14-generic/volatile/fglrx.ko
depends:        agpgart
vermagic:       2.6.22-14-generic SMP mod_unload 586 
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
parm:           firegl:charp

* grep -A 3 'ATI Technologies' /var/log/messages

no output (ignored again)

in adition trying to install gives me:

* sudo apt-get install xorg-driver-fglrx

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx

I also have to say that neither Synaptic makes updates from internet, but asks for CD...

I'm lost! As i see the things is quite big, but i don't know much, i'm noob in this.

Thanks in advance for any suggestions!

---

### Post by michael37 on 2007-10-25
> **ahrr said:**
> Michael,

i see your the wizard here...so here is may situation:

i have a very fresh install of gutsy, internet working but no 3D.

when i want to enable ATI drivers i get:

The software source for the package

  xorg-driver-fglrx

is not enabled.

outputs of a set of commands you asked someone else are

* uname -r

2.6.22-14-generic

* lsmod | grep fglrx

no output (just like is ignored

* dpkg -l xorg-driver-fglrx

No packages found matching xorg-driver-fglrx.

*  dpkg -l linux-restricted-modules-2.6.22-14-generic
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-restrict 2.6.22.4-14.9  Non-free Linux 2.6.22 modules on x86/x86_64

*  dpkg -S /usr/lib/xorg/modules/drivers/fglrx_drv.so

dpkg: /usr/lib/xorg/modules/drivers/fglrx_drv.so not found.

*  modinfo fglrx

filename:       /lib/modules/2.6.22-14-generic/volatile/fglrx.ko
depends:        agpgart
vermagic:       2.6.22-14-generic SMP mod_unload 586 
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
parm:           firegl:charp

* grep -A 3 'ATI Technologies' /var/log/messages

no output (ignored again)

in adition trying to install gives me:

* sudo apt-get install xorg-driver-fglrx

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx

I also have to say that neither Synaptic makes updates from internet, but asks for CD...

I'm lost! As i see the things is quite big, but i don't know much, i'm noob in this.

Thanks in advance for any suggestions!

Click on System->Administration->Software Sources
Check all four buttons in the first Ubuntu Software tab:
Main, Universe, Restricted, Multiverse

That will allow your restricted packages.

Then do 
```

sudo apt-get install restricted-manager
```

Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver".

If you don't have a selection for ATI accelerated graphics driver, then your hardware is not supported.

If you do enable that selection, follow the rest of the howto after that.

---

### Post by rgrig on 2007-10-25
After following this guide compiz works just fine. (I disabled it because I don't like flying windows but that's another story: I want to have it working for (flying) windows fans. This doesn't matter: Thanks for the very good howto.)

The problem is that somehow fonts in emacs got messed up. That is, they are become really hard to read because they are rendered improperly. Any idea what might be wrong?

Incidentally, I had the same problem when I upgraded to feisty and the solution was to change all references to /usr/share/fonts/X11 to /usr/share/X11/fonts in xconf.org.

---

### Post by michael37 on 2007-10-25
> **rgrig said:**
> After following this guide compiz works just fine. (I disabled it because I don't like flying windows but that's another story: I want to have it working for (flying) windows fans. This doesn't matter: Thanks for the very good howto.)

The problem is that somehow fonts in emacs got messed up. That is, they are become really hard to read because they are rendered improperly. Any idea what might be wrong?

Incidentally, I had the same problem when I upgraded to feisty and the solution was to change all references to /usr/share/fonts/X11 to /usr/share/X11/fonts in xconf.org.

I had the same problem.  Go to System->Preferences->Appearance
Click on Fonts tab
Click on Details

and experiment with Resolution in DPI.

I had the best experience with DPI of 100 or more.

P.S. /usr/share/X11/fonts does not exist on Gutsy.

---

### Post by chipbuddy on 2007-10-25
> **michael37 said:**
> Well, let's try here and see if I can help you... If yes, I will ...

Thanks so much. i've been having some problems with the ati restricted drivers (black screen after load). it looks like installing xserver did the trick.

---

### Post by rgrig on 2007-10-25
> **michael37 said:**
> ...and experiment with Resolution in DPI.

Ironically, that setting affects all the fonts *except* those in emacs. That is, it affects exactly those fonts that already look pretty well.

> **michael37 said:**
> P.S. /usr/share/X11/fonts does not exist on Gutsy.

The file xorg.conf was overwritten during the upgrade to gutsy (so my changes for Feisty aren't there anymore).

---

### Post by praxis22 on 2007-10-25
How to improve fonts in Ubuntu, works like a charm:

[http://mozilla.doslash.org/ubuntu/fonts.html](http://mozilla.doslash.org/ubuntu/fonts.html)

---

### Post by rgrig on 2007-10-25
The following line added to .emacs fixed the problem for me: (set-default-font "-*-courier-medium-r-normal--18-180-75-75-m-110-iso8859-1")
I guess emacs stopped finding the font that used to be the default before following the guide in this thread. No idea why.

praxis22, I think that the fonts in Gutsy are much better than the MS fonts. The guide you link to was more useful for Feisty and before.

---

### Post by michael37 on 2007-10-25
> **rgrig said:**
> Ironically, that setting affects all the fonts *except* those in emacs. That is, it affects exactly those fonts that already look pretty well.

Another detail I forgot to mention -- I uninstalled emacs and installed Xemacs packages.  Maybe that helps.

---

### Post by michael37 on 2007-10-26
Just to make a statement -- there is a new driver available for ATI devices and there is a lot of "irrational exuberance" about it.  I have probably seen about 10 how-tos how to install this new driver.

Two points.

[LIST]
[*]Gutsy provides a very solid 8.37 driver.  Upgrade from that driver is NOT necessary for most ATI users except owners of 2000HD cards
[*]The new 8.42 driver has to be compiled.  Once installed, it's nearly impossible to uninstall if something goes wrong -- you would need to reinstall Gutsy.  Ouch.
[/LIST]

---

### Post by volty on 2007-10-26
Sonofabitch.

Does that mean I'm hamstrung when it comes to further releases down the road? (Assuming I cant manage to buy a newer machine...)

---

### Post by mrhirsh on 2007-10-26
To Michael37, or anyone else . . . HELP!!

I have a Toshiba Laptop, ATI Radeon X1200.  I had 7.04 and Compiz working relatively well.  I did have to do a generic video driver because I could not get the x1200 fully supported.  But it was working pretty well.  And I liked the Compiz interface.

Then I did something not so smart . . . I updated to 7.10 and the nightmare began.  First, no FlashPlayer.  Not the end of the world, but nice to be able to do it.  Got that fixed from the Synaptic Pkg. Mgr.  Then the next day, the sound went away.  Tried several fixes but nothing.  Sound isn't the end of the world, but again nice to have.

I also lost Compiz when I upgraded.  When I would go to the System>Administrator>Compiz Configuration it would do nothing.  Tried a few things, but again nothing.  Again, not the end of the world but I did enjoy the interface.

Reading around the forum here, seemed like it was a ATI conflict type issue, so I followed your suggestions per above.  Obviously, I did something terribly wrong and totally - and I mean TOTALLY goofed it.  I have no screen at all now.  Just a big black screen.  OK, it's not that big but I got nothing.  This qualifies as a big deal.

When I boot up I get a recovery option, but I don't know what I'm doing.  It does take me to the root directory, but I don't want to make matters worse.

Any help would be appreciated.  If it's not too much trouble, if any solutions could be emailed in addition to posted here, that would be hugely helpful.  [email]mrhirsh@integrity.com[/email]

Thanks in advance

---

### Post by athaki on 2007-10-26
I'd probably just do a fresh install, back up your personal files first though, then come back and follow the instructions. That's what I did and it worked for me. I hope you'll have the same success.

---

### Post by mrhirsh on 2007-10-26
How do I get to the personal files?  By the way I was running Windows XP on a virtual machine and need some files from there as well.


I don't have a monitor.

Thanks,

---

### Post by michael37 on 2007-10-26
> **mrhirsh said:**
> How do I get to the personal files?  By the way I was running Windows XP on a virtual machine and need some files from there as well.


I don't have a monitor.

Thanks,

Well, if you had a backup, it wouldn't be an issue.  But reinstall won't work for you if you have valuable data on that hard drive.

So, here is my suggestion.  Print "upgrade" how-to from this thread (first page).

Reboot into recovery mode.

Run through steps 1-4 (complete uninstall).

Reboot. 

Try to boot into "normal mode".  If you have screen, continue with howto step 6.

If you still have no screen, reboot again into "recovery mode" and run command
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

While running that, do not try to autodetect anything or you may hang again (you will go into the same blank screen as "normal mode" boot).   Select "ati" driver ( yes, ati and not fglrx -- we will enable fglrx when system is back to normal in step 8 ) and the rest of the options that match your notebook.

Reboot into normal mode -- it WILL work this time, you will be on step 6.

Continue with upgrade HOWTO.

---

### Post by Ozitraveller on 2007-10-26
> **michael37 said:**
> Click on System->Preference->Advanced Desktop Effects Settings

Click on "General Options", Desktop Size tab, and pick Horizontal Virtual Size 4, Vertical Virtual Size 1, Number of Desktops 1.

Enable Desktop Cube plugin, then enable Rotate Cube.

Enjoy -- and remember, all of this stuff is pretty new.  One change at a time -- so if something breaks, you know how to go back.

How can I visualize the cube so that I can see the whole cube rather than 1 face at a time?
Can you zoom to see the full cube effect?

I have wall turned off.

Thanks

---

### Post by boxymug on 2007-10-26
I am having similar problems with an Inspiron 600m, with an RV250-based card.  Even installing xserver-xgl means I must launch the failsafe GNOME session to log in.  

I cannot launch Compiz on its own, and when I do with SKIP_CHECKS, a portion of the screen is not drawn-to, and the entire thing is, well, a mess.  It's a clean install of Gutsy (after following the guide earlier today for clean installs, I went ahead and installed again). 

fglrxinfo:

```

The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found

```

sudo compiz

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 

```

glxinfo

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x57 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

xorg.conf:

```

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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```
Any help appreciated.

---

### Post by michael37 on 2007-10-27
> **Ozitraveller said:**
> How can I visualize the cube so that I can see the whole cube rather than 1 face at a time?
Can you zoom to see the full cube effect?

I have wall turned off.

Thanks

Try Ctrl-Alt-Left Mouse Button drag.  How's that?

You have to poke around the "key bindings" for each plugin in Advanced Desktop Effects Settings to see what command does what.

---

### Post by michael37 on 2007-10-27
> **boxymug said:**
> I am having similar problems with an Inspiron 600m, with an RV250-based card.  Even installing xserver-xgl means I must launch the failsafe GNOME session to log in.  

I cannot launch Compiz on its own, and when I do with SKIP_CHECKS, a portion of the screen is not drawn-to, and the entire thing is, well, a mess.  It's a clean install of Gutsy (after following the guide earlier today for clean installs, I went ahead and installed again). 
...


Go through Upgrade Howto (first page of this thread) -- it's a cleaner way even though you have reinstalled Gutsy from scratch.

Your restricted driver is NOT enabled.  You shouldn't install xserver-xgl unless you are showing proper fglrxinfo output in step 8 of upgrade process.

---

### Post by michael37 on 2007-10-27
> **boxymug said:**
> I am having similar problems with an Inspiron 600m, with an RV250-based card.  Even installing xserver-xgl means I must launch the failsafe GNOME session to log in.  

I cannot launch Compiz on its own, and when I do with SKIP_CHECKS, a portion of the screen is not drawn-to, and the entire thing is, well, a mess.  It's a clean install of Gutsy (after following the guide earlier today for clean installs, I went ahead and installed again). 

(skip)

sudo compiz

(skip)

Any help appreciated.

You should never run 'sudo compiz'.  Execute compiz as yourself 
```

compiz --replace

```

Please enable Restricted Driver even before you attempt compiz.

---

### Post by itsbradman on 2007-10-27
I did it!!!  OK, the prob is with the new drivers that comae with gutsy and xgl itself.  If everything was working in feisty and you are using a radeon m9000 with the "mesa" problem, what you do is uninstall xgl "sudo apt-get remove xserver-xgl".  Then you have to unistall the new drivers and reinstall the open source drivers from feisty.  A walkthrough is on this page:[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")
everything is working like a charm now!!!!

---

### Post by Jose Catre-Vandis on 2007-10-27
Thanks Michael37 for the howto and for the post of your xorg.conf. My clean Gutsy install seemed to leave out most of the modes, and DRI, the inclusion of these improved the workings and performance of the compiz desktop, making it much more usable and stable.

I also get the problem with the black screen and no splash after login. Even after I disabled xserver login and used a normal Gnome session, still no splash. Goning to try splash manager to see if it brings it back. Yes, an LCD screen.

[edit]

Installed splash manager:
```
sudo apt-get install gnome-splash-manager
```
on running splash manager (system>preferences) it shows no splash screen installed, so I found one on disk and installed it. Logged out, logged in, and hey presto my splash is back. 

Still have the black screen through, so will look for a fix for this?

---

### Post by kmt on 2007-10-27
I just found this thread because I'm experiencing the MESA problem:

```
$ fglrxinfo -display :0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

I am unable to fix it due to two things that are different than the usual.

First of all, when I choose: System | Administration | Restricted Driver Manager" the system tells me "Your hardware does not need any restricted drivers", although I remember very well that after the upgrade to Gutsy, Ubuntu advised me about a
restricted driver missing: ATI accelerated graphics driver.  At that time it was showing the restricted driver panel with three other (don't remember which ones) *unselected* restricted drivers.  Adding the ATI accelerated graphics driver fixed my graphics, which, before that were low-resolution/blurry immediately after the upgrade.

Second, I have a problem doing this:

```
$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbf86c9f9 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d8f92b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d38050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 09:00 538649     /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 09:00 538649     /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7d14000-b7d15000 rw-p b7d14000 00:00 0
b7d15000-b7d17000 r-xp 00000000 09:00 603299     /lib/tls/i686/cmov/libdl-2.6.1.so
b7d17000-b7d19000 rw-p 00001000 09:00 603299     /lib/tls/i686/cmov/libdl-2.6.1.so
b7d19000-b7d1a000 rw-p b7d19000 00:00 0
b7d1a000-b7d1e000 r-xp 00000000 09:00 538776     /usr/lib/libXdmcp.so.6.0.0
b7d1e000-b7d1f000 rw-p 00003000 09:00 538776     /usr/lib/libXdmcp.so.6.0.0
b7d1f000-b7d21000 r-xp 00000000 09:00 538771     /usr/lib/libXau.so.6.0.0
b7d21000-b7d22000 rw-p 00001000 09:00 538771     /usr/lib/libXau.so.6.0.0
b7d22000-b7e66000 r-xp 00000000 09:00 603242     /lib/tls/i686/cmov/libc-2.6.1.so
b7e66000-b7e67000 r--p 00143000 09:00 603242     /lib/tls/i686/cmov/libc-2.6.1.so
b7e67000-b7e69000 rw-p 00144000 09:00 603242     /lib/tls/i686/cmov/libc-2.6.1.so
b7e69000-b7e6c000 rw-p b7e69000 00:00 0
b7e6c000-b7e8f000 r-xp 00000000 09:00 603353     /lib/tls/i686/cmov/libm-2.6.1.so
b7e8f000-b7e91000 rw-p 00023000 09:00 603353     /lib/tls/i686/cmov/libm-2.6.1.so
b7e91000-b7f7e000 r-xp 00000000 09:00 543666     /usr/lib/libX11.so.6.2.0
b7f7e000-b7f82000 rw-p 000ed000 09:00 543666     /usr/lib/libX11.so.6.2.0
b7f82000-b7f8f000 r-xp 00000000 09:00 538679     /usr/lib/libXext.so.6.4.0
b7f8f000-b7f90000 rw-p 0000d000 09:00 538679     /usr/lib/libXext.so.6.4.0
b7f90000-b7f91000 rw-p b7f90000 00:00 0
b7f91000-b7f98000 r-xp 00000000 09:00 541005     /usr/lib/libXrender.so.1.3.0
b7f98000-b7f99000 rw-p 00006000 09:00 541005     /usr/lib/libXrender.so.1.3.0
b7f99000-b7f9e000 r-xp 00000000 09:00 537675     /usr/lib/libXrandr.so.2.1.0
b7f9e000-b7f9f000 rw-p 00005000 09:00 537675     /usr/lib/libXrandr.so.2.1.0
b7fa5000-b7faf000 r-xp 00000000 09:00 81449      /lib/libgcc_s.so.1
b7faf000-b7fb0000 rw-p 0000a000 09:00 81449      /lib/libgcc_s.so.1
b7fb0000-b7fb3000 rw-p b7fb0000 00:00 0
b7fb3000-b7fcd000 r-xp 00000000 09:00 1174498    /lib/ld-2.6.1.so
b7fcd000-b7fcf000 rw-p 00019000 09:00 1174498    /lib/ld-2.6.1.so
bf858000-bf86e000 rw-p bf858000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

$ sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
```

Turns out I had a bunch of xorg.conf files:

```
$ ls -la /etc/X11/xorg.conf*
-rw-r--r-- 1 root root 4285 2007-10-25 18:40 /etc/X11/xorg.conf.1
-rw-r--r-- 1 root root 6557 2007-10-25 20:09 /etc/X11/xorg.conf.2
-rw-r--r-- 1 root root 2180 2007-10-25 20:12 /etc/X11/xorg.conf.failsafe
-rw-r--r-- 1 root root 1451 2007-10-25 20:12 /etc/X11/xorg.conf.failsafe.1
-rw-r--r-- 1 root root 2096 2007-10-25 20:09 /etc/X11/xorg.conf.original-0

```

out of which of course xorg.conf.original-0 is my latest (the one that 'sudo aticonfig --initial' moved from xorg.conf):
```
$ cat /etc/X11/xorg.conf.original-0 
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
        Option          "XkbModel"      "pc104"
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

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "vesa"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1280x1024"
        Horizsync       31.5-64.0
        Vertrefresh     56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1280x1024@60"  "1280x960@60"   "1024x768@60"   "800x600@60"    "800x600@56"    "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

```

I have not restarted my machine after the 'sudo aticonfig --initial'.  What should I do?  I'm clueless at this point.  Please help!  Thank you!

---

### Post by michael37 on 2007-10-27
> **kmt said:**
> I just found this thread because I'm experiencing the MESA problem:
(...)
I have not restarted my machine after the 'sudo aticonfig --initial'.  What should I do?  I'm clueless at this point.  Please help!  Thank you!

You are not using the driver yet... instead, you are running with the low resolution vesa driver.

aticonfig --initial crashed (never seen that), so you were right copying back xorg.conf (or a reboot would get real hairy)

What video card do you have?   (command is case sensitive)
```

lspci | grep ATI

```

---

### Post by itsbradman on 2007-10-27
[QUOTE=kmt;3645074]I just found this thread because I'm experiencing the MESA problem:

```
$ fglrxinfo -display :0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

The only way I have gotten this to work is to use the open source driver and aiglx.  the proprietary driver and xgl does not work for me at all.  A list of card that are fully 3d supported with this method are:     *  7000 / rv100 based cards.
    * 7200 / R100 based cards.
    * 7500 / rv200 based cards.
    * 8X00 / R200 based cards.
    * 9000 / rv250 based cards.
    * 9100 / R200 based cards.
    * 9200 / rv280 based cards.

You'll have to uninstall xgl and follow the instructions on this page.
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

---

### Post by sonicmaker on 2007-10-28
Thanks for the how-to :)

I tried a gazillion times to get it working, unfortunately taking many wrong moves along the way, including installing the 8.42 drivers, using Envy and following steps by themselves when they seemed appropriate, but I was always getting the MESA error, and that's if it would work at all.

However after a complete fresh install of Gutsy I followed your how-to to the letter with version 8.41 drivers and it's now working very well indeed! Not quite as well as Vista's Aero interface on the same hardware (I dual-boot), but that's ok - it's way better than the jumpiness I was getting before the Gutsy reinstall!

Oh, and my hardware is an HD 2600 XT with 256MB on an Athlon X2 5200+ with 2GB.

Would be interested to find out if/when there'll be a set of drivers for these new HD 2000 series cards that are:
a. easy to install,
b. bulletproof, and
c. as functional as the Windows drivers

Thanks again :)

---

### Post by Nikos.Alexandris on 2007-10-28
I have an ATI 1250.

Editing the xorg.conf:

.Loading the   [COLOR="Red"]**"GLcore"**[/COLOR]   under **Section "Module"** [B][COLOR="Red"]MAKES SCROLLING SLOWER!
[/COLOR][/B]
.Adding under **Section "Screen"**
   [COLOR="Red"]**Option "XaaNoOffscreenPixmaps"**[/COLOR]  ** gives a bit more speed** -- I found that on an external post.

---

### Post by michael37 on 2007-10-28
> **sonicmaker said:**
> Thanks for the how-to :)

I tried a gazillion times to get it working, unfortunately taking many wrong moves along the way, including installing the 8.42 drivers, using Envy and following steps by themselves when they seemed appropriate, but I was always getting the MESA error, and that's if it would work at all.

However after a complete fresh install of Gutsy I followed your how-to to the letter with version 8.41 drivers and it's now working very well indeed! Not quite as well as Vista's Aero interface on the same hardware (I dual-boot), but that's ok - it's way better than the jumpiness I was getting before the Gutsy reinstall!

Oh, and my hardware is an HD 2600 XT with 256MB on an Athlon X2 5200+ with 2GB.

Would be interested to find out if/when there'll be a set of drivers for these new HD 2000 series cards that are:
a. easy to install,
b. bulletproof, and
c. as functional as the Windows drivers

Thanks again :)

Hi, the HD 2xxx cards are sore spot for ATI drivers since their support was introduced only in 8.41.  So, while Windows drivers existed for a while, you are literally running THE first available driver for HD 2xxx.  I'd give it about 3-6 month before the Linux installation becomes more or less integrated and bulletproof.

---

### Post by michael37 on 2007-10-28
> **Nikos.Alexandris said:**
> I have an ATI 1250.

Editing the xorg.conf:

.Loading the   [COLOR="Red"]**"GLcore"**[/COLOR]   under **Section "Module"** [B][COLOR="Red"]MAKES SCROLLING SLOWER!
[/COLOR][/B]
.Adding under **Section "Screen"**
   [COLOR="Red"]**Option "XaaNoOffscreenPixmaps"**[/COLOR]  ** gives a bit more speed** -- I found that on an external post.

Thank you for suggestions.  

1. GLcore:   I tried disabling GLcore, but fglrx driver loads it anyway.   Are you sure that it's not loading for you?

Here is my result of disabling GLcore:
```

$ grep -i -C 2 glcore /var/log/Xorg.0.log
        [26] -1 0       0x0000bf80 - 0x0000bf9f (0x20) IX[B]
        [27] -1 0       0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(WW) "GLcore" will not be loaded unless you've specified it to be loaded elsewhere.
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "dbe"
--
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3

```

2.  XAANoOffscreenPixmaps made no performance difference for me.  After some research, I see that this parameter affects only AIGLX users.  Since we are using fglrx driver with Xgl, we are actually not using AIGLX -- even as you see in my output above, AIGLX is erroring out as it should.

---

### Post by jw5801 on 2007-10-28
An interesting problem for you Michael! I had a perfectly working compiz setup, when I made the terrible mistake of attempting to upgrade to fglrx 8.42, which was immensely painful to even compile for 64-bit and once I finally made it, the driver wouldn't load, just reverted to mesa. Anyway, I quit and decided I'd have to put up with XGL for a while longer, so I reinstalled XGL, removed all traces (as far as I can tell) of the newer fglrx, reinstalled the fglrx from the repositories, put my xorg.conf back the way it was (I've since changed it to be slightly closer to yours), and now Compiz fails to load.```
jw5801@laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "run_command_10"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "run_command_11"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "run_command_12"

jw5801@laptop:~$ glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
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
jw5801@laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

jw5801@laptop:~$ cat /etc/X11/xorg.conf

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

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        BusID   "1:5:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "Generic Video Card"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Extensions"
        Option          "Composite"     "1"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "false"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

There's a massive bundle of potentially useless information there for you! I notice that GLX_EXT_texture_from_pixmap is listed under "glx server extensions" in glxinfo but not under "GLX extensions." I don't know whether this is normal or not but it's the only potential thing I could notice.

---

### Post by michael37 on 2007-10-28
> **jw5801 said:**
> An interesting problem for you Michael! I had a perfectly working compiz setup, when I made the terrible mistake of attempting to upgrade to fglrx 8.42, which was immensely painful to even compile for 64-bit and once I finally made it, the driver wouldn't load, just reverted to mesa. Anyway, I quit and decided I'd have to put up with XGL for a while longer, so I reinstalled XGL, removed all traces (as far as I can tell) of the newer fglrx, reinstalled the fglrx from the repositories, put my xorg.conf back the way it was (I've since changed it to be slightly closer to yours), and now Compiz fails to load.
<skip>
There's a massive bundle of potentially useless information there for you! I notice that GLX_EXT_texture_from_pixmap is listed under "glx server extensions" in glxinfo but not under "GLX extensions." I don't know whether this is normal or not but it's the only potential thing I could notice.

Could you please get me output of 
fglrxinfo -display :0
and 
fglrxinfo -display :1

Thanks.

---

### Post by Nikos.Alexandris on 2007-10-28
Thanks michael37 for the correct information.

But commenting the "GLcore" and restarting X (not rebooting) gave me the impression of a faster scrolling.

I will re-check my impression.

Thanks again,

Nikos.

---

### Post by jw5801 on 2007-10-28
> **michael37 said:**
> Could you please get me output of 
fglrxinfo -display :0
and 
fglrxinfo -display :1

Thanks.

```
jw5801@laptop:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

jw5801@laptop:~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```

---

### Post by tva995 on 2007-10-28
I have a radeon 9600 card... the card worked with the restricted driver  on feisty, but after a clean install of gutsy, nothing I do has gotten the driver to work... the restricted driver manager shows the driver as enabled but not in use... please help...

fglrxinfo gave the dreaded mesa answer... 

vlt@black:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

looks like wrong version on modules...

vlt@black:~$ dpkg -l linux-restricted-modules-2.6.22-14-generic
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-restrict 2.6.22.4-14.9  Non-free Linux 2.6.22 modules on x86/x86_64

no packages matching 2.6.22-14-generic

vlt@black:~$ dpkg -l linux-2.6.22-14-generic
No packages found matching linux-2.6.22-14-generic.

can't find fglrx

vlt@black:~$ lsmod | grep fglrx
vlt@black:~$ modinfo fglrx
modinfo: could not find module fglrx

wrong version of the xorg-driver-fglrx... I tried the uninstall and reinstall... after reboot just got the same wrong result...

vlt@black:~$ dpkg -l xorg-driver-fglrx
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  xorg-driver-fg 7.1.0-8.37.6+2 Video driver for ATI graphics accelerators

vlt@black:~$ cat /var/log/Xorg.0.log |grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) AIGLX: Screen 0 is not DRI capable


thanks for your postings... I would be grateful for any help here to get the restricted driver installed... thanks...

---

### Post by Nikos.Alexandris on 2007-10-28
> **michael37 said:**
> Thank you for suggestions.  

1. GLcore:   I tried disabling GLcore, but fglrx driver loads it anyway.   Are you sure that it's not loading for you?

Here is my result of disabling GLcore:
```

$ grep -i -C 2 glcore /var/log/Xorg.0.log
        [26] -1 0       0x0000bf80 - 0x0000bf9f (0x20) IX[B]
        [27] -1 0       0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(WW) "GLcore" will not be loaded unless you've specified it to be loaded elsewhere.
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "dbe"
--
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3

```

2.  XAANoOffscreenPixmaps made no performance difference for me.  After some research, I see that this parameter affects only AIGLX users.  Since we are using fglrx driver with Xgl, we are actually not using AIGLX -- even as you see in my output above, AIGLX is erroring out as it should.

Michael,

just wanted to thank you one more time for taking time and explaining how things are to everyone! Many times we follow blindly instructions... which is incorrect.

So... have a look (if you still are not fed-up!):

**GLcore:**
```
$ grep -i -C 2 glcore /var/log/Xorg.*
/var/log/Xorg.20.log-[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
/var/log/Xorg.20.log-(EE) AIGLX: Screen 0 is not DRI capable
/var/log/Xorg.20.log:(II) Loading local sub module "GLcore"
/var/log/Xorg.20.log:(II) LoadModule: "GLcore"
/var/log/Xorg.20.log:(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
/var/log/Xorg.20.log:(II) Module GLcore: vendor="X.Org Foundation"
/var/log/Xorg.20.log-   compiled for 1.3.0, module version = 1.0.0
/var/log/Xorg.20.log-   ABI class: X.Org Server Extension, version 0.3

```


**My system:**

* **Samsung R20, ATI [COLOR="Red"]X1250 IGP[/COLOR], 14.1" monitor, (uname -r=) [COLOR="Red"]2.6.22-14-generic[/COLOR]** **[COLOR="Red"]*and ATI driver 8.42.3!*[/COLOR]**

* **I have Rotating Cube and all kinds of effects. Video seems to be more or less ok.**

* **250 Frames/sec gives the built-in-compiz benchmark tool**. **[COLOR="Blue"]Is this acceptable?[/COLOR]**

* The **$ fgl_glxgears **gives
```
Using GLX_SGIX_pbuffer
4586 frames in 5.0 seconds = 917.200 FPS
5092 frames in 5.0 seconds = 1018.400 FPS
5076 frames in 5.0 seconds = 1015.200 FPS
5086 frames in 5.0 seconds = 1017.200 FPS
5069 frames in 5.0 seconds = 1013.800 FPS
5082 frames in 5.0 seconds = 1016.400 FPS
5097 frames in 5.0 seconds = 1019.400 FPS
5097 frames in 5.0 seconds = 1019.400 FPS
5099 frames in 5.0 seconds = 1019.800 FPS
5100 frames in 5.0 seconds = 1020.000 FPS
```

**[COLOR="Blue"]How are the two benchmarks related?[/COLOR]**

* **I can't set-up a clone mode with an external 20" monitor. Neither a Big-Desktop.** :(

* **Some info about fglrx:**
```

$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress 1200 Series
OpenGL version string: 2.0.6958 Release

$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
```

**and**

```
$ glxinfo|grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```

**[COLOR="Blue"]Why is glxinfo negative? Is glx irrelevant with fglrx?[/COLOR]**

* **More output:**

```
$ aticonfig --query-monitor
  Connected monitors: none
  Enabled monitors: none

```

**I always get that when I boot!** **I have to** "**[COLOR="Blue"]export DISPLAY=:0[/COLOR]**" in order to get ```
$ aticonfig --query-monitor
  Connected monitors: lvds
  Enabled monitors: lvds

```

**My xorg.conf is (without an external monitor):**

```
Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

```
```
Section "Files"
EndSection

```
```
Section "Module"
#	Load  "GLcore"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "v4l"
	Load  "dbe"
EndSection

```

**This part of the configuration is not so important I suppose.**
```
Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us,gr"
	Option	    "XkbVariant" ","
	Option	    "XkbOptions" "grp:shifts_toggle,lv3:ralt_switch,grp_led:scroll"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

```
```
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnableMonitor" "lvds"
	Option      "UseFastTLS" "2" [COLOR="Blue"]**--> I use this for Wine, as recommended in the ATI unofficial wiki.**[/COLOR]
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
#      Option	"XaaNoOffscreenPixmaps"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```
```
Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection

```

Keep on the good work! :)

---

### Post by advilandy on 2007-10-29
Hello, this is a good guide so far, and I know someone it worked for, but it's not working for me due to the infamous mesa issue. This has been going on for me for over a year...my card worked fine until I upgraded to edgy. I just installed gutsy this morning, so hopefully I can fix this with someone's help!

In the guide you say to check a few things, and a couple of them went wrong.

First, 
```
$ dpkg -l linux-2.6.22-14-generic
No packages found matching linux-2.6.22-14-generic.
```

Here are the outputs you requested:

```
$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

```

$ fglrxinfo -display :1
Xlib: connection to ":1.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
Error: unable to open display :1
```

---

### Post by michael37 on 2007-10-29
> **jw5801 said:**
> ```
jw5801@laptop:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

jw5801@laptop:~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```

Good news.  Your driver is working perfectly (if you ever played Warcraft, it'd be "It doesn't get any better than that").

It looks like either your Xgl or your Compiz are busted.  Follow the "upgrade" instructions (first page in this thread) and do steps 1-5 and then 14-18.  Skip all other steps (esp the ones related to work on drivers).

---

### Post by michael37 on 2007-10-29
> **tva995 said:**
> I have a radeon 9600 card... the card worked with the restricted driver  on feisty, but after a clean install of gutsy, nothing I do has gotten the driver to work... the restricted driver manager shows the driver as enabled but not in use... please help...

fglrxinfo gave the dreaded mesa answer... 

vlt@black:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

Ouch.  Dreaded Mesa nightmare indeed.

> **tva995 said:**
> looks like wrong version on modules...

vlt@black:~$ dpkg -l linux-restricted-modules-2.6.22-14-generic
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-restrict 2.6.22.4-14.9  Non-free Linux 2.6.22 modules on x86/x86_64

no packages matching 2.6.22-14-generic

vlt@black:~$ dpkg -l linux-2.6.22-14-generic
No packages found matching linux-2.6.22-14-generic.

Oops.  Typo (corrected in the original post) should be 
dpkg -l linux-image-2.6.22-14-generic

What's the output of 'uname -r'?

> 
can't find fglrx

vlt@black:~$ lsmod | grep fglrx
vlt@black:~$ modinfo fglrx
modinfo: could not find module fglrx

Now, that's a problem.  Try running

depmod -a
modinfo fglrx

Any better?

> 
wrong version of the xorg-driver-fglrx... I tried the uninstall and reinstall... after reboot just got the same wrong result...

vlt@black:~$ dpkg -l xorg-driver-fglrx
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  xorg-driver-fg 7.1.0-8.37.6+2 Video driver for ATI graphics accelerators

My fault, unclear instructions here (corrected in the original post now).  You are fine here.

> 
thanks for your postings... I would be grateful for any help here to get the restricted driver installed... thanks...

Well, your driver is not taking in.  Could you please answer some questions here and we'll go from there on.

---

### Post by michael37 on 2007-10-29
> **advilandy said:**
> Hello, this is a good guide so far, and I know someone it worked for, but it's not working for me due to the infamous mesa issue. This has been going on for me for over a year...my card worked fine until I upgraded to edgy. I just installed gutsy this morning, so hopefully I can fix this with someone's help!

In the guide you say to check a few things, and a couple of them went wrong.

First, 
```
$ dpkg -l linux-2.6.22-14-generic
No packages found matching linux-2.6.22-14-generic.
```

Here are the outputs you requested:

```
$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

```

$ fglrxinfo -display :1
Xlib: connection to ":1.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
Error: unable to open display :1
```

Try this:  

depmod -a
modinfo fglrx

What does that print?

---

### Post by michael37 on 2007-10-29
> **Nikos.Alexandris said:**
> Michael,

just wanted to thank you one more time for taking time and explaining how things are to everyone! Many times we follow blindly instructions... which is incorrect.

So... have a look (if you still are not fed-up!):

(skip)

* **Some info about fglrx:**
```

$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress 1200 Series
OpenGL version string: 2.0.6958 Release

$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
```


You got Mesa crap for display :1 and ATI accelerated for display :0.  Xgl is running on display :1 so that's why it working so-so for you.

> **Nikos.Alexandris said:**
> 
```
Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "1"
EndSection

```

Keep on the good work! :)

Try setting "Composite" "0" and reboot.  Hopefully it will get better -- after reboot, please post your fglrxinfo outputs.

I think your biggest problem is 8.42.3 driver.  I think it's just a  bad driver.  See my extensive comments on that driver in [thread=588383]8.42.3[/thread].  Just for everyone's reference, I do NOT recommend 8.42.3 driver.  This thread is written primarily for 8.37.6 driver which ships in Gutsy repositories.  The only exceptions are 2000HD ATI users who need newer than 8.37 drivers.

---

### Post by jw5801 on 2007-10-29
> **michael37 said:**
> Good news.  Your driver is working perfectly (if you ever played Warcraft, it'd be "It doesn't get any better than that").

It looks like either your Xgl or your Compiz are busted.  Follow the "upgrade" instructions (first page in this thread) and do steps 1-5 and then 14-18.  Skip all other steps (esp the ones related to work on drivers).

:( No dice. Still have the same error. ```
jw5801@laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "run_command_10"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "run_command_11"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "run_command_12"
```I didn't upgrade from feisty to gutsy using the update manager by the way. I kept my home directory but did a fresh reinstall. Compiz was running perfectly until I decided to try the newer driver following [this](http://forlong.blogage.de/article/add_comment/796) guide. I couldn't get it working at all, so I quit, undid everything and reinstalled Xgl and the fglrx from the repositories and now I'm getting this "GLX_EXT_texture_from_pixmap is missing" error. I think I might remove Xgl (and the libglitz-glx libraries) then see if there are any broken traces of them lying around to remove and see if that makes a difference. Thanks for the help so far! Any other suggestions pop into mind?

---

### Post by athaki on 2007-10-29
I tried the new ATI driver, and it completely broke everything, so I reverted back to the old one and am going to wait until Ubuntu releases it through the restricted drivers manager because I'm too lazy to tweak stuff for 5 hours. :D

---

### Post by jw5801 on 2007-10-29
Ok, having a look around, several other driver install how-to's seem to mention making a backup copy of /usr/lib/xorg/modules/* and restoring it after running a shell script. So would it be possible for the driver installer, when I ran it, to mess with some of the libraries in that folder, hence preventing compiz from running? Also, I deleted "/usr/lib/xorg/modules/extensions/libglx.so" thinking that it had been installed by libglitz-glx1 and left behind when it was uninstalled, which it apparently wasn't, so now if I reinstall xserver-xgl I don't make it to the gnome desktop :(.
So could someone with a working AMD64 Gutsy install please upload either just:
/usr/lib/xorg/modules/extensions/libglx.so
or zip the entire /usr/lib/xorg/modules folder and upload it here for me?


EDIT: Yup... definitely shouldn't have deleted that library... heh. Well I may have needed to delete it... but I definitely needed to know how to get it back again first!
```
jw5801@laptop:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!
```

EDIT2: Fixed it by getting it back off the LiveCD, so back to square one now.

---

### Post by xarroyo on 2007-10-29
Hi Michael37
Here i post my fglxinfo.. But i was wondering if you could help me to enable the VGA video output to connect Projectors, and also enable de S-Video which was working on ubuntu 7.04. But now when i have updated to gutsy these video outputs are not working.

Thanks for your attention,
Xavier Arroyo

```
xavi@dellota:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

xavi@dellota:~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6473 (8.37.6))

```

---

### Post by advilandy on 2007-10-30
> **michael37 said:**
> Try this:  

depmod -a
modinfo fglrx

What does that print?

```
$ sudo depmod -a
$ modinfo fglrx
filename:       /lib/modules/2.6.22-14-generic/misc/fglrx.ko
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
alias:          pci:v00001002d0000719Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d00005B65sv*sd*bc03sc00i00*
alias:          pci:v00001002d00003151sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000728Csv*sd*bc03sc00i00*
alias:          pci:v00001002d000071DAsv*sd*bc03sc00i00*
alias:          pci:v00001002d000071D2sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007153sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007152sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005E48sv*sd*bc03sc00i00*
alias:          pci:v00001002d00003E54sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005B64sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004154sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007104sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000710Esv*sd*bc03sc00i00*
alias:          pci:v00001002d0000710Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d00007105sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005D51sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005D50sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005554sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005555sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005551sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005550sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004A4Dsv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E4Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d00004147sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E47sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071D4sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007106sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007103sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071C4sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007144sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005D49sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000564Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000564Asv*sd*bc03sc00i00*
alias:          pci:v00001002d00003154sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005464sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E54sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007211sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007210sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007284sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071DEsv*sd*bc03sc00i00*
alias:          pci:v00001002d000071D6sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071D5sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000718Asv*sd*bc03sc00i00*
alias:          pci:v00001002d00007188sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007186sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000718Dsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000718Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d00007196sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000718Csv*sd*bc03sc00i00*
alias:          pci:v00001002d00007102sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007101sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071C5sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007145sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000714Csv*sd*bc03sc00i00*
alias:          pci:v00001002d0000714Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d00007149sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000714Asv*sd*bc03sc00i00*
alias:          pci:v00001002d00005D48sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005D4Asv*sd*bc03sc00i00*
alias:          pci:v00001002d00005652sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005653sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005462sv*sd*bc03sc00i00*
alias:          pci:v00001002d00003150sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005461sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005460sv*sd*bc03sc00i00*
alias:          pci:v00001002d00003152sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004A4Esv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E56sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E52sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E50sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000728Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d00007289sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007288sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007280sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007281sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007283sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007287sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007290sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007291sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007297sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007293sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007200sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071C7sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071C1sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071C3sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071C6sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071C2sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071CEsv*sd*bc03sc00i00*
alias:          pci:v00001002d000071C0sv*sd*bc03sc00i00*
alias:          pci:v00001002d000071CDsv*sd*bc03sc00i00*
alias:          pci:v00001002d000071DEsv*sd*bc03sc00i00*
alias:          pci:v00001002d00007187sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007180sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007183sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007181sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007193sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000719Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000718Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d00007140sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000714Dsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000714Esv*sd*bc03sc00i00*
alias:          pci:v00001002d00007146sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000715Esv*sd*bc03sc00i00*
alias:          pci:v00001002d00007142sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007147sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000714Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d00007151sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000715Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d00007143sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007141sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000564Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d00005E4Asv*sd*bc03sc00i00*
alias:          pci:v00001002d00005E4Dsv*sd*bc03sc00i00*
alias:          pci:v00001002d00005E4Csv*sd*bc03sc00i00*
alias:          pci:v00001002d00005E4Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d00005657sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005E4Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d00003E50sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005B60sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005B62sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005B66sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005B63sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004155sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004153sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E51sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004152sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004151sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004150sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007248sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007249sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000724Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000724Csv*sd*bc03sc00i00*
alias:          pci:v00001002d0000724Dsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000724Esv*sd*bc03sc00i00*
alias:          pci:v00001002d0000724Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d00007247sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007240sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007243sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007244sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007245sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007246sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000724Asv*sd*bc03sc00i00*
alias:          pci:v00001002d0000710Asv*sd*bc03sc00i00*
alias:          pci:v00001002d0000710Csv*sd*bc03sc00i00*
alias:          pci:v00001002d0000710Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d00007108sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007109sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007100sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004B4Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d00004B48sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004B49sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004B4Asv*sd*bc03sc00i00*
alias:          pci:v00001002d00004B4Csv*sd*bc03sc00i00*
alias:          pci:v00001002d00005D4Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d00005D4Csv*sd*bc03sc00i00*
alias:          pci:v00001002d00005D4Dsv*sd*bc03sc00i00*
alias:          pci:v00001002d00005D52sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000554Esv*sd*bc03sc00i00*
alias:          pci:v00001002d0000554Dsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000554Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000554Csv*sd*bc03sc00i00*
alias:          pci:v00001002d0000554Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000554Asv*sd*bc03sc00i00*
alias:          pci:v00001002d00005549sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005548sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005D57sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004A4Bsv*sd*bc03sc00i00*
alias:          pci:v00001002d00004A48sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004A4Asv*sd*bc03sc00i00*
alias:          pci:v00001002d00004A50sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004A4Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d00004A54sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004A4Csv*sd*bc03sc00i00*
alias:          pci:v00001002d00004A49sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E4Asv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E49sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004148sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004149sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E48sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E44sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004144sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E45sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004E46sv*sd*bc03sc00i00*
alias:          pci:v00001002d00004146sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000796Csv*sd*bc03sc00i00*
alias:          pci:v00001002d0000796Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000796Esv*sd*bc03sc00i00*
alias:          pci:v00001002d0000796Dsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000791Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d0000791Esv*sd*bc03sc00i00*
alias:          pci:v00001002d00007942sv*sd*bc03sc00i00*
alias:          pci:v00001002d00007941sv*sd*bc03sc00i00*
alias:          pci:v00001002d0000793Fsv*sd*bc03sc00i00*
alias:          pci:v00001002d00005975sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005974sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005874sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005854sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005955sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005954sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005A42sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005A43sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005A41sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005A63sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005A62sv*sd*bc03sc00i00*
alias:          pci:v00001002d00005A61sv*sd*bc03sc00i00*
depends:        agpgart
vermagic:       2.6.22-14-generic SMP mod_unload 586
parm:           firegl:charp
```

Dunno what any of that means.

---

### Post by dmanbuhnik on 2007-10-30
Hi,

i have the "mesa3d nightmare"...
what i did up till now & setup:
ATI X800XL
ubuntu 7.10 (clean install)
after first reboot i used "system -> admin -> restricted drivers" and V on the ATI.
reboot
then ```
sudo apt-get install xserver-xgl
```
reboot (to be on the safe side :) )
```
sudo apt-get install compizconfig-settings-manager
```
and then enable 3d desktop using the "system -> pref -> ...."

everything is almost great!
i got all the 3d effects and stuff BUT its kind of slow in some points - mostly in scrolling in firefox

the problem i think is the "mesa nightmare" -
```
:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```
```
:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```
```
:~$ glxinfo|grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: ATI RADEON X800 XL
```

how to solve it? (and keep my nice xorg.conf like i like it, i'm a bit scared doing "aticonfig --initial")

Thx in advance for the help

---

### Post by Nikos.Alexandris on 2007-10-30
> **michael37 said:**
> You got Mesa crap for display :1 and ATI accelerated for display :0.  Xgl is running on display :1 so that's why it working so-so for you.



Try setting "Composite" "0" and reboot.  Hopefully it will get better -- after reboot, please post your fglrxinfo outputs.

I think your biggest problem is 8.42.3 driver.  I think it's just a  bad driver.  See my extensive comments on that driver in [thread=588383]8.42.3[/thread].  Just for everyone's reference, I do NOT recommend 8.42.3 driver.  This thread is written primarily for 8.37.6 driver which ships in Gutsy repositories.  The only exceptions are 2000HD ATI users who need newer than 8.37 drivers.

[SIZE="2"]**Well, I don't want to add more heavy posts in this thread. It's already too much I think!**[/SIZE]

[B]I tried to setup X with 2 monitors and 3D effects working(for a Samsung R20 - ATI X1250 IGP)  with Gutsys restricted drivers without success.

I managed to get dual monitor support with the new driver 8.42.3 without 3D (and not the best performance ever). Yet I can enable 3D effects whenever I use only the laptops monitor working in its best.[/B]

Here is the link for my post... [[COLOR="Blue"][SIZE="2"]**http://ubuntuforums.org/showthread.php?p=3669524#post3669524**[/SIZE][/COLOR]]("http://ubuntuforums.org/showthread.php?p=3669524#post3669524")

[COLOR="Blue"][SIZE="2"]If anyone is an expert and has the time to have a look... I would like to know why I got this error message whenever I try to enable 3D when both monitors work with their correct resolution (?)[/SIZE][/COLOR]

**[SIZE="2"]*** glibc detected *** fglrxinfo: double free or corruption (!prev): 0x08062068 ***[/SIZE]**

Thanks and GD Luck to everybody!

---

### Post by mrhirsh on 2007-10-30
Michael 37 was hugely helpful in getting mostly functional after some screw ups by myself.  Thanks.

I have not been able to get Compiz back after my upgrade to Gutsy.  When I type Compiz in the terminal, I get:

michael@toshibalaptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

Any help in getting Compiz back is appreciated.  By the way, all the options when I select System>Preferences>Advanced Desktop Settings are checked.  I have the Radeon x1200 card, which does not seem to be supported yet.

Thanks,

---

### Post by michael37 on 2007-10-30
> **advilandy said:**
> 
Dunno what any of that means.

It means that you are not using the driver shipped with Gutsy.  That's probably why you are having problems :)

Where you found this driver that you have installed now and how to uninstall -- that a question that I can't answer.  But sure do uninstall it first.

---

### Post by michael37 on 2007-10-30
> **mrhirsh said:**
> Michael 37 was hugely helpful in getting mostly functional after some screw ups by myself.  Thanks.

I have not been able to get Compiz back after my upgrade to Gutsy.  When I type Compiz in the terminal, I get:

michael@toshibalaptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

Any help in getting Compiz back is appreciated.  By the way, all the options when I select System>Preferences>Advanced Desktop Settings are checked.  I have the Radeon x1200 card, which does not seem to be supported yet.

Thanks,

Mrhirsh, your card is absolutely supported.  Please note the error "Checking for Xgl: not present. ".  If you had followed my guide, you would have Xgl installed.  Please go to the first page of this thread and follow the howto.

---

### Post by michael37 on 2007-10-30
> **dmanbuhnik said:**
> Hi,

i have the "mesa3d nightmare"...
what i did up till now & setup:
ATI X800XL
ubuntu 7.10 (clean install)
after first reboot i used "system -> admin -> restricted drivers" and V on the ATI.
reboot
then ```
sudo apt-get install xserver-xgl
```
reboot (to be on the safe side :) )
```
sudo apt-get install compizconfig-settings-manager
```
and then enable 3d desktop using the "system -> pref -> ...."

everything is almost great!
i got all the 3d effects and stuff BUT its kind of slow in some points - mostly in scrolling in firefox

the problem i think is the "mesa nightmare" -
```
:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```
```
:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```
```
:~$ glxinfo|grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: ATI RADEON X800 XL
```

how to solve it? (and keep my nice xorg.conf like i like it, i'm a bit scared doing "aticonfig --initial")

Thx in advance for the help

I am sorry to say, but your nice xorg.conf is broken.  I recommend wiping it out and rebuilding it from scratch.  You have MESA on display :0 and ATI accelerated driver on display :1.  That means your fglrx driver is being loaded correctly, but without 3D on one of the displays.

A few broken things come to mind: Xinerama enabled?  DRI section not correct?

---

### Post by michael37 on 2007-10-30
> **xarroyo said:**
> Hi Michael37
Here i post my fglxinfo.. But i was wondering if you could help me to enable the VGA video output to connect Projectors, and also enable de S-Video which was working on ubuntu 7.04. But now when i have updated to gutsy these video outputs are not working.

Thanks for your attention,
Xavier Arroyo


I am sorry, but this is outside of scope of this thread.  Try looking in other threads dedicated to bigdesktop (ATI feature that allows spanning monitors), like [thread=3664618]here[/thread]

---

### Post by michael37 on 2007-10-30
> **jw5801 said:**
> :( No dice. Still have the same error. 
(skip)
 I couldn't get it working at all, so I quit, undid everything and reinstalled Xgl and the fglrx from the repositories and now I'm getting this "GLX_EXT_texture_from_pixmap is missing" error. I think I might remove Xgl (and the libglitz-glx libraries) then see if there are any broken traces of them lying around to remove and see if that makes a difference. Thanks for the help so far! Any other suggestions pop into mind?

Umm, didn't I suggest to uninstall Xgl and compiz and reinstall them in [my previous reply](http://ubuntuforums.org/showpost.php?p=3663892&postcount=146)?  In any case, use --purge when removing packages.  remove is not enough.

---

### Post by advilandy on 2007-10-30
> **michael37 said:**
> It means that you are not using the driver shipped with Gutsy.  That's probably why you are having problems :)

Where you found this driver that you have installed now and how to uninstall -- that a question that I can't answer.  But sure do uninstall it first.

The restricted driver does not work on my machine for some reason...it will not keep resolutions and the xserver crashes over and over. I think I will probably wait until I get an nvidia card because I can't afford to mess up this computer (it's the only one I have right now) so close to my exams.

Thanks for you help, and I may be back after exams.

---

### Post by dmanbuhnik on 2007-10-31
my xorg.conf:
```
Section "Files"
EndSection

Section "InputDevice"
	Identifier		"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,il"
	Option		"XkbVariant"	",lyx"
	Option		"XkbOptions"	"grp:alt_shift_toggle,grp_led:scroll"
EndSection

#Section "InputDevice"
#	Identifier		"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mice"
#	Option		"Protocol"	"ImPS/2"
#	Option		"ZAxisMapping"	"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection
Section "InputDevice"
	Identifier		"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ExplorerPS/2"
	Option		"ZAxisMapping" "4 5"
	Option		"Buttons" "10"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier		"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier		"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier		"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver		"fglrx"
	Busid		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier		"Default Layout"
	screen		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

# To prevent Blank Screen from popping up every 10 minutes
# when xgl is run as a session on display :1,
# when all the power management settings
# you normally find only concerns display :0
#Section "ServerFlags"
#	Option 	"blank time" "10"
#	Option 	"standby time" "20"
#	Option 	"suspend time" "20"
#	Option	"off time" "30"
#EndSection
```

when i do ```
aticonfig --initial
``` will it destory my screen resolution?

---

### Post by sil3nt on 2007-10-31
Hi Michael37, I have a similar issue to dmanbuhnik with the same graphics card here are my details :-

fglrxinfo:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 2.0.6958 Release
```

glxinfo:

```
OpenGL renderer string: Mesa GLX Indirect
```

and last but not least the xorg.conf:

```
Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
	Option		"Composite"	"0"
EndSection
```

Is this also a prob with my xorg-conf?

Sil3nt

---

### Post by combatwombat_nz on 2007-10-31
I too had this problem after applying the 8.42.3 ati driver in gutsy: Mesa took over the rendering. What it came down to, from looking at /var/log/Xorg.0.log, was that the fglrx module was not loading, even tho' it was quite happy installing itself from the binary, and from Envy (which uses the same binary). After googling a bit I did this to fix:
first of all Become su, and do the following preferaibly outside of an X session, and having no X-sessions running. This is after the driver is installed!!!

1.) lsmod (look for any thing that says ati if exists type rmmod ati)
2.) cd /lib/modules/fglrx/build_mod/
3.) sh make.sh
4.) (not necessary but good to do anyway just in case) modprobe agpgart
5.) cd /lib/modules/fglrx/
6.) sh make_install.sh (Ignore any warnings about kernel taint)
7.) modprobe fglrx && lsmod | grep fglrx
8.) reboot, so that X can restart with it's default modules loaded.

Now I get:
fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X600
OpenGL version string: 2.0.6958 Release
:guitar:

So, I'm off to see what Compiz looks like under the new driver, and if it still has the window resizing bug...which is the whole reason I did this in the first place.

---

### Post by combatwombat_nz on 2007-10-31
It works, and they have fixed the bug, which was probably caused by XGL anyhow.

So, I now have running: Gnome, AIGLX, ATi X600 Mobility, Compiz Fusion. No XGL required. Full ATi 8.42.3 driver.

Thanks to Phoronix forums and this forum here!

Steps: follow the instructions on first page.
 But don't reinstal xserver-xgl
I needed to alter /usr/bin/compiz to whitelist the fglrx, and comment out the line blacklisting my graphics card (X600).

Then I make sure composite and AIGLX is enabled in the xorg.conf. My file:

==========
Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
Option		"DRI"			"true"
Option		"ColorTiling"		"on"
Option		"EnablePageFlip"	"true"
Option		"AccelMethod" 		"EXA"
Option		"XAANoOffscreenPixmaps"
Option		"RenderAccel"		"true"
Option 		"AGPMode" 		"4"
Option		"AGPFastWrite"		"on"
Option "KernelModuleParm" "agplock=0"
Option "UseInternalAGPGART" "no"
Option "EnablePrivateBackZ" "no"
Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
Option "mtrr" "on"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
Option		"DRI"			"true"
Option		"ColorTiling"		"on"
Option		"EnablePageFlip"	"true"
Option		"AccelMethod" 		"EXA"
Option		"XAANoOffscreenPixmaps"
Option		"RenderAccel"		"true"
Option 		"AGPMode" 		"4"
Option		"AGPFastWrite"		"on"
Option "KernelModuleParm" "agplock=0"
Option "UseInternalAGPGART" "no"
Option "EnablePrivateBackZ" "no"
Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
Option "mtrr" "on"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1440x900"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
Section "DRI"
Mode 0666
EndSection

Section "Module"
	Load		"glx"
EndSection
Section "ServerFlags"
	Option "AIGLX" "on"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
================
:lolflag:

---

### Post by jw5801 on 2007-10-31
> **michael37 said:**
> Umm, didn't I suggest to uninstall Xgl and compiz and reinstall them in [my previous reply](http://ubuntuforums.org/showpost.php?p=3663892&postcount=146)?  In any case, use --purge when removing packages.  remove is not enough.

Sorry, I did remove Xgl and compiz (with --purge) and all the associated configuration files, as per your how-to, all to no avail. Following this being unsuccessful, I decided I would check manually for anything that may have been left behind by the newer ATi script. This turned out to be a bad idea and didn't help at all, but I repaired extra damage I may have caused and I'm now back to the original point with compiz reporting that "GLX_EXT_texture_from_pixmap is missing." My "No dice, still have the same error" was meant to convey that I had done as you suggested and had no change. I also gave some background information on how I came to this point which was a little jumbled together with what had happened since your last post, so I apologize for that.

Anyway, long story short, uninstalling and purging Xgl, compiz and fglrx, then reinstalling all three returned me to the same point with compiz not wanting to initiate.

---

### Post by Nikos.Alexandris on 2007-10-31
> **dmanbuhnik said:**
> my xorg.conf:
```
Section "Files"
EndSection

Section "InputDevice"
	Identifier		"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,il"
	Option		"XkbVariant"	",lyx"
	Option		"XkbOptions"	"grp:alt_shift_toggle,grp_led:scroll"
EndSection

#Section "InputDevice"
#	Identifier		"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mice"
#	Option		"Protocol"	"ImPS/2"
#	Option		"ZAxisMapping"	"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection
Section "InputDevice"
	Identifier		"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ExplorerPS/2"
	Option		"ZAxisMapping" "4 5"
	Option		"Buttons" "10"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier		"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier		"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier		"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver		"fglrx"
	Busid		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier		"Default Layout"
	screen		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

# To prevent Blank Screen from popping up every 10 minutes
# when xgl is run as a session on display :1,
# when all the power management settings
# you normally find only concerns display :0
#Section "ServerFlags"
#	Option 	"blank time" "10"
#	Option 	"standby time" "20"
#	Option 	"suspend time" "20"
#	Option	"off time" "30"
#EndSection
```

when i do ```
aticonfig --initial
``` will it destory my screen resolution?

Do you run Compiz without problems? You don't have the ```
Load   "dri"
``` module under **Section "Module"**.

Concerning ```
"aticonfig --initial"
``` (or ```
sudo aticonfig --initial --force
``` if the first does not work -- (together with ```
sudo dpkg-reconfigure xserver-xorg
``` if necessary)

...as far as I can tell, it's not the one command  which is going to brake your X. The opposite, it's the one who will bring you back if you can't start up GDM.

---

### Post by sil3nt on 2007-10-31
COMBATWOMBAT U ROCK!!!!!!!

I fixed my problem using some of the info you posted!!!!

look when I run glxinfo | grep direct I now get :

```
direct rendering: Yes
```

Heres what I did, Removed xserver-xgl as per first article stripped off compiz and did a autoremove cleanup

I checked out my /var/log/Xorg.0.log but everything looked ok and it was starting fglrx ok.

The real key for me was the edit of xorg.conf i copied a few of your settings mainly :

```
Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
Option "AccelMethod" "EXA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "on"
Option "KernelModuleParm" "agplock=0"
Option "UseInternalAGPGART" "no"
Option "EnablePrivateBackZ" "no"
Option "DisableGLXRootClipping" "true"
Option "AddARGBGLXVisuals" "true"
Option "AllowGLXWithComposite" "true"
Option "EnablePageFlip" "true"
Option "mtrr" "on"
EndSection
```

and ```
Section "Module"
Load "glx"
EndSection
Section "ServerFlags"
Option "AIGLX" "on"
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection
```

Thanks so much 

Sil3nt

---

### Post by Nikos.Alexandris on 2007-10-31
> combatwombat_nz;3675643]It works, and they have fixed the bug, which was probably caused by XGL anyhow.

So, I now have running: Gnome, AIGLX, ATi X600 Mobility, Compiz Fusion. No XGL required. Full ATi 8.42.3 driver.

Thanks to Phoronix forums and this forum here!

Steps: follow the instructions on first page.
 But don't reinstal xserver-xgl
I needed to alter /usr/bin/compiz to whitelist the fglrx, and comment out the line blacklisting my graphics card (X600).

Then I make sure composite and AIGLX is enabled in the xorg.conf. My file:

...

```
[B]Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
Option "AccelMethod" "EXA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "on"
Option "KernelModuleParm" "agplock=0"
Option "UseInternalAGPGART" "no"
Option "EnablePrivateBackZ" "no"
Option "DisableGLXRootClipping" "true"
Option "AddARGBGLXVisuals" "true"
Option "AllowGLXWithComposite" "true"
Option "EnablePageFlip" "true"
Option "mtrr" "on"[/B]
```

Hi!

I am trying to trace some documentation about some of the options you mention in your xorg.conf (ColorTiling, AllowGLXWithComposite and more).

Where can I read more about this? There is nothing to read about them in the xorg.conf man, and in the aticonfig help file as well.

Thanks in advance.

---

### Post by Nikos.Alexandris on 2007-10-31
Well,

I found that [https://help.ubuntu.com/community/RadeonDriver#head-4353128024338b05ba40d5e5c837ff7b65f55b78](https://help.ubuntu.com/community/RadeonDriver#head-4353128024338b05ba40d5e5c837ff7b65f55b78)

about the open source driver (the one that is shipped with Gutsy).

Do all of these options apply also to the ATI 8.42.3 driver?

---

### Post by kane357 on 2007-10-31
Is this the settings for the newest ati driver?

---

### Post by Nikos.Alexandris on 2007-10-31
> **kane357 said:**
> Is this the settings for the newest ati driver?

If you mean about the link I copy-pasted... (?) This is my question too?

---

### Post by kane357 on 2007-10-31
Yes because I am very foreign to all of linux. I have used Windows since my inception to PC's. I am lost with all the drivers and xgl stuff so I dont want to ruin my vid card doing all types of options.

My problem is I have no direct rendering, I removed xserver xgl and i still have no rendering. I keep freezing up when i run to many things with graphics.

---

### Post by kane357 on 2007-10-31
THis is in regards to the first post about what the manula how to says

"Some users report using Envy or alternative mechanisms to install newer drivers. This is very dangerous. As this press-release indicates, many with older GPUs had immediately upgraded with some then having a foul experience. In this guide, "older" means anything but 2000HD series!!! That's what most of us run. So, if you have have a video card from the supported hardware section (see my previous post), then you must not upgrade to the newer driver."
 
I have a x800 Mobility and I upgraded to newest drivers, why should i go back and how do i go back, please elaborate. Im at a over informed stage and I am pretty lost atm. I did not upgrade from fiesty, I did a fresh install and my card is a x800 mobility pci-express card.

Help zores, sorry about the multiple posts.

---

### Post by Nikos.Alexandris on 2007-10-31
> **kane357 said:**
> Yes because I am very foreign to all of linux. I have used Windows since my inception to PC's. I am lost with all the drivers and xgl stuff so I dont want to ruin my vid card doing all types of options.

My problem is I have no direct rendering, I removed xserver xgl and i still have no rendering. I keep freezing up when i run to many things with graphics.


I think that if you follow **STEP-BY-STEP** the post of combatwombat_nz ([COLOR="Blue"][http://ubuntuforums.org/showpost.php?p=3675643&postcount=167](http://ubuntuforums.org/showpost.php?p=3675643&postcount=167)[/COLOR]) or even better the Unofficial ATI wiki [[COLOR="Blue"]http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")
then you have nothing to loose.

If you still want to stay 100% sure that you will not brake your X then... you don't do anything and you wait for the **BIG NEWS**.

But then again, testing various things... is what will give you experience. Just be very careful when you use the sudo command (or when you are logged in as root). And... watch out in case you uninstall completely all of the video drivers (as it is described in some how-to's) [COLOR="Red"]**DON'T REBOOT** before you install some  driver to support your graphic card[/COLOR]! The rest... you can play with your system.

P.S. This is how I managed to get Full 3D support in my ATI 1250 > [http://ubuntuforums.org/showpost.php?p=3669524&postcount=10]("http://ubuntuforums.org/showpost.php?p=3669524&postcount=10")

---

### Post by Nikos.Alexandris on 2007-10-31
Has anybody an idea about... **[COLOR="Red"]*** glibc detected *** fglrxinfo: double free or corruption (!prev): 0x08062068 ***[/COLOR]** **[COLOR="Red"]???[/COLOR]**

---

### Post by pwozney on 2007-10-31
Here is fglrxinfo and glxinfo:
[INDENT]paul@paul-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6958 Release

paul@paul-laptop:~$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect[/INDENT]

And this is the same data, but from each display:
[INDENT]paul@paul-laptop:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6958 Release

paul@paul-laptop:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

paul@paul-laptop:~$ glxinfo -display :0 | grep render
direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon X1300

paul@paul-laptop:~$ glxinfo -display :1 | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect[/INDENT]

I had ati-config make a new xorg.conf with "aticonfig --initial --force"  Here is the xorg.conf:
[INDENT]paul@paul-laptop:~$ cat /etc/X11/xorg.conf

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
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        InputDevice    "Synaptics Touchpad"
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
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "EnableMonitor" "crt1"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection[/INDENT]

I followed this thread very closely, a few times.  Each time I took the second path and did a complete purge and started over.  I have compiz running, but it is clear that the load is being handled by my CPU, and not the GPU.  This is not so good as I need my CPU for other stuff.

Maybe Xgl is using the second display?  It would seem to me that it would be better to have the ATI driver on both displays, but if this isn't possible then Xorg should use the display with the slow driver, and Xgl should use the ATI display.

Any recommendations?

Paul

---

### Post by niallcd on 2007-10-31
I'd just like to say nice work on solving some of these difficulties first off.

My question is about Xgl and how cpu intensive it can be. I run 7.10 with Compiz Fusion and its great but my Radeon 9800pro needs the Xgl driver to make CF work. 

I use the drivers that came with Ubuntu and added sudo apt-get install xserver-xgl to get Xgl.

Now everything works now its just a matter of ironing out some kinks and fine tuning. Something I noticed the other day while writing an email was a delay when writing text and the cpu useage with Xgl was hovering around 30% and if I moved the cube its climbed to 90%.

So I guess the point is, is there a way to make Xgl less intensive and have it not bog down?
Or could I have missed adding something that works in conjunction with Xgl to help it along?

I read about CVS a little but I'm not fully confident in my knowledge surrounding it.

Source for CVS input I got from here: [http://ubuntuforums.org/showthread.php?t=148860&page=36](http://ubuntuforums.org/showthread.php?t=148860&page=36)

Any help would be great. 

Ps posted below is my Xorg-conf if needed. Thanks again.

> Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SDM-HS95P"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"SDM-HS95P"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1280x960"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection  

---

### Post by dmanbuhnik on 2007-10-31
hello again (sorry about the long replay, work u know...)
anyway, i made backup my xorg.conf (move him to another name) and run
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
then
```
sudo aticonfig --initial --force
```
restart
and.... no change
fglrx on :0 i have mesa3d, and on :1 i have ATI
my new xorg.conf:
```
Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
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
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver      "ati"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

compiz run smooth, my only problem is the slow scrolling in FF (depends on the page)
i NOT running 8.42.3 driver version
my ATI driver is 8.37.6 (automatic install from ubuntu 7.10)
and what about DRI? i need to enable it even if i'm not using the new driver? is so, how
or i just need to move up to the new driver?

how can i fix this?
Thx,

---

### Post by burgerboy06 on 2007-11-01
Thanks for the help everyone!  Got it working following the guide on that first page.  ASUS W3J X1600 Mobility ATI core duo.  I got it working on Feisty and Edgy, now on Gusty, thank a lord.  I thought I was going to have to abandon ubuntu.  

I use Windows for AutoCad programs and thats it now!  Thanks.

---

### Post by Nikos.Alexandris on 2007-11-01
> **pwozney said:**
> Here is fglrxinfo and glxinfo:
[INDENT]paul@paul-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6958 Release

paul@paul-laptop:~$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect[/INDENT]

And this is the same data, but from each display:
[INDENT]paul@paul-laptop:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6958 Release

paul@paul-laptop:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

paul@paul-laptop:~$ glxinfo -display :0 | grep render
direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon X1300

paul@paul-laptop:~$ glxinfo -display :1 | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect[/INDENT]

I had ati-config make a new xorg.conf with "aticonfig --initial --force"  Here is the xorg.conf:
[INDENT]paul@paul-laptop:~$ cat /etc/X11/xorg.conf

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
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        InputDevice    "Synaptics Touchpad"
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
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "EnableMonitor" "crt1"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection[/INDENT]

I followed this thread very closely, a few times.  Each time I took the second path and did a complete purge and started over.  I have compiz running, but it is clear that the load is being handled by my CPU, and not the GPU.  This is not so good as I need my CPU for other stuff.

Maybe Xgl is using the second display?  It would seem to me that it would be better to have the ATI driver on both displays, but if this isn't possible then Xorg should use the display with the slow driver, and Xgl should use the ATI display.

Any recommendations?

Paul

I had the same problem... I just removed XGL and the I had direct rendering in both monitors. It's just that the performance of AIGLX is not the best you can get when watching video at full screen or using googleearth for example (at least this is my eperience).

---

### Post by Hoenheim on 2007-11-01
Well, yeah I'm having a problem with my ati driver, it says not in use in restricted drivers manager and 
this is what I get from fglrxinfo -display :0
```
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

```
someone got the answer, all help is welcome, thx.

---

### Post by kane357 on 2007-11-01
I removed ubuntu and I installed Vista. I was up and running in 30 minutes. I see no reason to go back to ubuntu yet. I hope they get some good drivers eventually and I will be a full fledge member of the ubuntu movement:]

---

### Post by dmanbuhnik on 2007-11-01
ok!
after ~1.5 hour of playing with things (install, uninstall, install using deferent guide, uninstall, install......i even tried AIGLX which sucks right now (so slow...))
my new output:
fglrxinfo -display :0
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 2.0.6473 (8.37.6)

```
fglrxinfo -display :1
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 1.2 (2.0.6473 (8.37.6))

```
glxinfo -display :0
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
...
client glx vendor string: ATI
client glx version string: 1.3
...
GLX version: 1.2
...
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 2.0.6473 (8.37.6)
...
```
glxinfo -display :1
```
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
...
client glx vendor string: ATI
client glx version string: 1.3
...
GLX version: 1.2
...
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```
glxgear have nice result (but uses 100% of CPU!)
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
38002 frames in 5.0 seconds = 7600.373 FPS
43291 frames in 5.0 seconds = 8650.282 FPS
72277 frames in 5.0 seconds = 14429.582 FPS
73715 frames in 5.0 seconds = 14738.031 FPS

```
add my xorg.conf as a file

what's the deal with the "Xlib:  extension "XFree86-DRI" missing on display ":1.0""? and how can i fix that?
and why glxgear uses 100% of the CPU? (i think that's the problem with the scrolling in FF)

again, thx for the help

---

### Post by kyleau on 2007-11-02
I have follow the how-to guide and install everything without problems, but I still get the error
    "desktop effect can not be enabled" :(
(my fglrxinfo 0 and 1 are showing correctly with my ati x1600)
any idea? thank you!

---

### Post by michael37 on 2007-11-03
> **kyleau said:**
> I have follow the how-to guide and install everything without problems, but I still get the error
    "desktop effect can not be enabled" :(
(my fglrxinfo 0 and 1 are showing correctly with my ati x1600)
any idea? thank you!

Please run

compiz --replace --disable-sm

and post the output here.

---

### Post by michael37 on 2007-11-03
> **dmanbuhnik said:**
> ok!
after ~1.5 hour of playing with things (install, uninstall, install using deferent guide, uninstall, install......i even tried AIGLX which sucks right now (so slow...))
my new output:

what's the deal with the "Xlib:  extension "XFree86-DRI" missing on display ":1.0""? and how can i fix that?
and why glxgear uses 100% of the CPU? (i think that's the problem with the scrolling in FF)

again, thx for the help

Message  "Xlib:  extension "XFree86-DRI" missing on display ":1.0" is normal.  DRI is direct rendering, and our fglrx driver provides alternative DRI method which is used by Xgl on display :1.  If you care for details, type
grep ATIFGLRXDRI /var/log/Xorg.0.log

I think your system is configured perfectly.  I recommend playing with Firefox settings to ensure smooth scrolling -- I doubt it's a graphics driver, Xgl or Compiz.

---

### Post by michael37 on 2007-11-03
> **kane357 said:**
> I removed ubuntu and I installed Vista. I was up and running in 30 minutes. I see no reason to go back to ubuntu yet. I hope they get some good drivers eventually and I will be a full fledge member of the ubuntu movement:]

I am glad you have money to purchase Vista.  I am sure that if every Vista user considering Ubuntu contributed half as much money as Vista cost to the Ubuntu development, Ubuntu would have been miles ahead.

---

### Post by michael37 on 2007-11-03
> **Hoenheim said:**
> Well, yeah I'm having a problem with my ati driver, it says not in use in restricted drivers manager and 
this is what I get from fglrxinfo -display :0
```
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

```
someone got the answer, all help is welcome, thx.

What video card do you have?
lspci | grep ATI

---

### Post by michael37 on 2007-11-03
> **pwozney said:**
> Here is fglrxinfo and glxinfo:
[INDENT]paul@paul-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6958 Release

paul@paul-laptop:~$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect[/INDENT]

And this is the same data, but from each display:
[INDENT]paul@paul-laptop:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6958 Release

paul@paul-laptop:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

<...>

I followed this thread very closely, a few times.  Each time I took the second path and did a complete purge and started over.  I have compiz running, but it is clear that the load is being handled by my CPU, and not the GPU.  This is not so good as I need my CPU for other stuff.

Maybe Xgl is using the second display?  It would seem to me that it would be better to have the ATI driver on both displays, but if this isn't possible then Xorg should use the display with the slow driver, and Xgl should use the ATI display.

Any recommendations?

Paul

Different OpenGL methods on display :0 and :1 are typically a result of a broken fglrx driver installation.  What driver are you using?  8.42?  If yes, then disable AIGLX and Composite in xorg.conf and hopefully that will fix the problem.

Section "Extensions"
Option "AIGLX" "off"
Option "Composite" "off"
EndSection

---

### Post by elightbo on 2007-11-03
I am having problems as well, 3d rendering works, but i am getting this error message when trying to enable compiz.  There was a post from combatwombat about whitelisting fglrx, but how exactly is that done?  

Checking for Xgl: not present. 
```
Detected PCI ID for VGA: 06:00.0 0300: 1002:7280 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6473 (8.37.6)
```

Compiz config file:
```
#!/bin/sh
# Compiz Manager wrapper script
# 
# Copyright (c) 2007 Kristian Lyngstøl <kristian@bohemians.org>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
#
#
# Contributions by: Treviño (3v1n0) <trevi55@gmail.com>, Ubuntu Packages
#
# Much of this code is based on Beryl code, also licensed under the GPL.
# This script will detect what options we need to pass to compiz to get it
# started, and start a default plugin and possibly window decorator.
# 


COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real) 

# For Xgl LD_PRELOAD
LIBGL_NVIDIA="/usr/lib/nvidia/libGL.so.1.2.xlibmesa"
LIBGL_FGLRX="/usr/lib/fglrx/libGL.so.1.2.xlibmesa"

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default

# For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

FALLBACKWM="${METACITY}"
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
#WHITELIST="nvidia intel ati radeon i810"
WHITELIST="fglrx"

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"
unset T

COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
COMPIZ_PLUGINS=""
ENV=""

# Use emerald by default if it exist
USE_EMERALD="yes"

# No indirect by default
INDIRECT="no"

# Set to yes to enable verbose
VERBOSE="yes"

# Echos the arguments if verbose
verbose()
{
        if [ "x$VERBOSE" = "xyes" ]; then
                printf "$*"
        fi
}

# abort script and run fallback windowmanager
abort_with_fallback_wm()
{
        if [ "x$SKIP_CHECKS" = "xyes" ]; then
                verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"
                return 0;
        fi

        verbose "aborting and using fallback: $FALLBACKWM \n"

        if [ -x $FALLBACKWM ]; then
                exec $FALLBACKWM $FALLBACKWM_OPTIONS
        else
                printf "no $FALLBACKWM found, exiting\n"
                exit 1
        fi
}

# Check for non power of two texture support
check_npot_texture()
{
        verbose "Checking for non power of two support: "
        if glxinfo 2> /dev/null | egrep -q '(GL_ARB_texture_non_power_of_two|GL_NV_texture_rectangle|GL_EXT_texture_rectangle|GL_ARB_texture_rectangle)' ; then
                verbose "present. \n";
                return 0;
        else
                verbose "Not present. \n"
                return 1;
        fi

}

# Check for presence of FBConfig
check_fbconfig()
{
        verbose "Checking for FBConfig: "
        if [ "$INDIRECT" = "yes" ]; then
                $GLXINFO -i | grep -q GLX.*fbconfig 
                FB=$?
        else
                $GLXINFO | grep -q GLX.*fbconfig 
                FB=$?
        fi

        if [ $FB = "0" ]; then
                unset FB
                verbose "present. \n"
                return 0;
        else
                unset FB
                verbose "not present. \n"
                return 1;
        fi
}


# Check for TFP
check_tfp()
{
        verbose "Checking for texture_from_pixmap: "
        if [ $($GLXINFO 2>/dev/null | grep GLX_EXT_texture_from_pixmap -c) -gt 2 ] ; then
                verbose "present. \n"
                return 0;
        else
                verbose "not present. \n"
                if [ "$INDIRECT" = "yes" ]; then
                        unset LIBGL_ALWAYS_INDIRECT
                        INDIRECT="no"
                        return 1;
                else
                        verbose "Trying again with indirect rendering:\n";
                        INDIRECT="yes"
                        export LIBGL_ALWAYS_INDIRECT=1
                        check_tfp;
                        return $?
                fi
        fi
}

# Check wether the composite extension is present
check_composite()
{
        verbose "Checking for Composite extension: "
        if xdpyinfo -queryExtensions | grep -q Composite ; then
                verbose "present. \n";
                return 0;
        else
                verbose "not present. \n";
                return 1;
        fi
}

# Detects if Xgl is running
check_xgl()
{
        verbose "Checking for Xgl: "
        if xvinfo | grep -q Xgl ; then
                verbose "present. \n"
                return 0;
        else
                verbose "not present. \n"
                return 1;
        fi
}

# Check if the nVidia card has enough video ram to make sense
check_nvidia_memory()
{
        MEM=$(${NVIDIA_SETTINGS} -q VideoRam | egrep Attribute\ \'VideoRam\'\ .*: | cut -d: -f3 | sed 's/[^0-9]//g')
        if [ $MEM -lt $NVIDIA_MEMORY ]; then
                verbose "Less than ${NVIDIA_MEMORY}kb of memory and nVidia";
                return 1;
        fi
        return 0;
}

# Check for existence if NV-GLX
check_nvidia()
{
        if [ ! -z $NVIDIA_INTERNAL_TEST ]; then
                return $NVIDIA_INTERNAL_TEST;
        fi
        verbose "Checking for nVidia: "
        if xdpyinfo | grep -q NV-GLX ; then
                verbose "present. \n"
                NVIDIA_INTERNAL_TEST=0
                return 0;
        else
                verbose "not present. \n"
                NVIDIA_INTERNAL_TEST=1
                return 1;
        fi
}

# Check if the max texture size is large enough compared to the resolution
check_texture_size()
{
        TEXTURE_LIMIT=$(glxinfo -l | grep GL_MAX_TEXTURE_SIZE | sed 's/.*=[^0-9]//g')
        RESOLUTION=$(xdpyinfo  | grep -i dimensions: | sed 's/[^0-9]*pixels.*(.*).*//' | sed 's/[^0-9x]*//')
        VRES=$(echo $RESOLUTION | sed 's/.*x//')
        HRES=$(echo $RESOLUTION | sed 's/x.*//')
        verbose "Comparing resolution ($RESOLUTION) to maximum 3D texture size ($TEXTURE_LIMIT): ";
        if [ $VRES -gt $TEXTURE_LIMIT ] || [ $HRES -gt $TEXTURE_LIMIT ]; then
                verbose "Failed.\n"
                return 1;
        fi
        verbose "Passed.\n"
        return 0
}

# check driver whitelist
running_under_whitelisted_driver()
{
        LOG=$(xset q|grep "Log file"|awk '{print $3}')
        if [ -z "$LOG" ];then
                verbose "AIEEEEH, no Log file found \n"
                verbose "$(xset q) \n"
        return 0
        fi
        for DRV in ${WHITELIST}; do
                if egrep -q "Loading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG &&
                   ! egrep -q "Unloading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG; 
                then
                        return 0
                fi
        done
        verbose "No whitelisted driver found\n"
        return 1
}

# check pciid blacklist
have_blacklisted_pciid()
{
        OUTPUT=$(lspci -n)
        for ID in ${BLACKLIST_PCIIDS}; do
                if echo "$OUTPUT" | egrep -q "$ID"; then
                        verbose "Blacklisted PCIID '$ID' found \n"
                        return 0
                fi
        done
        OUTPUT=$(lspci -vn | grep -i VGA)
        verbose "Detected PCI ID for VGA: $OUTPUT\n"
        return 1
}

build_env()
{
        if check_nvidia; then
                ENV="__GL_YIELD=NOTHING "
        fi
        if [ "$INDIRECT" = "yes" ]; then
                ENV="$ENV LIBGL_ALWAYS_INDIRECT=1 "
        fi
        if check_xgl; then
                if [ -f ${LIBGL_NVIDIA} ]; then
                        ENV="$ENV LD_PRELOAD=${LIBGL_NVIDIA}"
                        verbose "Enabling Xgl with nVidia drivers...\n"
                fi
                if [ -f ${LIBGL_FGLRX} ]; then
                        ENV="$ENV LD_PRELOAD=${LIBGL_FGLRX}"
                        verbose "Enabling Xgl with fglrx ATi drivers...\n"
                fi
        fi

        ENV="$ENV FROM_WRAPPER=yes"

        if [ -n "$ENV" ]; then
                export $ENV
        fi
}

build_args()
{
        if [ $INDIRECT = "yes" ]; then
                COMPIZ_OPTIONS="$COMPIZ_OPTIONS --indirect-rendering "
        fi
        if check_nvidia; then
                COMPIZ_OPTIONS="$COMPIZ_OPTIONS --loose-binding"
        fi
}

####################
# Execution begins here.

# Read configuration from XDG paths
if [ -z "$XDG_CONFIG_DIRS" ]; then
        test -f /etc/xdg/compiz/compiz-manager && . /etc/xdg/compiz/compiz-manager
else
        test -f $XDG_CONFIG_DIRS/compiz/compiz-manager && . $XDG_CONFIG_DIRS/compiz/compiz-manager
fi

if [ -z "$XDG_CONFIG_HOME" ]; then
        test -f $HOME/.config/compiz/compiz-manager && . $HOME/.config/compiz/compiz-manager
else
        test -f $XDG_CONFIG_HOME/compiz/compiz-manager && .  $XDG_CONFIG_HOME/compiz/compiz-manager
fi

# Don't use compiz when running the failsafe session
if [ "x$GNOME_DESKTOP_SESSION_ID" = "xFailsafe" ]; then
        abort_with_fallback_wm
fi

if [ "x$LIBGL_ALWAYS_INDIRECT" = "x1" ]; then
        INDIRECT="yes";
fi

# if we run under Xgl, we can skip some tests here
if ! check_xgl; then
        # if vesa or vga are in use, do not even try glxinfo (LP#119341)
        if ! running_under_whitelisted_driver || have_blacklisted_pciid; then
                abort_with_fallback_wm
        fi
        # check if we have the required bits to run compiz and if not, 
        # fallback
        if ! check_tfp || ! check_npot_texture || ! check_composite || ! check_texture_size; then
                abort_with_fallback_wm
        fi

        if check_nvidia && ! check_nvidia_memory; then
                abort_with_fallback_wm
        fi

        if ! check_fbconfig; then
                abort_with_fallback_wm
        fi
fi

# load the ccp plugin if present and fallback to plain gconf if not
if [ -f ${PLUGIN_PATH}libccp.so ]; then
        COMPIZ_PLUGINS="$COMPIZ_PLUGINS ccp"
elif [ -f ${PLUGIN_PATH}libgconf.so ]; then
        COMPIZ_PLUGINS="$COMPIZ_PLUGINS glib gconf"
fi

# get environment
build_env
build_args

# start the gtk-window-decorator if present
if [ -x ${COMPIZ_BIN_PATH}emerald ] && [ "$USE_EMERALD" = "yes" ]; then
        verbose "Starting emerald\n"
        ${COMPIZ_BIN_PATH}emerald --replace &
elif [ -x ${COMPIZ_BIN_PATH}gtk-window-decorator ] && [ -n "$GNOME_DESKTOP_SESSION_ID" ]; then
        verbose "Starting gtk-window-decorator\n"
        ${COMPIZ_BIN_PATH}gtk-window-decorator --replace &
elif [ -x ${COMPIZ_BIN_PATH}kde-window-decorator ] && [ -n "$KDE_FULL_SESSION" ]; then
        verbose "Starting kde-window-decorator\n"
        ${COMPIZ_BIN_PATH}kde-window-decorator --replace &
        FALLBACKWM="${KWIN}"
fi

${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS
```

---

### Post by michael37 on 2007-11-03
> **elightbo said:**
> I am having problems as well, 3d rendering works, but i am getting this error message when trying to enable compiz.  There was a post from combatwombat about whitelisting fglrx, but how exactly is that done?  

Checking for Xgl: not present. 
```
Detected PCI ID for VGA: 06:00.0 0300: 1002:7280 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6473 (8.37.6)
```


You are running 8.37.6 driver (which is great, and it works great for you too), so you need to install Xgl before you start compiz.  Please follow the HOWTO from the first page of this thread.

---

### Post by kyleau on 2007-11-04
Since I follow the "If you are upgrading from Feisty 7.04 or earlier versions and you have run Xgl before." steps, It still don't work, Then I try to install a fresh copy of gutsy.
And finally I get my x1600 to work by following the "If you are doing fresh install of Gutsy" steps.
Thank you for your how to michael37:)

---

### Post by elightbo on 2007-11-04
> **michael37 said:**
> You are running 8.37.6 driver (which is great, and it works great for you too), so you need to install Xgl before you start compiz.  Please follow the HOWTO from the first page of this thread.

I just re-followed that how-to using the upgrade post.  It is still giving me the same error message complaining about not having xgl.   

Thanks again,
~eric

---

### Post by rjbgbo on 2007-11-04
> **michael37 said:**
> Well, let's try here and see if I can help you... If yes, I will create a Wiki page.

[SIZE="7"]Before we begin -- supported hardware list[/SIZE]

*Taken from fglrx driver description for Gutsy.*

This version of the ATI driver officially supports:

 * FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400,
           V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128,
           X1-128, X1-256p
 * FireMV: 2200 (Single card PCI-e configuration)
 * Mobility FireGL: V5000, T2
 * Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300,
                    9800, 9600, 9550, 9500
 * Radeon Xpress: 200M series, 1250 IGP, 200 series
 * Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550,
           X300, 9800, 9700, 9600, 9550, 9500

ATI All-in-Wonder variants of the above cards/chips are also supported,
but video capture is not.

[SIZE="7"]If you are doing fresh install of Gutsy[/SIZE]

[LIST=1]
[*]Enable fgrlx driver.

Install linux-restricted-modules and restricted-manager provied in the restricted repositories:
```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". 

[*]Install xserver-xgl package
```
sudo apt-get install xserver-xgl
```
[*]Install compiz
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
```
[*]Reboot
[*]Log in.  3D effects should be enabled!
[*]Customize Compiz Fusion.
Select System &#8594; Preferences &#8594; Advanced Desktop Effects Settings
In the new window, General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size.  Set it to 4.
The other two options have to be left at 1.

Continue customization per Forlong's guide at [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

[/LIST]

I executed
OK!!!
:)

I left the normal effect.

My current one xorg.conf

```
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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor Genérico"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"Monitor Genérico"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

Testing with - [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6473 (8.37.6)

In the screen login it comes a bigger screen that 1280x1024, e a black screen before entering desktop.
My monitor: LCD 17'' custom. :(

---

### Post by michael37 on 2007-11-04
> **elightbo said:**
> I just re-followed that how-to using the upgrade post.  It is still giving me the same error message complaining about not having xgl.   

Thanks again,
~eric

OK I think you have broken xorg.org.  Why don't you try this:

- print out this message 'cause you will be offline for a little

- reboot and start in "recovery mode" (not graphical session)

- it will give you just a regular prompt 

- run 

 sudo dpkg-reconfigure -phigh xserver-xorg

and select fglrx driver.

- reboot into graphical mode.  What happens?

---

### Post by michael37 on 2007-11-04
> **rjbgbo said:**
> I executed
OK!!!
:)

I left the normal effect.

My current one xorg.conf

```
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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor Genérico"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"Monitor Genérico"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

Testing with - [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6473 (8.37.6)

In the screen login it comes a bigger screen that 1280x1024, e a black screen before entering desktop.
My monitor: LCD 17'' custom. :(

Same suggestion for you.

Why don't you try this:

- print out this message 'cause you will be offline for a little

- reboot and start in "recovery mode" (not graphical session)

- it will give you just a regular prompt

- run

sudo dpkg-reconfigure -phigh xserver-xorg

and select fglrx driver and resolution that you want for your display.

- reboot into graphical mode. What happens?

---

### Post by carlosjuero on 2007-11-04
I have given up on Compiz for multiple reasons. Namely? the XGL X Server slows my sessions down to a crawl, graphics updates are slow, effects are sluggish (firefox scrolls at a snails pace).

I am a tad irritated that my old file server that I just put Ubuntu onto had Compiz enabled by default with an old AGP ATI card - and it looks great. This machine has a newer card (X1650 PCIe) and it can't do compiz worth a darn with the proprietary drivers. If I turn off the proprietary and use the Ubuntu kernel drivers then I will lose the advanced functionality for OpenGL apps :/

---

### Post by michael37 on 2007-11-04
> **carlosjuero said:**
> I have given up on Compiz for multiple reasons. Namely? the XGL X Server slows my sessions down to a crawl, graphics updates are slow, effects are sluggish (firefox scrolls at a snails pace).

I am a tad irritated that my old file server that I just put Ubuntu onto had Compiz enabled by default with an old AGP ATI card - and it looks great. This machine has a newer card (X1650 PCIe) and it can't do compiz worth a darn with the proprietary drivers. If I turn off the proprietary and use the Ubuntu kernel drivers then I will lose the advanced functionality for OpenGL apps :/

Your XGL is slow because you don't have right driver.  Run fglrxinfo -display :0 and fglrxinfo -display :1 and convince yourself on both of your computers.  I am thinking Mesa nightmares.

The off-the-shelf driver from Gutsy supports X1600 but not X1650.  With your new shiny X1650 card, you are one of those rare people who do need to go through 8.42.3 driver installation.  Use [Envy](http://albertomilone.com/nvidia_scripts1.html) -- it makes installation simpler.

**Disclaimer** Read how much problem other people have before installing the 8.42.3 driver.  Do it only if you absolutely uncertainly need it.

---

### Post by carlosjuero on 2007-11-04
> **michael37 said:**
> Your XGL is slow because you don't have right driver.  Run fglrxinfo -display :0 and fglrxinfo -display :1 and convince yourself on both of your computers.  I am thinking Mesa nightmares.

The off-the-shelf driver from Gutsy supports X1600 but not X1650.  With your new shiny X1650 card, you are one of those rare people who do need to go through 8.42.3 driver installation.  Use [Envy](http://albertomilone.com/nvidia_scripts1.html) -- it makes installation simpler.

**Disclaimer** Read how much problem other people have before installing the 8.42.3 driver.  Do it only if you absolutely uncertainly need it.
Nope, fglrxinfo displays ATI data - I fixed the Mesa issue with some annoyance.

Installed the 8.42.3 and no difference (boy that was a nightmare :/ - ATI .. love to hate 'em)

I am thinking that the 8.42.3 drivers just don't work well with Compiz.

Heres my fglrxinfo from the machine with the X1650:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6958 Release

```

The file server (with the older card) isn't even using the fglrx driver.

---

### Post by kade on 2007-11-04
I have an Thinkpad t60 with an ati x1400.  What do you think will yield better performance: ATI 8.42 driver or older driver + XGL?  I've been looking at various threads trying to decide which route to go.

---

### Post by elightbo on 2007-11-04
> **michael37 said:**
> OK I think you have broken xorg.org.  Why don't you try this:

- print out this message 'cause you will be offline for a little

- reboot and start in "recovery mode" (not graphical session)

- it will give you just a regular prompt 

- run 

 sudo dpkg-reconfigure -phigh xserver-xorg

and select fglrx driver.

- reboot into graphical mode.  What happens?

Here is the output from compiz after doing that:

[HTML]ubuntified:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"[/HTML]

---

### Post by elightbo on 2007-11-04
michael37 -> Just so you know, it is only allowing me to pick refresh rates up to 60 Hz now as well.

---

### Post by michael37 on 2007-11-04
> **kade said:**
> I have an Thinkpad t60 with an ati x1400.  What do you think will yield better performance: ATI 8.42 driver or older driver + XGL?  I've been looking at various threads trying to decide which route to go.

Certainly 8.37.6 driver with Xgl.

---

### Post by michael37 on 2007-11-04
> **carlosjuero said:**
> Nope, fglrxinfo displays ATI data - I fixed the Mesa issue with some annoyance.

Installed the 8.42.3 and no difference (boy that was a nightmare :/ - ATI .. love to hate 'em)

I am thinking that the 8.42.3 drivers just don't work well with Compiz.


How about fgrlxinfo -display :1?  Are you running Xgl?

If unsure, restart compiz (compiz --replace --disable-sm) and copy here the messages.

---

### Post by michael37 on 2007-11-04
> **elightbo said:**
> michael37 -> Just so you know, it is only allowing me to pick refresh rates up to 60 Hz now as well.

Well, it probed your monitor.  Something is very much not healthy with your xorg.conf.  Please post your  /etc/X11/xorg.conf  and /var/log/Xorg.0.log.

---

### Post by michael37 on 2007-11-04
Suggestion from another forum for all you Mesa nightmare sufferers.
```

sudo apt-get --purge remove xorg-driver-fglrx
sudo apt-get install xorg-driver-fglrx

```
reboot

---

### Post by elightbo on 2007-11-04
> **michael37 said:**
> Well, it probed your monitor.  Something is very much not healthy with your xorg.conf.  Please post your  /etc/X11/xorg.conf  and /var/log/Xorg.0.log.

```
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
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        BusID           "PCI:6:0:0"
EndSection

Section "Extensions"
        Option          "Composite"     "0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

```

```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux ubuntified 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov  4 22:06:58 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,277c card 1043,8178 rev c0 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,277d card 0000,0000 rev c0 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1043,81d8 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,27e0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,27e2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1043,8179 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1043,8179 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 1043,8179 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1043,8179 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c3 card 1043,2604 rev 01 class 01,04,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1043,8179 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:03:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:00:0: chip 11ab,6141 card 11ab,6141 rev 01 class 01,06,81 hdr 00
(II) PCI: 03:00:0: chip 11ab,4362 card 1043,8142 rev 20 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 11ab,4362 card 1043,8142 rev 20 class 02,00,00 hdr 00
(II) PCI: 06:00:0: chip 1002,7280 card 1458,2156 rev 00 class 03,00,00 hdr 80
(II) PCI: 06:00:1: chip 1002,72a0 card 1458,2157 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:1:0), (0,6,6), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 6 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xff900000 - 0xff9fffff (0x100000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0xcff00000 - 0xefefffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xcfe00000 - 0xcfefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:3), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xff800000 - 0xff8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:4), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xff700000 - 0xff7fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:5), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xff600000 - 0xff6fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xff500000 - 0xff5fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(6:0:0) ATI Technologies Inc ATI Radeon X1950 Pro Primary (PCIE) rev 0, Mem @ 0xd0000000/28, 0xff9f0000/16, I/O @ 0xc800/8, BIOS @ 0xff9c0000/17
(--) PCI: (6:0:1) ATI Technologies Inc ATI Radeon X1950 Pro Secondary (PCIE) rev 0, Mem @ 0xff9e0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xff8fc000 - 0xff8fffff (0x4000) MX[B]
	[1] -1	0	0xff7fc000 - 0xff7fffff (0x4000) MX[B]
	[2] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[3] -1	0	0xff5f8000 - 0xff5fbfff (0x4000) MX[B]
	[4] -1	0	0xff5ff800 - 0xff5fffff (0x800) MX[B]
	[5] -1	0	0xffafb800 - 0xffafbbff (0x400) MX[B]
	[6] -1	0	0xffafbc00 - 0xffafbfff (0x400) MX[B]
	[7] -1	0	0xffafc000 - 0xffafffff (0x4000) MX[B]
	[8] -1	0	0xff9e0000 - 0xff9effff (0x10000) MX[B](B)
	[9] -1	0	0xff9c0000 - 0xff9dffff (0x20000) MX[B](B)
	[10] -1	0	0xff9f0000 - 0xff9fffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[13] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[14] -1	0	0x00009480 - 0x0000949f (0x20) IX[B]
	[15] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[16] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[17] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[18] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[19] -1	0	0x0000d880 - 0x0000d88f (0x10) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[22] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[30] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[31] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[32] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xff8fc000 - 0xff8fffff (0x4000) MX[B]
	[1] -1	0	0xff7fc000 - 0xff7fffff (0x4000) MX[B]
	[2] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[3] -1	0	0xff5f8000 - 0xff5fbfff (0x4000) MX[B]
	[4] -1	0	0xff5ff800 - 0xff5fffff (0x800) MX[B]
	[5] -1	0	0xffafb800 - 0xffafbbff (0x400) MX[B]
	[6] -1	0	0xffafbc00 - 0xffafbfff (0x400) MX[B]
	[7] -1	0	0xffafc000 - 0xffafffff (0x4000) MX[B]
	[8] -1	0	0xff9e0000 - 0xff9effff (0x10000) MX[B](B)
	[9] -1	0	0xff9c0000 - 0xff9dffff (0x20000) MX[B](B)
	[10] -1	0	0xff9f0000 - 0xff9fffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[13] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[14] -1	0	0x00009480 - 0x0000949f (0x20) IX[B]
	[15] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[16] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[17] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[18] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[19] -1	0	0x0000d880 - 0x0000d88f (0x10) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[22] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[30] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[31] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[32] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8fc000 - 0xff8fffff (0x4000) MX[B]
	[5] -1	0	0xff7fc000 - 0xff7fffff (0x4000) MX[B]
	[6] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[7] -1	0	0xff5f8000 - 0xff5fbfff (0x4000) MX[B]
	[8] -1	0	0xff5ff800 - 0xff5fffff (0x800) MX[B]
	[9] -1	0	0xffafb800 - 0xffafbbff (0x400) MX[B]
	[10] -1	0	0xffafbc00 - 0xffafbfff (0x400) MX[B]
	[11] -1	0	0xffafc000 - 0xffafffff (0x4000) MX[B]
	[12] -1	0	0xff9e0000 - 0xff9effff (0x10000) MX[B](B)
	[13] -1	0	0xff9c0000 - 0xff9dffff (0x20000) MX[B](B)
	[14] -1	0	0xff9f0000 - 0xff9fffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[20] -1	0	0x00009480 - 0x0000949f (0x20) IX[B]
	[21] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[22] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[23] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[24] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[25] -1	0	0x0000d880 - 0x0000d88f (0x10) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[28] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[36] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[37] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[38] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[39] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Primary Device is: PCI 06:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.37.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.37g1                           
(II) ATI Proprietary Linux Driver Build Date: May 25 2007 14:25:03
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.37.1.1.2.3-driver-lnx-x86-x86_64-346145
(WW) fglrx: No matching Device section for instance (BusID PCI:6:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x7280) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8fc000 - 0xff8fffff (0x4000) MX[B]
	[5] -1	0	0xff7fc000 - 0xff7fffff (0x4000) MX[B]
	[6] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[7] -1	0	0xff5f8000 - 0xff5fbfff (0x4000) MX[B]
	[8] -1	0	0xff5ff800 - 0xff5fffff (0x800) MX[B]
	[9] -1	0	0xffafb800 - 0xffafbbff (0x400) MX[B]
	[10] -1	0	0xffafbc00 - 0xffafbfff (0x400) MX[B]
	[11] -1	0	0xffafc000 - 0xffafffff (0x4000) MX[B]
	[12] -1	0	0xff9e0000 - 0xff9effff (0x10000) MX[B](B)
	[13] -1	0	0xff9c0000 - 0xff9dffff (0x20000) MX[B](B)
	[14] -1	0	0xff9f0000 - 0xff9fffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[20] -1	0	0x00009480 - 0x0000949f (0x20) IX[B]
	[21] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[22] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[23] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[24] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[25] -1	0	0x0000d880 - 0x0000d88f (0x10) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[28] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[36] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[37] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[38] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[39] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8206c48
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff8fc000 - 0xff8fffff (0x4000) MX[B]
	[5] -1	0	0xff7fc000 - 0xff7fffff (0x4000) MX[B]
	[6] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[7] -1	0	0xff5f8000 - 0xff5fbfff (0x4000) MX[B]
	[8] -1	0	0xff5ff800 - 0xff5fffff (0x800) MX[B]
	[9] -1	0	0xffafb800 - 0xffafbbff (0x400) MX[B]
	[10] -1	0	0xffafbc00 - 0xffafbfff (0x400) MX[B]
	[11] -1	0	0xffafc000 - 0xffafffff (0x4000) MX[B]
	[12] -1	0	0xff9e0000 - 0xff9effff (0x10000) MX[B](B)
	[13] -1	0	0xff9c0000 - 0xff9dffff (0x20000) MX[B](B)
	[14] -1	0	0xff9f0000 - 0xff9fffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[23] -1	0	0x00009480 - 0x0000949f (0x20) IX[B]
	[24] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[25] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[26] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[27] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[28] -1	0	0x0000d880 - 0x0000d88f (0x10) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[31] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[39] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[40] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[41] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[42] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[43] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[44] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 6 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "Radeon X1950 Series" (Chipset = 0x7280)
(--) fglrx(0): (PciSubVendor = 0x1458, PciSubDevice = 0x2156)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xff9f0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.13
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV570
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(WW) fglrx(0): GetVBEMode failed
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.37.6
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDRX
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: NEC  Model: 61d2  Serial#: 16843009
(II) fglrx(0): Year: 2002  Week: 44
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 24
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.322   greenX: 0.277 greenY: 0.598
(II) fglrx(0): blueX: 0.145 blueY: 0.062   whiteX: 0.283 whiteY: 0.297
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 720x400@88Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 70  vid: 19057
(II) fglrx(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #5: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 94.5 MHz   Image Size:  310 x 232 mm
(II) fglrx(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) fglrx(0): Ranges: V min: 55  V max: 120 Hz, H min: 31  H max: 70 kHz, PixClock max 110 MHz
(II) fglrx(0): Monitor name: MultiSync 77F
(II) fglrx(0): Serial No: 2Y01689YA
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0038a3d26101010101
(II) fglrx(0): 	2c0c01030c211878eae038a352479925
(II) fglrx(0): 	0f484cffee00315945596159714a8140
(II) fglrx(0): 	818001010101ea240060410028303060
(II) fglrx(0): 	130036e81000001e000000fd0037781f
(II) fglrx(0): 	460b000a202020202020000000fc004d
(II) fglrx(0): 	756c746953796e6320373746000000ff
(II) fglrx(0): 	003259303136383959410a2020200022
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 21 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0):  Default mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(0): Modeline "720x576"   26.56  720 736 808 896  576 577 580 593 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (330, 240) mm
(--) fglrx(0): DPI set to (98, 108)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0):  Default mode "720x576": 26.6 MHz (scaled from 0.0 MHz), 29.6 kHz, 50.0 Hz
(II) fglrx(0): Modeline "720x576"   26.56  720 736 808 896  576 577 580 593 +hsync
(**) fglrx(0):  Default mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) LoadModule: "glesx.so" (glesx)
(WW) LoadModule: given non-canonical module name "glesx.so"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xff9f0000 - 0xff9fffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xff8fc000 - 0xff8fffff (0x4000) MX[B]
	[7] -1	0	0xff7fc000 - 0xff7fffff (0x4000) MX[B]
	[8] -1	0	0xff6ffc00 - 0xff6fffff (0x400) MX[B]
	[9] -1	0	0xff5f8000 - 0xff5fbfff (0x4000) MX[B]
	[10] -1	0	0xff5ff800 - 0xff5fffff (0x800) MX[B]
	[11] -1	0	0xffafb800 - 0xffafbbff (0x400) MX[B]
	[12] -1	0	0xffafbc00 - 0xffafbfff (0x400) MX[B]
	[13] -1	0	0xffafc000 - 0xffafffff (0x4000) MX[B]
	[14] -1	0	0xff9e0000 - 0xff9effff (0x10000) MX[B](B)
	[15] -1	0	0xff9c0000 - 0xff9dffff (0x20000) MX[B](B)
	[16] -1	0	0xff9f0000 - 0xff9fffff (0x10000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[26] -1	0	0x00009480 - 0x0000949f (0x20) IX[B]
	[27] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[28] -1	0	0x00009880 - 0x00009883 (0x4) IX[B]
	[29] -1	0	0x00009c00 - 0x00009c07 (0x8) IX[B]
	[30] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[31] -1	0	0x0000d880 - 0x0000d88f (0x10) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[34] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[36] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[41] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[42] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[43] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[44] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[45] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:6:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:6:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7fb4000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.37.6
(II) fglrx(0):     Date: May 25 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x00701000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): GLESX enableFlags = 16
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:6:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:6:0:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetClientVersion: 0 9

```

---

### Post by michael37 on 2007-11-04
> **elightbo said:**
> <snip>

Try these commands (post the output here please)

sudo apt-get --purge remove xserver-xgl

and then

sudo apt-get install xserver-xgl

and then reboot

and then if compiz keeps giving you trouble, do 

compiz --replace

and lastly, post the output of 

fglrxinfo -display :0
fglrxinfo -display :1

---

### Post by elightbo on 2007-11-05
> **michael37 said:**
> 
Try these commands (post the output here please)

sudo apt-get --purge remove xserver-xgl

and then

sudo apt-get install xserver-xgl

and then reboot

and then if compiz keeps giving you trouble, do

compiz --replace

and lastly, post the output of

fglrxinfo -display :0
fglrxinfo -display :1



sudo apt-get --purge remove xserver-xgl
```
[sudo] password for lightbodys:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xgl*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 4510kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 130187 files and directories currently installed.)
Removing xserver-xgl ...
Purging configuration files for xserver-xgl ...

```


sudo apt-get install xserver-xgl
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1737kB of archives.
After unpacking 4510kB of additional disk space will be used.
Selecting previously deselected package xserver-xgl.
(Reading database ... 130168 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_1%3a1.1.99.1~git20070727-0ubuntu3_i386.deb) ...
Setting up xserver-xgl (1:1.1.99.1~git20070727-0ubuntu3) ...

```

compiz --replace
```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

fglrxinfo -display :0
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6473 (8.37.6)

```

fglrxinfo -display :1 brings back nothing

---

### Post by opolette on 2007-11-05
Hi,

Thank you for this great tuto.
I must add that it works also with the ATI RADEON 7500 (despite the fact that it is not listed in the list of supported cards).
Only, the screen refresh seems to be a bit slower now (maybe because of XGL?)

Thanks

---

### Post by Nikos.Alexandris on 2007-11-05
> **elightbo said:**
> sudo apt-get --purge remove xserver-xgl
```
[sudo] password for lightbodys:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xgl*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 4510kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 130187 files and directories currently installed.)
Removing xserver-xgl ...
Purging configuration files for xserver-xgl ...

```


sudo apt-get install xserver-xgl
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1737kB of archives.
After unpacking 4510kB of additional disk space will be used.
Selecting previously deselected package xserver-xgl.
(Reading database ... 130168 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_1%3a1.1.99.1~git20070727-0ubuntu3_i386.deb) ...
Setting up xserver-xgl (1:1.1.99.1~git20070727-0ubuntu3) ...

```

compiz --replace
```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

fglrxinfo -display :0
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6473 (8.37.6)

```

fglrxinfo -display :1 brings back nothing

Have you "whitelisted" your fglrx driver, if  you use this driver of course?

Have a look at [[COLOR="Blue"]http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") in the  **3D desktop effects** section.

---

### Post by carlosjuero on 2007-11-05
> **michael37 said:**
> How about fgrlxinfo -display :1?  Are you running Xgl?

If unsure, restart compiz (compiz --replace --disable-sm) and copy here the messages.

To help with test benchmarking I reinstalled Compiz and XGL - heres the info you asked for:

fglrxinfo Display 0:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6958 Release

```

Display 1:
```

display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

```

compiz --replace output:
```

compiz --replace --disable-sm
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: Unknown option '--disable-sm'

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Edit: attached xorg.conf file

---

### Post by jack handy on 2007-11-05
i've got a dell with the ATI radeon mobility x1400.  is there any hope at all to get my movies playing correctly (with the right colors) and to get some of the desktop effects running?

---

### Post by kade on 2007-11-05
> **michael37 said:**
> Certainly 8.37.6 driver with Xgl.

Thanks for the advice.  I've installed Xgl and Compiz is working flawlessly.  Now I can go about customizing my desktop. :smile:

---

### Post by michael37 on 2007-11-05
> **Nikos.Alexandris said:**
> Have you "whitelisted" your fglrx driver, if  you use this driver of course?

Have a look at [[COLOR="Blue"]http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") in the  **3D desktop effects** section.

Nikos, this link instructs users to install a VERY RISKY UNSTABLE 8.42.3 driver.  The driver does not work for majority of ATI-Ubuntu users.  If you look earlier in the thread, **elightbo** posted their /var/log/Xorg.0.log file where fglrx driver is clearly initialized, so your suggestion will not help.  Please do not instruct to use the 8.42 driver blindly unless there is a specific reason for it.

---

### Post by michael37 on 2007-11-05
> **jack handy said:**
> i've got a dell with the ATI radeon mobility x1400.  is there any hope at all to get my movies playing correctly (with the right colors) and to get some of the desktop effects running?

Guess what, I got a Dell Inspiron E1505 laptop with ATI Radeon Mobility x1400 and I can't complain about my desktop effects and about my movie playback.  Sounds familiar :) ?
Actually, my kid prefers cartoons off youtube on my laptop...

---

### Post by michael37 on 2007-11-05
> **carlosjuero said:**
> To help with test benchmarking I reinstalled Compiz and XGL - heres the info you asked for:

fglrxinfo Display 0:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6958 Release

```

Display 1:
```

display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

```

compiz --replace output:
```

compiz --replace --disable-sm
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: Unknown option '--disable-sm'

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Edit: attached xorg.conf file

You screwed yourself by installing the 8.40 or 8.42 ATI driver.  It doesn't work (Nikos, are you reading this?) for you -- your fglrxinfo -display :1 shows "Mesa nightmare" instead of proper ATI output.  Try uninstalling that driver -- however you unstalled it and load back the Gutsy supported 8.37 driver : once you uninstall the broken driver, enable ATI accelerated driver in Restricted Drivers Manager.  Don't try to use the Restricted Drivers manager before uninstalling the broken one though, it won't work and will break your system even further.

---

### Post by michael37 on 2007-11-05
> **elightbo said:**
> sudo apt-get --purge remove xserver-xgl
```
[sudo] password for lightbodys:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xgl*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 4510kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 130187 files and directories currently installed.)
Removing xserver-xgl ...
Purging configuration files for xserver-xgl ...

```


sudo apt-get install xserver-xgl
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1737kB of archives.
After unpacking 4510kB of additional disk space will be used.
Selecting previously deselected package xserver-xgl.
(Reading database ... 130168 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_1%3a1.1.99.1~git20070727-0ubuntu3_i386.deb) ...
Setting up xserver-xgl (1:1.1.99.1~git20070727-0ubuntu3) ...

```

compiz --replace
```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

fglrxinfo -display :0
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6473 (8.37.6)

```

fglrxinfo -display :1 brings back nothing

**elightbo**, dumb question: are you 100% sure you are running Gutsy?  Your system is responding as if it's a Feisty, and not Gutsy.

Could you please give me the output of this command:  ```
grep -i xgl  -C 1 /etc/gdm/*
```

---

### Post by michael37 on 2007-11-05
> **opolette said:**
> Hi,

Thank you for this great tuto.
I must add that it works also with the ATI RADEON 7500 (despite the fact that it is not listed in the list of supported cards).
Only, the screen refresh seems to be a bit slower now (maybe because of XGL?)

Thanks

Actually, it's more likely your card itself.  It's not the freshest graphics card, you know, and 3D operations used by Xgl and Compiz is fairly graphics-intensive.  Time for a new video card :) ?

---

### Post by carlosjuero on 2007-11-05
> **michael37 said:**
> You screwed yourself by installing the 8.40 or 8.42 ATI driver.  It doesn't work (Nikos, are you reading this?) for you -- your fglrxinfo -display :1 shows "Mesa nightmare" instead of proper ATI output.  Try uninstalling that driver -- however you unstalled it and load back the Gutsy supported 8.37 driver : once you uninstall the broken driver, enable ATI accelerated driver in Restricted Drivers Manager.  Don't try to use the Restricted Drivers manager before uninstalling the broken one though, it won't work and will break your system even further.

8.42 yeah. Ok, I will try uninstalling it and then using the Gutsy supported version.

---

### Post by jack handy on 2007-11-05
ok, so i still cant get desktop effects going, 

here's my fglrxinfo after the manual install:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6958 Release
```

and here's my xorg.conf:

```
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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection
```


what can i do?

EDIT;  correction:  avi's are playing fine now.  but i'd still like to get the desktop effects going.

---

### Post by carlosjuero on 2007-11-05
> **michael37 said:**
> You screwed yourself by installing the 8.40 or 8.42 ATI driver.  It doesn't work (Nikos, are you reading this?) for you -- your fglrxinfo -display :1 shows "Mesa nightmare" instead of proper ATI output.  Try uninstalling that driver -- however you unstalled it and load back the Gutsy supported 8.37 driver : once you uninstall the broken driver, enable ATI accelerated driver in Restricted Drivers Manager.  Don't try to use the Restricted Drivers manager before uninstalling the broken one though, it won't work and will break your system even further.

Well, uninstalling the 8.42's broke my system. Just uninstalling them broke it, now I can't get X to get the display settings right, and the 8.37's won't 'take' (nor will the Restricted Graphics Manager option 'stick').

I went from just not being able to use Compiz, to not being able to use anything except for the safe terminal.

I have tried forcing a reconfigure of the X server (sudo dpkg-reconfigure -phigh xserver-xorg), I have tried choosing different drivers, uninstalling/reinstalling the fglrx drivers, just about everything. I am hoping this will not require a fresh install, cause that will drive me up the wall :( [even though it will go smoothly].

No idea what to do next, not gonna do anything more for at least a few hours (I am on Windows side now) but any suggestions?

---

### Post by elightbo on 2007-11-05
> **michael37 said:**
> **elightbo**, dumb question: are you 100% sure you are running Gutsy?  Your system is responding as if it's a Feisty, and not Gutsy.  

Could you please give me the output of this command:  ```
grep -i xgl  -C 1 /etc/gdm/*
```

Unfortunately, it's Gutsy.  When I go to System -> About Ubuntu, I get a  Thank you for your interest in 7.10 Gutsy Gibbon

Thanks for your persistance with this!

```

/etc/gdm/factory-gdm.conf-# How long gdm should wait before it assumes a started Xserver is defunct and
/etc/gdm/factory-gdm.conf:# kills it.  10 seconds should be long enough for X, but Xgl may need 20 or 25. 
/etc/gdm/factory-gdm.conf-GdmXserverTimeout=10
--
/etc/gdm/gdm.conf-# How long gdm should wait before it assumes a started Xserver is defunct and
/etc/gdm/gdm.conf:# kills it.  10 seconds should be long enough for X, but Xgl may need 20 or 25. 

```

---

### Post by carlosjuero on 2007-11-06
> **carlosjuero said:**
> Well, uninstalling the 8.42's broke my system. Just uninstalling them broke it, now I can't get X to get the display settings right, and the 8.37's won't 'take' (nor will the Restricted Graphics Manager option 'stick').

I went from just not being able to use Compiz, to not being able to use anything except for the safe terminal.

I have tried forcing a reconfigure of the X server (sudo dpkg-reconfigure -phigh xserver-xorg), I have tried choosing different drivers, uninstalling/reinstalling the fglrx drivers, just about everything. I am hoping this will not require a fresh install, cause that will drive me up the wall :( [even though it will go smoothly].

No idea what to do next, not gonna do anything more for at least a few hours (I am on Windows side now) but any suggestions?

Quoting myself to update.

Ok, so I went into recovery and manually removed everything related to the video settings and created a fresh xorg.conf with vesa drivers.

I then booted into GNOME, installed the 8.37's (restricted drivers enabled).. and Compiz did absolutely nothing [couldn't enable the advanced effects]. The fglrxinfo displayed ATI for both screens, but with the 'missing XFree86-DRI' error on screen 1.

I tried 8.39 & 8.40 drivers as well and ended up with corrupted graphics and an unstable X environment.

I am so sick of trying to get compiz working that I am just going to forgo any further tinkering related to it until things get better driver wise (or whatever has to be fixed). I re-installed the 8.42's (after some more annoyances) and am running just fine now without Compiz.

I know I can get Compiz running jaggedly on the 8.42's, but with the slow performance of scrolling in Firefox and effects (as well as the inability to play any OpenGL games via Cedega/Wine) isn't worth it.

It seems to be all on ATI's end at least, hopefully the next driver canidate will work out better.

Edit (final update I promise :)) -

Ok, I got compiz effects working... without the xserver-xgl. How did I do it? All I did was what one of the ATI pages suggested and added fglrx to the /usr/bin/compiz Whitelist section.

Thats it. Scrolling is still slow in FireFox - but it seems to be any full screen app that does this :/ - I can run my OpenGL games by just disabling compiz temporarily for the gaming session. This took a heck of a lot less time and effort than dealing with the xserver-xgl and older driver sets; Hopefully the next round of ATI drivers smooths things out a bit more.

---

### Post by Hoenheim on 2007-11-06
> **michael37 said:**
> What video card do you have?
lspci | grep ATI

05:00.0 VGA compatible controller: ATI Technologies Inc R423 UK [Radeon X800SE (PCIE)]
05:00.1 Display controller: ATI Technologies Inc Radeon R423 UK (PCIE) [X800 SE] (Secondary)

---

### Post by jonray74 on 2007-11-06
I tried this guide and it load up Compiz-Fusion on my Gutsy install, but after a few minutes my PC freezes for some unknown reason. I open up Firefox, or any application, and then everything freezes, even my cairo-clock won't work, and so is my desklets, although i can move my mouse pointer but couldn't click anything on the menu or on the desktop at all. :(

I have a Sapphire Radeon 9600 Pro 256MB, and it should work well with the Radeon card when I enable restricted drivers, but for some reason my PC freezes when its enabledr, anyone who experienced this problem i hope someone can help. Also, sometimes my PC freezes when the Screensaver starts up.

Thanks

---

### Post by torgrot on 2007-11-06
Hey Michael,

Thanks a lot.  I followed your How To and it worked like a champ on my Dell 4550 with ATI 9800.  This is the first time I have ever gotten it to work with the ATI driver.

Again Thanks.

Torgrot

---

### Post by Kwisniew on 2007-11-06
Thank you thank you,perfect write up. Had Fiesty upgrade same problems, nice job!

---

### Post by BrandonBan6 on 2007-11-07
Thanks for the Post Michael,

Here is what I am running into however......after the reboot after running the xserver-xgl install.....my system hangs up right after the initial login and reboots itself back to the login page. The only work around is to log into safe and unistall xserver-xgl........can you offer any advice? 

I'm using a ATI Radeon X300 vid card. 

thanks!

~b

---

### Post by luis.alves@lafaspot.com on 2007-11-07
*** Gutsy AIGLX and ATI fglrx works ***

I updated the ATI wiki

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

to describe how to configure ubuntu and kubuntu to work with AIGLX
and 3D effects.

---

### Post by Arituay on 2007-11-07
I am unable to get even fglrx working correctly.  I have followed all the steps in post #8 with no luck.  With Feisty I had fglrx and Big Desktop working fine (no compiz or anything like that though).  Now that I upgraded I can't get dual monitors working.  The Ubuntu Screens and Graphics interface doesn't work at all, it doesn't recognize that fglrx is the driver for my card even though in the restricted driver screen it is enabled and active as well as the fact that it is the driver specified in my xorg.conf.  No changes attempted in Screens and Graphics interface remain after the required restart.

So I tried using my xorg.conf that worked under Feisty (see below) and that won't work either.


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
	Screen      0  "aticonfig-Screen[0]" 0 0
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

Section "ServerFlags"
	Option	    "AIGLX" "off"
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
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "EnablePrivateBackZ" "yes"
	Option	    "HSync2" "65"
	Option	    "VRefresh2" "60"
	Option	    "PairModes" "1024x768+1024x768"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1024x768" "1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

When I do aticonfig --query-monitor I get:

```

Connected monitors: none
Enabled monitors: none

```

The xrandr command yields:
```

Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      60.0* 

```

fglrxinfo yields:
```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

```

glxinfo -display :0 yields:
```

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
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

uname -r :
```
2.6.22-14-generic
```

dpkg -l linux-restricted-modules-2.6.22-14-generic :
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-restrict 2.6.22.4-14.9  Non-free Linux 2.6.22 modules on x86/x86_64

```

dpkg -l linux-image-2.6.22-14-generic :
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  linux-image-2. 2.6.22-14.46   Linux kernel image for version 2.6.22 on x86
```


lsmod | grep fglrx :
```
fglrx                 656352  0 
agpgart                35016  1 fglrx

```

modinfo fglrx :```

filename:       /lib/modules/2.6.22-14-generic/volatile/fglrx.ko
depends:        agpgart
vermagic:       2.6.22-14-generic SMP mod_unload 586 
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
parm:           firegl:charp
```

dpkg -l xorg-driver-fglrx :
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  xorg-driver-fg 7.1.0-8.37.6+2 Video driver for ATI graphics accelerators

```




Any help on this is much appreciated, thanks,

Arituay

---

### Post by michael37 on 2007-11-08
Thanks to everyone for interest in this thread.  I am going out of country for about two weeks and won't be able to reply to any questions.  I hope there are a lot of Gutsy users by now who figured our how to run Xgl+ATI fglrx+Compiz who can answer the questions!

Good luck everyone!

---

### Post by Hoenheim on 2007-11-08
When I go to restricted drivers it says the driver is enabled but status is not in use.
Anyone know how to solve this

This is my video card:
05:00.0 VGA compatible controller: ATI Technologies Inc R423 UK [Radeon X800SE (PCIE)]
05:00.1 Display controller: ATI Technologies Inc Radeon R423 UK (PCIE) [X800 SE] (Secondary)

---

### Post by chodak on 2007-11-08
Okay. I've read through pretty much the whole thread, I followed the guide from the beginning, removing old attempts with the --purge option, I had the "MESA issue" before, but that's fixed thanks to the great advice of combatwombat_nz. However, I am still not able to enable desktop effects, when I do so in System -> Preferences -> Appearance, I get a helpful "Desktop effects could not be enabled" error. This is the most annoying problem I've had with Ubuntu so far and I'm getting to the point of giving up... Can anyone give some advice?

I did not install xgl, as per CombatWombat, so I could use AIGLX. Could this be it?

Here's my info:

```
$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6473 (8.37.6)

$ fglrxinfo -display :1
Error: unable to open display :1
```

xorg.conf
```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc101"
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
	Identifier   "DELL 2007WFP"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV530 [Radeon X1600]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV530 [Radeon X1600]"
	Monitor    "DELL 2007WFP"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection
```

ATI driver is enabled in Restricted drivers and I whitelisted fglrx with compiz. Oh, and I did the SKIP_CHECKS thing, too. Still no luck. :confused:

---

### Post by PPPP on 2007-11-10
Thanks for the guide! One thing of note is I couldn't get GUI to work, had to do ctrl+alt+f1 to get to the command line.

then had to run:

```
sudo dpkg-reconfigure xserver-xorg
```

Then X started fine.  I followed the rest of the instructions and it works just great :)

Now I'm just wondering...before I was using Feisty and I found Xgl to have memory leak and requires me to reboot every so often.  Is it better now with Gutsy?  Or is it better to go with AIGLX?  I've read a few posts where people complained about AIGLX's performance.  Anyone want to comment on that?

---

### Post by RavanH on 2007-11-10
I have not read this whole thread, so this might already have been mentioned ---

**TIP** for anybody here that tries to use the latest 8.42.3 with AIGLX to get that eye-candy: Following [_**this how-to**_]("http://ubuntuforums.org/showthread.php?t=589075") did the trick for me, with special attention to the last addition to the how-to where it mentions "Check the next section to make sure your card is not blacklisted." -- this turned out to be crucial for me... read on in that thread to find out more on how to get your card off of the outdated compiz-fusion blacklist.

Good luck :)

---

### Post by spacegypsy on 2007-11-10
> **michael37 said:**
> Well, let's try here and see if I can help you... If yes, I will create a Wiki page.

[SIZE="7"]Before we begin -- supported hardware list[/SIZE]

*Taken from fglrx driver description for Gutsy.*

This version of the ATI driver officially supports:

 * FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400,
           V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128,
           X1-128, X1-256p
 * FireMV: 2200 (Single card PCI-e configuration)
 * Mobility FireGL: V5000, T2
 * Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300,
                    9800, 9600, 9550, 9500
 * Radeon Xpress: 200M series, 1250 IGP, 200 series
 * Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550,
           X300, 9800, 9700, 9600, 9550, 9500

ATI All-in-Wonder variants of the above cards/chips are also supported,
but video capture is not.

[SIZE="7"]If you are doing fresh install of Gutsy[/SIZE]

[LIST=1]
[*]Enable fgrlx driver.

Install linux-restricted-modules and restricted-manager provied in the restricted repositories:
```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". 

[*]Install xserver-xgl package
```
sudo apt-get install xserver-xgl
```
[*]Install compiz
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
```
[*]Reboot
[*]Log in.  3D effects should be enabled!
[*]Customize Compiz Fusion.
Select System &#8594; Preferences &#8594; Advanced Desktop Effects Settings
In the new window, General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size.  Set it to 4.
The other two options have to be left at 1.

Continue customization per Forlong's guide at [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

[/LIST]

thanks michael37

just what I needed

works perfect with my X700 card

:):):)

---

### Post by csioucs on 2007-11-11
First: I have a Thinkpad T60, with Ati X1300. 

The default, nonrestricted drivers, got me suspend/hibernation working but no effects. As this was my first longer connection to ubuntu, I wanted to try it out.

So, before I am going to go by Feisty to see how it is there, since I read that in Feisty the effects and the suspend/hibernation work, I will say how I got my effects going: Credit is not mine, but I got some week ago, and I do not recall where and whom to give credit. It was someone from the compiz forums:
Before this backup your xorg.conf, that is to save it some place else....or similar.

This was the solution:

Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your card...

---

### Post by soxs on 2007-11-11
I am using the latest driver from the ati/amd homepage (installed via the gui-interface which works like a charm) replacing "ati" with "fglrx" in the xorg.conf (at least make sure that it's there), composite enabled and compiz works fine. xserver-xgl is not required anymore.
You may additionally have to edit ```
/usr/bin/compiz
``` and change  this line (#54) to  ```
WHITELIST="nvidia intel ati radeon fglrx i810"
```
This enables compiz to run, no matter if it officially suports that driver or not, I myself did not. (ATI RADEON 9500PRO/9700)

---

### Post by MeneK on 2007-11-11
I wrote a tiny Python app to easily enable / disable Xgl (my first Python program!). Use it at your will.

---

### Post by opolette on 2007-11-12
> **michael37 said:**
> Actually, it's more likely your card itself.  It's not the freshest graphics card, you know, and 3D operations used by Xgl and Compiz is fairly graphics-intensive.  Time for a new video card :) ?

Actually not. The RADEON 7500 supports natively lots of graphic operations and it should not be that slow.

It was due to XGL.

I could have my card run perfectly with compiz by using AIGLX.

All you have to do is:

1 - Remove XLG:

```
# sudo apt-get --purge remove xserver-xgl
```

2 - Install AIGLX support:
```

# apt-get update
# apt-get install libgl1-mesa-glx libgl1-mesa-dri
```

3 - Modify /etc/X1/xorg.conf by adding following lines in "Device" section:
```

    	Option 		"XAANoOffscreenPixmaps" "true"
	Option 		"AddARGBGLXVisuals" "true"
	Option 		"AllowGLXWithComposite" "true"
```

4 - Modify /etc/X1/xorg.conf by adding (or updating) "Extensions" section: 

```
Section "Extensions"
    Option "Composite" "Enable"
EndSection
```


And now it is fast even with my old RADEON 7500 !!!!

Bye

---

### Post by skychris on 2007-11-12
Hi, 
like many, I struggle to set up my ATI card on my laptop that I upgraded from feisty to gutsy. I went trough quit a lot of post with quite a lot of "how to's" some did a good work some didn't. basically I came down to this problem :

output of  lspci|grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

output of fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6958 Release

output of  glxinfo
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


what am I missing here? I have compiz installed and working, but some soft using 3d effect, like google earth, crash my session and brings me back to the login page...

any ideas??

BTW, I'm still fairly new at linux and I'm not yet quite sure on "what does what where" ...:)

---

### Post by skychris on 2007-11-12
following my last post, here's my xorg.conf


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

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection


Thanks a lot for your help

---

### Post by soxs on 2007-11-12
first, @ all: plx use code tags, or oyur posts look realy ugly and plx reduce the output of glxinfo to what is really required!
@opolette: xgl-xserver lags for me aswell as hell (RADEON 9500PRO/9700)

@skychris: you do not have direct rendering enabled, I suggest you to try removing your ati graphics driver and reinstall it. (type ```
glxinfo|grep direct
``` into a console and you'll see what I mean, fglrxinfo has nothing to say)

---

### Post by skychris on 2007-11-12
```
first, @ all: plx use code tags, or oyur posts look realy ugly and plx reduce the output of glxinfo to what is really required!
@opolette: xgl-xserver lags for me aswell as hell (RADEON 9500PRO/9700)

@skychris: you do not have direct rendering enabled, I suggest you to try removing your ati graphics driver and reinstall it. (type
Code:

glxinfo|grep direct

into a console and you'll see what I mean, fglrxinfo has nothing to say)
```

thanks socks, 

I kinda figured that I only had a partially installed driver. How can I do a clean removal of it, with nothing left behind, as I installed and desinstalled my driver several time depending on the "How to" I was following. None of them cover all of the particularities of a specific hardware setup (... and it's normal :) ) but I feel like I want to go somewhere with a citymap in pieces, and it's not so easy to follow the right track sometime...I mostly followed those two threads

[http://ubuntuforums.org/showthread.php?t=575843&highlight=gutsy+ati+driver](http://ubuntuforums.org/showthread.php?t=575843&highlight=gutsy+ati+driver)
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

thanks for your help, and I will work on my post's look as well :lolflag:

---

### Post by skychris on 2007-11-12
before desinstalling everything, I tried something else I saw in another thread.
I typed > glxinfo and I got
> OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
OpenGL extensions:


then I typed >  aticonfig --query-monitor
and I got >  Connected monitors: none
  Enabled monitors: none


then > chris@chris-laptop:~$ export DISPLAY=:0
chris@chris-laptop:~$ aticonfig --query-monitor
  Connected monitors: lvds
  Enabled monitors: lvds


and I got > glxinfo
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6958 Release


wich is exactly what I want. but for some reason, this setting is not saved, if I close the Terminal window and open it again, it's back as before


:confused::confused:

---

### Post by Znupi on 2007-11-12
I'm having a problem. I did a fresh install of Gusty and... the restricted drivers don't work :(. If I choose to use them and reboot, Ubuntu enters "low-graphics mode" until I uninstall the drivers and choose to use the open-source fglrx. On Feisty, the restricted drivers worked perfectly and I was able to install Beryl with them.

I have an Ati Radeon X550 Card with 512 MB of RAM. Is there any chance to get Compiz Fusion working with the open-source fglrx drivers? :-s

---

### Post by soxs on 2007-11-14
@skychris: It seems to me that```
aticonfig
``` has no writing permissions to xorg.conf. Are you root? Otherwise it can not work. NOTE: Make a backup! ```
 cp -vf /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
``` and copy pack if it fails  ```
 cp -vf /etc/X11/xorg.conf.mybackup /etc/X11/xorg.conf
``` (do this as root)
Note: Imyself edit the xorg.conf ALWAYS manually, so I am not expirienced with aticonfig-tools at all.
Note: I've atteched my xorg.conf, so you can have a look at mine, especially the device section and serverlayout sections are important. If you have no clue at all, attach it here.

@Znupi: Yes, but you have to install xserver-xgl via synaptic or via ```
sudo apt-get install xserver-xgl
``` but I suggest you NOT to do this. Your problem is likly to be caused by messed up/bad configured xorg.conf (/etc/X11/xorg.conf). Attach it and I'll have a look at it.
Did you check if the latest ati driver was installed correctly via ```
glxinfo|grep direct
``` and ```
fglrxinfo
```? Did you setup your xorg.conf manually or with aticonfig? Did you save a backup of your xorg.conf you used before?

---

### Post by rmfought on 2007-11-14
Holy crap, it just worked!  :)  I love it when that happens.  I now have beautiful desktop effects on my Radeon Mobility X700 laptop.

This is the kind of stuff that makes Ubuntu kick ***.

---

### Post by carli on 2007-11-14
Hi guys!

I gave up making desktop effects work on my Acer TM8210 w/ATI Mobility X1600.

I noticed during the process that if I enabled the restricted driver it got slow. When I installed the ATI driver from their website the graphics became quick and agile (ie dragging windows smoothly) but no effects. So I was fairly happy with this.

Until today. I got some updates today and amongst them some Restricted Modules things. After this update the graphics was back to slow and jerky. Still 1680x1050 but crap performance.

Then I noticed that ATI had released a new version on their website so I tried this one.

No luck.

What in the world would I do now? Feels like I am in some kind of "generic" graphics driver mode but the resolution is right.... I cant figure it out.

---

### Post by soxs on 2007-11-14
@carli: Requests without info are quite useless.. plx add the output of```
 glxinfo|grep direct
``` & ```
fglrxinfo
``` and attach your xorg.conf

@rmfought: may you plx write what did you do that did the job?

---

### Post by leroy_30 on 2007-11-14
Haleleuja! You rock. Compiz finally works for me.

New Xubuntu Gutsy install on Dell E1705 w/ ATI X1400.

---

### Post by Znupi on 2007-11-14
I have created a new thread [here](http://ubuntuforums.org/showthread.php?p=3770176). Can you please have a look at it? Thanks :)

---

### Post by rmfought on 2007-11-14
> **soxs said:**
> 

@rmfought: may you plx write what did you do that did the job?

I followed Michael37's instructions for a fresh install of Gutsy on the first page of this thread.

However, I have discovered that Google Earth is now broken.  DANG!  Always something.  I get the following error:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".

Anybody know how to make Google Earth play nice?

---

### Post by carli on 2007-11-16
Hi!

My glxinfo | grep direct returns:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

My glrxinfo returns

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)

if I have the restricted driver enabled. If I use the ATI driver, fglrxinfo crashes and kills the X server.

---

### Post by Mcavity on 2007-11-16
Ok now I feel silly. but I have found the main problem I was having with Compiz.

I have a ATI radon 9800 with 128 megs of memory. 
I have dual lcd desktop displays that run a a native resolution of 1280x1024
I did the ati driver install and installed the big desktop. 
> 
aticonfig --initial=dual-head --screen-layout=right
aticonfig --dtop=horizontal --overlay-on=1


This gave me a nice big desktop over both my displays. 
For the Life of me I could not get compiz to start. 
I would always get "desktop effects could not be enabled"
Turns out that the maximum texture size for this card is about 2048
however with big desktop enabled at native resolution I needed a texture size of  2560. 
This is what keeps killing compiz. I then set the resolution to 1024x768 on both displays using> 
aticonfig --resolution=0,1024x768 1,1024x768 

Once I did this. Compiz worked!. 
unfortunately It means I cant run my LCD display at native resolution. so things are a little.. soft. but I have wobbly windows!

I hope this helps other people.

---

### Post by soxs on 2007-11-17
@ carli: USE CODE TAGS!

> **carli said:**
> 

My glxinfo | grep direct returns:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```



This means either your driver installation is corrupted so you have to reinstall the drivers,OR (well, I am not 100% shure about it) you did not update your xorg.conf , replacing the "ati" or "radeon" string with "fglrx" (@ the device section).

---

### Post by semakwetu on 2007-11-17
> **rmfought said:**
> 

Anybody know how to make Google Earth play nice?

```
DISPLAY=:0 googleearth
```

from in a terminal.  Is what worked for me though you can only use Googleearth and have no window borders or titlebar

---

### Post by charIie on 2007-11-17
Hey, Not sure what is going on with my upgrade from Feisty to Gusty. Everything went correctly. I followed the guide to make compiz work. All was installed correctly as well. Now, when I reboot and run, not all my applications load. Terminal wont load yet firefox did. It varies as well. If I reboot they both might not work. Folders on the desktop open fine, but folders from the Places menu do not open. Has anyone else experienced this problem?

Compiz also is not running. 

I'm running Gutsy on an Acer Travelmate 4670. 

I also have done a successful upgrade on my desktop computer and have not encountered any problems. 

Any Ideas would be appreciated.

Brian

EDIT: Found out after uninstalling compiz and everything related, that I still get the issue. Now, it is irrelevant to the thread, yet if someone knows why or how to fix please let me know.

---

### Post by carli on 2007-11-18
> **soxs said:**
> @ carli: USE CODE TAGS!



This means either your driver installation is corrupted so you have to reinstall the drivers,OR (well, I am not 100% shure about it) you did not update your xorg.conf , replacing the "ati" or "radeon" string with "fglrx" (@ the device section).

@soxs: I did?!? Dunno why it doesnt show.

I already described that the ATI driver now gives me the same result.. This happened after the Restricted Modules update on last wednesday...

So what you are saying is that my xorg.conf is supposed to read ati or radeon to work?

Ok, I will now try to remove the restricted driver and install the ATI driver again and check the xorg.conf.

---

### Post by soxs on 2007-11-18
would you mind trying envy?

---

### Post by intimaAcE on 2007-11-19
Hey,

I'm running an ATI X1600 on gutsy with the fglrx drivers installed using the restriced drivers manager, and with xserver-xgl installed (else compiz didn't work) but **glxinfo | grep rendering** returns:

```
glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

**fglrxinfo** returns: 


```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6473 (8.37.6)

```

And my **xorg.conf** is 

```
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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:5:0:0"
	Option "DRI" "true"
EndSection

Section "Monitor"
	Identifier	"BenQ 241W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"BenQ 241W"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1920x1200"	"1680x1680"	"1600x1200"	"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

Basically any game I try to run either has the same effect as pushing ctrl+alt+backspace (restarting the X session? I'm a linux newb.), or it runs unplayably slowly, or with texture corruption, or with text corruption. However, compiz works just fine, and smoothly. 

PLEASE help!

---

### Post by rjbgbo on 2007-11-19
I have one ATI Radeon x300, that I obtained to install for following - [http://ubuntuforums.org/showthread.php?t=569654&highlight=x300+gutsy](http://ubuntuforums.org/showthread.php?t=569654&highlight=x300+gutsy) of michael37

It had attemped to install, but without success for Envy with I finish it drive.

In both my screen of login = 1920x1080, and I use 1280x1024 - 60Hz. In the Gutsy this all normal one, also I am having finally Compiz Fusion functioning with drive ATI

I took off the following ones screenshots:

[[IMG]http://img216.imageshack.us/img216/9301/capturadatelachoosescreni8.th.png[/IMG]](http://img216.imageshack.us/my.php?image=capturadatelachoosescreni8.png)

[[IMG]http://img217.imageshack.us/img217/2447/capturadatelascreenandgvx5.th.png[/IMG]](http://img217.imageshack.us/my.php?image=capturadatelascreenandgvx5.png)

My monitor is one  LG Flatron L1750S LCD 17'', considered in the listing as generico. In the second screen it this with 1024x768.

My current one xorg.conf

```
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
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor Genérico"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"Monitor Genérico"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

Screen and Graphics = 1280x1024 - 60Hz. Functioning normal

Thank

---

### Post by carli on 2007-11-21
I have it working on my Mobility X1600 now!!! Sweet stuff!! And fast!

All I did was uninstall ALL driver and utils from the official ATI package.

This accomplished by either running APT and remove fglrx-amdcccle or:

```
you@computer:/$ sudo /usr/share/ati/fglrx-uninstall.sh
```

Then I removed xorg-driver-fglrx and rebooted. My computer went into generic xga mode and I was back to 1400x1050.

Then I simply re-enabled the restricted driver, got a new xorg-driver-fglrx driver package and then I simply went into System-Administration->Screens and Graphics to set the correct resolution.

Then I went back to Gnome from Xgl when logging in and set Gnome to default.

To my surprise the new xorg-driver-fglrx did the trick! I dunno if it is newly released but now my Compiz is super agile in 1680x1050 with HEAVY effects on! :D:D:D:D

---

### Post by petzworld999 on 2007-11-23
Hello. I am running a Compaq Presario V5305WM notebook and am using Gutsy. My video card is an ATI Radeon Xpress 200M. I have compiz and xgl installed and working, but I do not have 3D acceleration. Is there any way to get 3D acceleration with my video card?

---

### Post by mamlouk on 2007-11-23
I'm running Ubuntu Gutsy 64-bit edition. I was able to install the 8.42.3 driver, thanks to Michael and this [site](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide). However, before  I attempted the installation, I had upgraded my kernel to 2.6.23. But in order to install the ATI driver, I had to log on my 2.6.22-14-generic kernel in order to get the Restricted Drivers Manager to work (since it doesn't work in 2.6.23). Now that I installed the driver, got my 3d effects, whenever I log back to my 2.6.23 kernel, I get a blank screen just after I enter my username and password, and it's worth noting that my mouse cursor is the only thing on that screen.

So my question is, what do I do in the 2.6.23 kernel to get it running with the ati driver?

---

### Post by silviur on 2007-11-23
mamluk, use the Adept Manager (system tools) as root and install xgl server (type xgl in the search box, it will show 2 options, choose to install xgl and Apply).
It will work after restart.

From what i understand, the new Ati drivers we have should render the effects without a XGL server, but it seems it doesn't in some cases.

Tell me if it worked.

---

### Post by KingArthur10 on 2007-11-23
> **popophobia said:**
> Hi,
I'm a new user and just install the compiz package as above. However, after installation, Ubuntu seems to lost some of its original setting options (touchpad in particular).
Now I cannot disable tapping... Any ideas how to restore the options? Thanks.

I, too, am having this issue.  Any fixes that don't involve having to do that SMHConfig (or whatever it is called) hack?

---

### Post by mamlouk on 2007-11-24
> **silviur said:**
> Tell me if it worked.
Apparently, there is 3d acceleration without the xgl-server, which I did not install because of [this](http://combatwombat.7doves.com/index.php/2007/10/31/gutsy_effort_in_new_ati_driver). Anyway, I followed your advice, and installed xgl-server, restarted X on my 2.6.22-14 kernel, and everything seemed to be ok, it even fixed an issue I had after enabling compiz, which was that I couldn't watch any videos, and I felt it was a problem with the overlay, and thought I would fix it after running the ATI driver under 2.6.23.

Anyway, loaded my 2.6.23 and it opened. Now, I felt that the graphics are really heavy, and very choppy. Dragging windows or even scrolling down a webpage would give you something like 1 frame per second. So, I logged both Xorg.0.log on both kernels and here is the difference.
```
diff /home/mamlouk/Documents/xorg.2622 /home/mamlouk/Documents/xorg.2623 > /home/mamlouk/Documents/xorg.diff
```
```
6c6
< Current Operating System: Linux mamloukubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
---
> Current Operating System: Linux mamloukubuntu 2.6.23 #1 SMP Wed Nov 7 00:03:26 EET 2007 x86_64
14c14
< (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 24 11:15:56 2007
---
> (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 24 11:32:31 2007
442,453c442,446
< drmOpenDevice: open result is 7, (OK)
< drmOpenDevice: node name is /dev/dri/card0
< drmOpenDevice: open result is 7, (OK)
< drmOpenDevice: node name is /dev/dri/card0
< drmOpenDevice: open result is 7, (OK)
< drmGetBusid returned ''
< (II) Loading sub module "fglrxdrm"
< (II) LoadModule: "fglrxdrm"
< (II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
< (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
< 	compiled for 7.1.0, module version = 8.42.3
< 	ABI class: X.Org Server Extension, version 0.3
---
> drmOpenDevice: open result is -1, (No such device or address)
> drmOpenDevice: open result is -1, (No such device or address)
> drmOpenDevice: Open failed
> [drm] failed to load kernel module "fglrx"
> (WW) fglrx(0): Failed to open DRM connection
734c727,730
< (II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
---
> (II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
> (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
> 	compiled for 7.1.0, module version = 8.42.3
> 	ABI class: X.Org Server Extension, version 0.3
741c737
< (II) fglrx(0): [pcie] 258048 kB allocated with handle 0xdeadbeef
---
> (WW) fglrx(0): No DRM connection for driver fglrx.
794,903c790,799
< (II) Loading extension ATIFGLRXDRI
< (II) fglrx(0): doing DRIScreenInit
< drmOpenDevice: node name is /dev/dri/card0
< drmOpenDevice: open result is 7, (OK)
< drmOpenDevice: node name is /dev/dri/card0
< drmOpenDevice: open result is 7, (OK)
< drmOpenByBusid: Searching for BusID PCI:2:0:0
< drmOpenDevice: node name is /dev/dri/card0
< drmOpenDevice: open result is 7, (OK)
< drmOpenByBusid: drmOpenMinor returns 7
< drmOpenByBusid: drmGetBusid reports 
< drmOpenDevice: node name is /dev/dri/card1
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card2
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card3
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card4
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card5
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card6
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card7
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card8
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card9
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card10
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card11
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card12
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card13
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card14
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: open result is -1, (No such device)
< drmOpenDevice: Open failed
< drmOpenByBusid: drmOpenMinor returns -19
< drmOpenDevice: node name is /dev/dri/card0
< drmOpenDevice: open result is 7, (OK)
< drmOpenDevice: node name is /dev/dri/card0
< drmOpenDevice: open result is 7, (OK)
< drmGetBusid returned ''
< (II) fglrx(0): [drm] DRM interface version 1.0
< (II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
< (II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
< (II) fglrx(0): [drm] mapped SAREA 0x2000 to 0x2afd0f139000
< (II) fglrx(0): [drm] framebuffer handle = 0x3000
< (II) fglrx(0): [drm] added 1 reserved context for kernel
< (II) fglrx(0): DRIScreenInit done
< (II) fglrx(0): Kernel Module Version Information:
< (II) fglrx(0):     Name: fglrx
< (II) fglrx(0):     Version: 8.42.3
< (II) fglrx(0):     Date: Oct 19 2007
< (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
< (II) fglrx(0): Kernel Module version matches driver.
< (II) fglrx(0): Kernel Module Build Time Information:
< (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
< (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
< (II) fglrx(0):     Build-Kernel __SMP__:            no
< (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
< (II) fglrx(0): [drm] register handle = 0x00004000
< (II) fglrx(0): Interrupt handler installed at IRQ 24.
< (II) fglrx(0): Exposed events to the /proc interface
< (II) fglrx(0): DRI initialization successfull!
< (II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x00701c00
< (II) fglrx(0): FBMM initialized for area (0,0)-(1280,1435)
---
> (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
> (WW) fglrx(0): ***********************************************
> (WW) fglrx(0): * DRI initialization failed!                  *
> (WW) fglrx(0): * (maybe driver kernel module missing or bad) *
> (WW) fglrx(0): * 2D acceleraton available (MMIO)             *
> (WW) fglrx(0): * no 3D acceleration available                *
> (WW) fglrx(0): ********************************************* *
> (II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000
> (==) fglrx(0): Write-combining range (0xd0000000,0x8000000)
> (II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
905c801
< (II) fglrx(0): Largest offscreen area available: 1280 x 411
---
> (II) fglrx(0): Largest offscreen area available: 1280 x 7167
913,915c809
< 	8x8 mono pattern filled rectangles
< 	Solid Lines
< 	Dashed Lines
---
> 	Solid Horizontal and Vertical Lines
918c812,814
< 		30 128x128 slots
---
> 		32 128x128 slots
> 		32 256x256 slots
> 		16 512x512 slots
922,925c818
< (II) fglrx(0): X context handle = 0x1
< (II) fglrx(0): [DRI] installation complete
< (II) fglrx(0): Direct rendering enabled
< [atiddx] ASYNCIO init succeed!
---
> (II) fglrx(0): Direct rendering disabled
944,1032c837,844
< drmOpenDevice: node name is /dev/dri/card0
< drmOpenDevice: open result is 8, (OK)
< drmOpenByBusid: Searching for BusID PCI:2:0:0
< drmOpenDevice: node name is /dev/dri/card0
< drmOpenDevice: open result is 8, (OK)
< drmOpenByBusid: drmOpenMinor returns 8
< drmOpenByBusid: drmGetBusid reports PCI:2:0:0
< (WW) AIGLX: 3D driver claims to not support visual 0x23
< (WW) AIGLX: 3D driver claims to not support visual 0x24
< (WW) AIGLX: 3D driver claims to not support visual 0x25
< (WW) AIGLX: 3D driver claims to not support visual 0x26
< (WW) AIGLX: 3D driver claims to not support visual 0x27
< (WW) AIGLX: 3D driver claims to not support visual 0x28
< (WW) AIGLX: 3D driver claims to not support visual 0x29
< (WW) AIGLX: 3D driver claims to not support visual 0x2a
< (WW) AIGLX: 3D driver claims to not support visual 0x2b
< (WW) AIGLX: 3D driver claims to not support visual 0x2c
< (WW) AIGLX: 3D driver claims to not support visual 0x2d
< (WW) AIGLX: 3D driver claims to not support visual 0x2e
< (WW) AIGLX: 3D driver claims to not support visual 0x2f
< (WW) AIGLX: 3D driver claims to not support visual 0x30
< (WW) AIGLX: 3D driver claims to not support visual 0x31
< (WW) AIGLX: 3D driver claims to not support visual 0x32
< (WW) AIGLX: 3D driver claims to not support visual 0x33
< (WW) AIGLX: 3D driver claims to not support visual 0x34
< (WW) AIGLX: 3D driver claims to not support visual 0x35
< (WW) AIGLX: 3D driver claims to not support visual 0x36
< (WW) AIGLX: 3D driver claims to not support visual 0x37
< (WW) AIGLX: 3D driver claims to not support visual 0x38
< (WW) AIGLX: 3D driver claims to not support visual 0x39
< (WW) AIGLX: 3D driver claims to not support visual 0x3a
< (WW) AIGLX: 3D driver claims to not support visual 0x3b
< (WW) AIGLX: 3D driver claims to not support visual 0x3c
< (WW) AIGLX: 3D driver claims to not support visual 0x3d
< (WW) AIGLX: 3D driver claims to not support visual 0x3e
< (WW) AIGLX: 3D driver claims to not support visual 0x3f
< (WW) AIGLX: 3D driver claims to not support visual 0x40
< (WW) AIGLX: 3D driver claims to not support visual 0x41
< (WW) AIGLX: 3D driver claims to not support visual 0x42
< (WW) AIGLX: 3D driver claims to not support visual 0x43
< (WW) AIGLX: 3D driver claims to not support visual 0x44
< (WW) AIGLX: 3D driver claims to not support visual 0x45
< (WW) AIGLX: 3D driver claims to not support visual 0x46
< (WW) AIGLX: 3D driver claims to not support visual 0x47
< (WW) AIGLX: 3D driver claims to not support visual 0x48
< (WW) AIGLX: 3D driver claims to not support visual 0x49
< (WW) AIGLX: 3D driver claims to not support visual 0x4a
< (WW) AIGLX: 3D driver claims to not support visual 0x4b
< (WW) AIGLX: 3D driver claims to not support visual 0x4c
< (WW) AIGLX: 3D driver claims to not support visual 0x4d
< (WW) AIGLX: 3D driver claims to not support visual 0x4e
< (WW) AIGLX: 3D driver claims to not support visual 0x4f
< (WW) AIGLX: 3D driver claims to not support visual 0x50
< (WW) AIGLX: 3D driver claims to not support visual 0x51
< (WW) AIGLX: 3D driver claims to not support visual 0x52
< (WW) AIGLX: 3D driver claims to not support visual 0x53
< (WW) AIGLX: 3D driver claims to not support visual 0x54
< (WW) AIGLX: 3D driver claims to not support visual 0x55
< (WW) AIGLX: 3D driver claims to not support visual 0x56
< (WW) AIGLX: 3D driver claims to not support visual 0x57
< (WW) AIGLX: 3D driver claims to not support visual 0x58
< (WW) AIGLX: 3D driver claims to not support visual 0x59
< (WW) AIGLX: 3D driver claims to not support visual 0x5a
< (WW) AIGLX: 3D driver claims to not support visual 0x5b
< (WW) AIGLX: 3D driver claims to not support visual 0x5c
< (WW) AIGLX: 3D driver claims to not support visual 0x5d
< (WW) AIGLX: 3D driver claims to not support visual 0x5e
< (WW) AIGLX: 3D driver claims to not support visual 0x5f
< (WW) AIGLX: 3D driver claims to not support visual 0x60
< (WW) AIGLX: 3D driver claims to not support visual 0x61
< (WW) AIGLX: 3D driver claims to not support visual 0x62
< (WW) AIGLX: 3D driver claims to not support visual 0x63
< (WW) AIGLX: 3D driver claims to not support visual 0x64
< (WW) AIGLX: 3D driver claims to not support visual 0x65
< (WW) AIGLX: 3D driver claims to not support visual 0x66
< (WW) AIGLX: 3D driver claims to not support visual 0x67
< (WW) AIGLX: 3D driver claims to not support visual 0x68
< (WW) AIGLX: 3D driver claims to not support visual 0x69
< (WW) AIGLX: 3D driver claims to not support visual 0x6a
< (WW) AIGLX: 3D driver claims to not support visual 0x6b
< (WW) AIGLX: 3D driver claims to not support visual 0x6c
< (WW) AIGLX: 3D driver claims to not support visual 0x6d
< (WW) AIGLX: 3D driver claims to not support visual 0x6e
< (WW) AIGLX: 3D driver claims to not support visual 0x6f
< (WW) AIGLX: 3D driver claims to not support visual 0x70
< (WW) AIGLX: 3D driver claims to not support visual 0x71
< (WW) AIGLX: 3D driver claims to not support visual 0x72
< (II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
< (II) GLX: Initialized DRI GL provider for screen 0
---
> (EE) AIGLX: Screen 0 is not DRI capable
> (II) Loading local sub module "GLcore"
> (II) LoadModule: "GLcore"
> (II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
> (II) Module GLcore: vendor="X.Org Foundation"
> 	compiled for 1.3.0, module version = 1.0.0
> 	ABI class: X.Org Server Extension, version 0.3
> (II) GLX: Initialized MESA-PROXY GL provider for screen 0
```
Apparently fglrx failed to open a DRM connection, and hence fglrx didn't load.

Any ideas?

---

### Post by silviur on 2007-11-24
No ideas, sorry, I don't know that much Ubuntu :)
It seems many others have similar problems, so let's wait a few days until, hopefully, we will get an update. Good luck!

---

### Post by chrome101 on 2007-11-24
I had to reinstall Gutsy on a desktop for the home after upgrading compiz. I had exactly the same problem with video and surfing the web was a joke. This time I have the upgrade icon constantly lit, because I refuse to upgrade compiz. I do hope they sort the problem out soon, cause it could affect the good name of ubuntu...

---

### Post by mamlouk on 2007-11-25
> **silviur said:**
> No ideas, sorry, I don't know that much Ubuntu :)
It seems many others have similar problems, so let's wait a few days until, hopefully, we will get an update. Good luck!
It's ok, I just read the release notes for the new [AMD Catalyst™ Linux 7.11](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_711_linux.html), and I quote: ```
The kernel module is now working on kernel version 2.6.23
```
Thanks anyway :)

---

### Post by Juanmanuel on 2007-11-25
Thanks Michael for the great tutorial.
I have just started using Linux a few days ago, so im still getting the hang of it... but thanks to people like all of you this is not gonna be difficult.

\\:D/

---

### Post by jonssoni on 2007-11-26
Okay. First, thanks of the EXCELLENT guide.
Everything works fine until I tried to play Frets On Fire... :guitar:

```
jonsson@jonsson-desktop:~$ fretsonfire
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 155, in __init__
    self.video.setMode((width, height), fullscreen = fullscreen, multisamples = multisamples)
  File "/usr/share/games/fretsonfire/game/Video.py", line 61, in setMode
    self.screen = pygame.display.set_mode(resolution, flags)
pygame.error: No video mode large enough for 1600x1200

```

Compiz works fine and simple games work fine.

```
jonsson@jonsson-desktop:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.0.6473 (8.37.6)

```

```
jonsson@jonsson-desktop:~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 1.2 (2.0.6473 (8.37.6))

```

Can anyone help, what to do next..? :confused:

---

### Post by darolu on 2007-11-26
```

compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

That's what I got after doing a fresh install of gutsy and doing the instructions in the first page of this thread (the fresh install instructions of course), all my system is running really slow now, well the graphics aspect, my keyboard configuration is also bad I have spanish installation and my keyboard is now set to english, any ideas on how to fix it?
BTW I have an ATI Radeon 9550 with 256MB.
Thanks in advance.

---

### Post by bucky100771 on 2007-11-28
Is it just me....I have the effects installed now, but my system perfromance has gone WAAAAAY down.  I have an Acer 5100 with the Radeon X1100.  It is not listed as one of the supported cards, but it does work.....  just everything is very slow.  Does this mean that its not truly supported?  Or is there a fix to the speed problem?

How do I undo this if I want to go back to no 3D effects and higher perfromance?

---

### Post by delphiguy on 2007-11-28
I followed the instruction in this thread to install compiz in Kubuntu 7.10, it did worked, however something weird is happening.

If I startup Kubuntu without running compiz, Kubuntu is just plain sluggish, I mean moving windows and such is very sloooow.  However as soon as I start compiz by typing in the terminal this command:
compiz --replace
Kubuntu then becomes responsive.  That is until I start to watch a video, and it becomes sluggish again.

Any idea what went wrong here?

below is my xorg.conf
```

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
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Generic Video Card"
    Boardname    "ati"
    Busid        "PCI:1:0:0"
    Driver        "fglrx"
    Screen    0
    Option        "VideoOverlay"    "on"
    Option        "OpenGLOverlay"    "off"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x800"
    Horizsync    31.5-50.0
    Vertrefresh    56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    800
        Modes        "1280x800@60"    "1280x720@60"    "1280x768@60"    "800x600@60"    "800x600@56"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
    Inputdevice    "Synaptics Touchpad"
EndSection

Section "Extensions"
    Option        "Composite"    "Enable"
EndSection
Section "Module"
    Load        "glx"
    Load        "dbe"
    Load        "v4l"
EndSection
Section "device" # 
    Identifier    "device1"
    Boardname    "ati"
    Busid        "PCI:1:0:0"
    Driver        "fglrx"
    Screen    1
EndSection
Section "screen" # 
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
EndSection
Section "monitor" # 
    Identifier    "monitor1"
    Gamma    1.0
EndSection
Section "ServerFlags"
EndSection


```


Thanks.

---

### Post by bill516 on 2007-11-28
Terrific work by Michael37.  Over the weekend my grandson, who is a very skilled Linux/Unix programmer visited and he showed me how to activate the compiz-fusion desktop enhancements using the Radeon X1600 card on my laptop.  He did it exactly as Michael outlines in his "fresh install" how-to.  Well done Michael!

Gee, now I can do all sorts of cute, pointless and occasionally helpful things with my Gnome desktop!

---

### Post by Elnath on 2007-12-04
Hi everybody!
I'm looking for a possibility to reset all the rubbish I did while trying to enable 2d and 3d hardware acceleration for my ATI X1650 on Gutsy. Before you start to blame me: Yes, I know that it was me who did everything wrong. ](*,) Yes, I know that it is my fault. ](*,) Yes, I promise to not do it again. ](*,)

I tried envy with different options, the installer from ati with different options and several HowTo's for Feisty - all mixed up. Now it seems that everything regarding graphic drivers, configuration files and file links is messed up.

I tried to use the instructions out of this tread to clean this up and start from beginning. I followed the steps from michael37 #8 two times up to step 10 without success. Now the X server even crashes every time I try to use fglrxinfo.

Does anybody see a chance to fix a system like mine beside reformatting the disc and start over from scratch? :confused:

Thx,

Elnath

---

### Post by X-dark on 2007-12-07
After an unsuccesful try to install latest driver (catalyst 7.11) I've switched back to the one in the repo.
Before that Compiz worked very well.
Now when I try to activate it I get a "Desktop Effects could not be enabled" message.

the driver are well installed :

> cedric@cedric-laptop:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)

cedric@cedric-laptop:~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 1.2 (2.0.6473 (8.37.6))

So I really don't understand the problem.
I've even tried to follow the full guide (update from feisty) but without much differences.

Any help ?

---

### Post by okkie on 2007-12-10
i have spent the past weeks trying to find a solution.the ati radeon 92--------cards are not catered for in gutsy although in feisty there was no problem.doesn't make sense.i and many of us have 9250  ati cards.does anybody know if something is being done to help us or must we replace them?

---

### Post by praxis22 on 2007-12-11
I had the ATI drivers working when gutsy first came out, but after a few upgrades, I started get strange transparency errors. black and white blocks wherever the text was white, text entry boxes and the like. 

I finally tracked this down to a kernel upgrade, once I roiled back the kernel everything worked smoothly again.

I'm in windows at the moment or I'd look up what kernel I'm running, etc.

---

### Post by Mum_Chamber on 2007-12-12
> **michael37 said:**
> Well, let's try here and see if I can help you... If yes, I will create a Wiki page.

[SIZE="7"]Before we begin -- supported hardware list[/SIZE]

*Taken from fglrx driver description for Gutsy.*

This version of the ATI driver officially supports:

 * FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400,
           V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128,
           X1-128, X1-256p
 * FireMV: 2200 (Single card PCI-e configuration)
 * Mobility FireGL: V5000, T2
 * Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300,
                    9800, 9600, 9550, 9500
 * Radeon Xpress: 200M series, 1250 IGP, 200 series
 * Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550,
           X300, 9800, 9700, 9600, 9550, 9500

ATI All-in-Wonder variants of the above cards/chips are also supported,
but video capture is not.

[SIZE="7"]If you are doing fresh install of Gutsy[/SIZE]

[LIST=1]
[*]Enable fgrlx driver.

Install linux-restricted-modules and restricted-manager provied in the restricted repositories:
```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". 

[*]Install xserver-xgl package
```
sudo apt-get install xserver-xgl
```
[*]Install compiz
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
```
[*]Reboot
[*]Log in.  3D effects should be enabled!
[*]Customize Compiz Fusion.
Select System &#8594; Preferences &#8594; Advanced Desktop Effects Settings
In the new window, General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size.  Set it to 4.
The other two options have to be left at 1.

Continue customization per Forlong's guide at [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

[/LIST]

worked for me very smoothly. thanks a lot

---

### Post by FokkerCharlie on 2007-12-12
And worked splendidly for me, too-

thanks!

Charlie

---

### Post by X-dark on 2007-12-12
> **X-dark said:**
> After an unsuccesful try to install latest driver (catalyst 7.11) I've switched back to the one in the repo.
Before that Compiz worked very well.
Now when I try to activate it I get a "Desktop Effects could not be enabled" message.

the driver are well installed :
> cedric@cedric-laptop:~$ fglrxinfo -display :0
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)

cedric@cedric-laptop:~$ fglrxinfo -display :1
Xlib: extension "XFree86-DRI" missing on display ":1.0".
display: :1.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 1.2 (2.0.6473 (8.37.6))


So I really don't understand the problem.
I've even tried to follow the full guide (update from feisty) but without much differences.

Any help ?

Up!

---

### Post by mramsey on 2007-12-12
OK I don't mean to beat a dead horse here, but, I have been running gutsy since the official release and initially it ran pretty good right out of the box.  Then I got Compiz running (Sweet). Then I started messing around with things and hence this post:). 

Initially i noticed some issues with some 3d games that were working fine in feisty. I tried several things to get them to work and that is probably where i went wrong.  I have an ATI X600 256mb graphics card installed, at this point would I be better off reinstalling gutsy or is there a way to correct this mess?

Now I get issues like only the upper left hand corner of my screen if i disable desktop effects. (it's driving me nuts. BTW I also have  a new Nvidia 8600GT 512 MB graphics card on the way...Would I be better off waiting for that?:confused: Sorry to ramble

---

### Post by psywped on 2007-12-15
thanks for the fix worked great

---

### Post by gibby213 on 2007-12-15
(Moved from the guide thread)

Yo, used this guide to get Compiz and xserver-xgl installed on a freshly installed Ubuntu Gutsy dual boot.  Compiz starts up just fine, but everything runs so slow you actually can't see the new effects.  Here is the information I *think* is relevant:

```
$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)

```

(There is no display :1)

xorg.conf:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool,
#using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades
#*only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically
#updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "dri"
	Load  "glx"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
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
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1920x1200"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "enable"
EndSection

```

I just do:
```
$ sudo apt-get install xserver-xgl
$ sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0

```


And reboot.  Any ideas? I've read a lot about it being slow but there aren't any fixes that have worked for me.

EDIT: ATI Mobility Radeon X1600 256MB...Dunno if that makes a difference.

---

### Post by jw5801 on 2007-12-16
hmm... I'm having an interesting problem:
```
jw5801@laptop:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

jw5801@laptop:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```

So it would appear that Xgl is running fglrx as it should be, however Xorg is using the mesa driver. Does anyone have any ideas on how to fix this?

---

### Post by X-dark on 2007-12-19
I get this error :

```

Checking for Xgl: present. 
Checking for nVidia: cedric@cedric-laptop:~$ not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

---

### Post by X-dark on 2007-12-20
OK I've solved my problem.
I've used envy to cleanly uninstall my previous unsuccessful install then I've followed the fresh guide and now it works.

---

### Post by tunalock on 2007-12-20
> **michael37 said:**
> Well, let's try here and see if I can help you... If yes, I will create a Wiki page.

[SIZE="7"]Before we begin -- supported hardware list[/SIZE]

*Taken from fglrx driver description for Gutsy.*

This version of the ATI driver officially supports:

 * FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400,
           V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128,
           X1-128, X1-256p
 * FireMV: 2200 (Single card PCI-e configuration)
 * Mobility FireGL: V5000, T2
 * Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300,
                    9800, 9600, 9550, 9500
 * Radeon Xpress: 200M series, 1250 IGP, 200 series
 * Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550,
           X300, 9800, 9700, 9600, 9550, 9500

ATI All-in-Wonder variants of the above cards/chips are also supported,
but video capture is not.

[SIZE="7"]If you are doing fresh install of Gutsy[/SIZE]

[LIST=1]
[*]Enable fgrlx driver.

Install linux-restricted-modules and restricted-manager provied in the restricted repositories:
```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". 

[*]Install xserver-xgl package
```
sudo apt-get install xserver-xgl
```
[*]Install compiz
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
```
[*]Reboot
[*]Log in.  3D effects should be enabled!
[*]Customize Compiz Fusion.
Select System &#8594; Preferences &#8594; Advanced Desktop Effects Settings
In the new window, General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size.  Set it to 4.
The other two options have to be left at 1.

Continue customization per Forlong's guide at [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

[/LIST]


Have a thinkpad t41 with Radeon 9500 (Mobility?).  I have a new installation of ubuntu gutsy (7.10).  I have unblacklisted via the "SKIP_CHECKS=YES" in the compiz-manager file.  I followed all of these instructions.  I have compiz and all other associated packages installed.  Rebooted, and now when i log in, i just see the beige background which eventually routes me back to the login screen AGAIN!  Thus, I keep getting the login screen no matter what I do.  I'm guessing that the installation of xserver-xgl was the culprit (because I already had the compiz stuff installed).

```
sudo apt-get install xserver-xgl
```

What can I do to diagnose the problem?  I can't even get into my gnome session.  Please help!

Oh, wait wait!  I forgot to mention when I did this:

```
 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". 

I did not see "ATI accelerated graphics driver" in the restricted driver manager.  I'm guessing that's bad.

---

### Post by arno77 on 2007-12-31
Hi! That's a great guide ... but unfortunately it did not work for me!

Did the version "If you are ..." and came up to item "9. Reboot, if necessary".

After reboot I have a black screen and nothing goes any more. Anybody a similar problem?

Can anybody help?

Below is my xorg.conf

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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	Busid		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL SE197FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"DELL SE197FP"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1272x1272"	"1024x768"	"880x704"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
	Option		"Composite"	"0"
EndSection

---

### Post by Chronos6 on 2008-01-05
I would like to play with 3d games, but if i run glxgears X crashes, and having problem with playing videos, and running openoffice. I would really appritiate any help. I've installed the official ati driver, made packages, and enabled the restricted drivers. Everything seems ok, only this Mesa is a misery. Thanx, regards!

chronos@ChronosBase-Ubuntu:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7170 Release

chronos@ChronosBase-Ubuntu:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

---

### Post by BOBSONATOR on 2008-01-05
Guys, i have gutsy fglrx on my Lenovo T60, but i cannot get suspend to work, does anyone here have a fix for it?

---

### Post by angels on 2008-01-15
Hi al, 
I tried to remove compiz as stated below, and now I have many problems:
1. volume control doesn't work anymore-- the error signed is: no volume controller gStreamer plugins and/or devices found. 
2. the windows open on the top left and if I try to fix that with metacity --replace, it works only for that session, after reboot all is the same 
3. and...  I have new restricted driver listed here:
Lucent/Agere linmodem controller driver (which is not in use), but I don't know where it comes from.
Thanks for your answer. I really don't know what should I do, so much mess is now here ... :(
 > # Remove customizations
Code:

rm -rf ~/.compiz
rm -rf ~/.config/compiz
rm -rf ~/.gconf/apps/compiz
sudo rm -i /usr/local/bin/startxgl.sh
sudo rm -i /usr/share/xsessions/xgl.desktop

When asked to remove the files, type YES. If the files were present and you removed them, proceed to the next item. Otherwise, undo customizations to /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom that you have made from this section of the guide
# Reboot
# Login back in and find yourself in a 3D effect devoid session. You may not even be running a windows manager. If you can't move windows and don't see window decorations, press "Alt-F2" and type
Code:

metacity --replace

# Verify that everything else is working properly, e.g. Firefox opens, Wired and/or Wireless Network connects, etc. This is the best time to troubleshoot everything else until we enable 3D effects.
# Enable fgrlx driver.

---

### Post by Raincheque on 2008-01-17
Forgive me for not reading through all the posts, and refer me if you have already answered this:

My problem is that I follow the directions to the letter and nothing changes, but the odd part that I can't figure out is that my /etc/X11/xorg.conf file is completely blank.
How would that have happened? How do I fix it?

I'm using a X1300, and it's listed as supported.

---

### Post by ugm6hr on 2008-01-17
> **Alexander Heß said:**
> AIGLX support is supposed to be included in the 8.42 release which should come this month. That is if they don't screw up their “one release per month” schedule.

Just in case people are still wondering - this is pretty easy now.

Envy will install the latest fglrx driver, and it supports Compiz without xgl (minimal tweaking required).

---

### Post by geirhoe on 2008-01-18
On my system (gutsy on a thinkpad T60 with ATI Mobility Radeon X1400) the fglrx is not loaded:

$lsmod | grep fglrx
$

I have installed the 8.43 ati driver (need suspend).

After investigating, I have found that the module is loaded using lrm-video (from /etc/modprobe.d/lrm-video):

# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
#install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
#install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
#install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS

in /sbin/lrm-video the module is loaded with this command:

modprobe --ignore-install -Qb $@ $MODULE

the -b option is undocumented in the man page, but removing it, makes the module load at boot, and /dev/dri/ is not empty. In this state, suspend fails.

What does the -b option to modprobe mean ?

How can I load the module at boot time and still keep my syspend (the promise of the 8.43 driver)

---

### Post by geirhoe on 2008-01-19
My problem appears to be solved. There was two things I needed to do:

1) remove fglrx from /etc/modprobe.d/blacklist-restricted

2) from [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide:](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide:)

For Thinkpad T60 with ATI X1400, to get the laptop to wake up from suspend, I had to change the following in /etc/default/acpi-support:

SAVE_VBE_STATE=false

POST_VIDEO=false

---

### Post by Aanidaani on 2008-01-23
I followed the steps on the first page, but for some reason I can't get Compiz to work correctly. My rendering is somewhat sluggish and when I try to enable effects in the Appearance manager I get a notice saying the system is unable to enable them.

I have a Radeon X1950 Pro and I'm using the restricted drivers.

Here is the output I get when I execute "Compiz --replace &":

```
steven@steven-desktop:~$ Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

And here is my xorg.conf file:
```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1680"	"1680x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

---

### Post by alamarco on 2008-01-25
Not sure if it makes a difference, but I have my ATi Radeon Xpress 200M working with the "Composite" option set as "0" instead of "Enable". When you run fglrxinfo you should get something like the following:

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)
```

If it says anything about Mesa you should get DRI working first.

---

### Post by Aanidaani on 2008-01-25
Following X-Dark's tip on page 30 worked. I uninstalled my ATI drivers using [Envy]("http://albertomilone.com/nvidia_scripts1.html") and then reinstalled using the fresh install instructions. Worked great.

---

### Post by sunseeker888 on 2008-02-13
> **michael37 said:**
> Well, let's try here and see if I can help you... If yes, I will create a Wiki page.

[SIZE="7"]Before we begin -- supported hardware list[/SIZE]

*Taken from fglrx driver description for Gutsy.*

This version of the ATI driver officially supports:

 * FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400,
           V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128,
           X1-128, X1-256p
 * FireMV: 2200 (Single card PCI-e configuration)
 * Mobility FireGL: V5000, T2
 * Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300,
                    9800, 9600, 9550, 9500
 * Radeon Xpress: 200M series, 1250 IGP, 200 series
 * Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550,
           X300, 9800, 9700, 9600, 9550, 9500

ATI All-in-Wonder variants of the above cards/chips are also supported,
but video capture is not.

[SIZE="7"]If you are doing fresh install of Gutsy[/SIZE]

[LIST=1]
[*]Enable fgrlx driver.

Install linux-restricted-modules and restricted-manager provied in the restricted repositories:
```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". 

[*]Install xserver-xgl package
```
sudo apt-get install xserver-xgl
```
[*]Install compiz
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
```
[*]Reboot
[*]Log in.  3D effects should be enabled!
[*]Customize Compiz Fusion.
Select System &#8594; Preferences &#8594; Advanced Desktop Effects Settings
In the new window, General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size.  Set it to 4.
The other two options have to be left at 1.

Continue customization per Forlong's guide at [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

[/LIST]






HI GUys

I am a newbie

This ati card is doing my nuts in.

what I have done

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager


ok


then


Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver".



The restricted drivers get download and installed (not linux-restricteded ones)


and I getting blank screen again, try a few times same things. According to micheal if I click on ATI accelerated graphics driver tab, he does not say to download the drivers. I thhoght, you click on it Ati accelerator driver, it would used the linux drivers? fglrx


what am i doing wrong ? Please help, I am a complete beginner:(


HOw can I force it to select the linux restricted one before?




By the way, I am using Ubuntu 64 bits with 4GB ram, quad core phenom 9500, does that matter?

---

### Post by nosushi4you on 2008-02-13
Is there a way to get my Radeon 7000 card to enable desktop effects? I think it should support it. Whenever I try to enable them, it loads for a second and says "Can not enable desktop effects".

---

### Post by sunseeker888 on 2008-02-13
> **nosushi4you said:**
> Is there a way to get my Radeon 7000 card to enable desktop effects? I think it should support it. Whenever I try to enable them, it loads for a second and says "Can not enable desktop effects".

Maybe this is you, enabling extras, unfortunately for me, the thing keep loading mesa, I have tried everything. When it goes blank, i can't get back in, evn witn ctrl + alt + F2.

[http://beans.seartipy.com/2007/10/30/finally-got-3d-desktop-effects-in-my-ubuntu-gutsy-ati-hardware/](http://beans.seartipy.com/2007/10/30/finally-got-3d-desktop-effects-in-my-ubuntu-gutsy-ati-hardware/)

---

### Post by bixejo on 2008-03-02
> **nosushi4you said:**
> Is there a way to get my Radeon 7000 card to enable desktop effects? I think it should support it. Whenever I try to enable them, it loads for a second and says "Can not enable desktop effects".

Have a look at [[COLOR="Navy"]_this thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=674803") and in particular to two post of [_[COLOR="Navy"]Temüjin[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=4202892#poststop") and [[COLOR="Navy"]_myself_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4431041#poststop").

---

### Post by Fire69 on 2008-04-08
I reinstalled Gutsy today because I couldn't get the Ati-drivers working properly.
So this time, I didn't use the restricted drivers from Ubuntu first, but immediately after the install, I used those from the Ati-site.  That was beter, the drivers seemed to be working OK.
I wanted to enable the wobly windows, but got the "Desktop Effects can't be enabled".
So I installed XGL, no problems, everything was wobbly again :)
But... now when I started XBMC, it crashed and sent me back to the login-screen :(

I checked fglrxinfo and guess what...

> fire69@Krycek:~$ fglrxinfo
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

And now for the really confusing part:

> fire69@Krycek:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.1.7412 Release

> fire69@Krycek:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

How the hell did I manage to do that!? :confused:
How can I get rid of the display 1:0 and use 0:0??

Xorg.conf
> 
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


---

### Post by Fire69 on 2008-04-09
Anybody? :confused:

What's the difference between display :0.0 and display :1.0??

I only have my laptop-screen, no dual-screen setup.

I checked my xorg.0.log-file, fglrx-module is loaded and used, why do I still have the mesa-drivers when checking fglrxinfo??

---

### Post by RavanH on 2008-04-15
> **Fire69 said:**
> Anybody? :confused:

What's the difference between display :0.0 and display :1.0??

I only have my laptop-screen, no dual-screen setup.

I checked my xorg.0.log-file, fglrx-module is loaded and used, why do I still have the mesa-drivers when checking fglrxinfo??

Can't answer you on these questions (sorry) but I have one thought for you: Why do you use XGL when the latest ATI drivers finally support AIGLX ? 

For that you will need in your xorg.conf the following  entries.
Under Section "Extensions" ```
Option	    "Composite" "Enable"
``` And under Section "ServerLayout" ```
Option	    "AIGLX" "on"
```

Uninstalling XGL and following one of the How-to's on ATI driver installation worked fine for me. I remember using [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0) which also has a 'More Troubleshooting' section that might be helpful to you. Have you tried: ```
$ depmod -ae
``` ?

Nice speed improvement, 3D and with some tinkering (Xv) even good video playback on AMD64...

Only downside to the ATI drivers is that now my Suspend/Hibernation is busted :(

Anyway, hope you can work it out :)

---

### Post by RavanH on 2008-04-15
> **Fire69 said:**
> ... How the hell did I manage to do that!? :confused:
How can I get rid of the display 1:0 and use 0:0??

Xorg.conf

What does it say in the **Section "ServerLayout"** of your xorg.conf ? I think it should be like ```
screen 0 "aticonfig-Screen[0]" 0 0
``` (note that there is that aticonfig-Screen[0] refference as well as these 0's !)

---

