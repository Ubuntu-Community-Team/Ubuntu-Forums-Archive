---
title: "GTK, Compiz, emerald, what are all these?"
date: 2009-04-13
forum: General Help
---

### Post by u.2 on 2009-04-13
Hi,
I am a bit confused when looking for themes I am getting lost installing them.
I was wondering if someone could tell me what the difference in them is in regards to some being GTK, Emerald, Compiz, Beryl, etc.

I am using Jaunty.

---

### Post by RedSingularity on 2009-04-13
They are theme decorators.  Compiz does all sorts of things though.  Compiz makes your desktop look real nice.  Emerald is a windows decorator.  It allows you to change the way your windows looks.  For example you can use it to get rid of that horrid orange bar at the top of every window and turn it into something colorful.  Themes can be found at [www.gnome-look.org](www.gnome-look.org)

---

### Post by lovinglinux on 2009-04-13
Start with *GTK 2.x*. This is were you will find themes for gnome.
[I]
Metacity[/I] is the default windows decorator, the thingy that put borders around application windows. So these themes basically change the shape and the color of borders.

*Beryl* (Emerald) is another windows decorator, with more fancy features. You must have Emerald installed to use these themes.

*GDM Themes* stands for Gnome Display Manager, which is basically the login screen window. So GDM themes changes the looks of the login screen.

*Colour Schemes* - When you change a theme, you can get different buttons, scrollbars etc, but this would change only the colors of any theme.

*Splash Screens* is a term used to describe an image that appears while a computer program is loading.

*Compiz*: is the thingy responsible for the fancy cube and other effects. I'm not sure exactly why there is this category, because it seems that there themes for Emerald, MyGtk2R and other stuff.

*Desklets, Screenlets, XMMS Themes, MPlayer Themes, Xine Themes, VLC Themes, GnoMenu Themes, Cairo-Clock Themes* are application specific themes.
*Screenshots, Fonts, Cliparts, Icons *: self-explanatory
*Systemsounds*: self-explanatory
*X11 Mouse Theme*s: self-explanatory
*Screensavers*: self-explanatory
*Nautilus Scripts:* add-ons for Nautilus file manager

---

### Post by u.2 on 2009-04-13
great, thx!  I am trying to use compiz, but got this error when running the compiz --replace command?

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by juancarlospaco on 2009-04-13
You dont have 3D Hardware Aceleration...

---

### Post by u.2 on 2009-04-14
OK, so does that mean I can't use compiz or just can't use the 3d window option?

---

### Post by u.2 on 2009-04-15
I ran quite a few commands and it appears as though my integrated card does have 3d capabilities.  I tried the other day to run compiz and was getting some errors.

How can I confirm that compiz + emerald will work OK?  I ran the tests I was sent.

Here are the specs of the card, thank you very much for your help!

Direct 3 rendering
direct rendering: Yes

Video card info:
glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

gtxgears
349 frames in 5.0 seconds = 869.684 FPS
4630 frames in 5.0 seconds = 925.810 FPS
4688 frames in 5.0 seconds = 937.578 FPS
4625 frames in 5.0 seconds = 924.895 FPS
4489 frames in 5.0 seconds = 897.790 FPS
4701 frames in 5.0 seconds = 940.147 FPS
4480 frames in 5.0 seconds = 895.818 FPS
4504 frames in 5.0 seconds = 900.633 FPS

xrandr
Screen 0: minimum 320 x 200, current 2720 x 900, maximum 2720 x 900
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
1280x800 60.0*+
1024x768 85.0 75.0 70.1 60.0
832x624 74.6
800x600 85.1 72.2 75.0 60.3 56.2
640x480 85.0 72.8 75.0 59.9
720x400 85.0
640x400 85.1
640x350 85.1
TMDS-1 connected 1440x900+1280+0 (normal left inverted right x axis y axis) 410mm x 256mm
1440x900 59.9*+ 59.9
1152x864 75.0
1024x768 85.0 75.0 70.1 60.0
832x624 74.6
800x600 85.1 72.2 75.0 60.3 56.2
640x480 85.0 75.0 72.8 66.7 59.9
720x400 70.1
TV disconnected (normal left inverted right x axis y axis)

---

