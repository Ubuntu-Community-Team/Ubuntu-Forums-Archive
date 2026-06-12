---
title: "A few small CF and Emerald questions"
date: 2007-08-30
forum: Desktop Effects &amp; Customization
---

### Post by gimmic on 2007-08-30
I recently finally managed to get CF running properly.
I'm using compiz 5.5 w/ Emerald on feisty

It's currently running in indirect rendering and when I try to switch to direct rendering I lose compiz, it seems to have issues with black windows randomly and all decorations / functionality disappears.

1. Is it possible to run in direct render mode?
2. What is the "loose binding" option?

3. I am running the fusion-icon and for the life of me can't find where emerald puts the 'tray' icons at for the current theme being used. The Fusion-icon's icon(dept of redundancy dept!) is missing so from what I've read I need to copy it into my theme's dir. Anyone know the usual path for that sort of icon in emerald?

Here's some output that might help on the Direct rendering question:

egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10:
Section "Device"
    Identifier     "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"


glxinfo:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

sudo dpkg -l | egrep "decor|compiz":
ii  compiz                                     0.5.5~git20070828+3v1ubuntu0               OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070828+3v1ubuntu0               OpenGL window and compositing manager
ii  compiz-dev                                 0.5.5~git20070828+3v1ubuntu0               OpenGL window and compositing manager - deve
rc  compiz-extra                               0.3.6.1-0ubuntu2                           extra third party plugins for compiz
ii  compiz-fusion-plugins-extra                0.5.2~git20070828+3v1ubuntu0               Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-main                 0.5.2~git20070828+3v1ubuntu0               Collection of Compiz Fusion plugins for Comp
ii  compiz-gnome                               0.5.5~git20070828+3v1ubuntu0               OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                            OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.5~git20070828+3v1ubuntu0               OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2~git20070827+3v1ubuntu0               Plugin and configuration tool - Compiz Fusio
rc  gnome-compiz-manager                       0.10.3-0ubuntu1                            Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2~git20070821+3v1ubuntu0               GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2~git20070829+3v1ubuntu0               Settings library for plugins - Compiz Fusion
ii  libdecoration0                             0.5.5~git20070828+3v1ubuntu0               Compiz window decoration library
rc  libgnome-compiz-manager0                   0.10.3-0ubuntu1                            Compiz Gnome Manager
ii  python-compizconfig                        0.5.2~git20070824+3v1ubuntu0               Python bindings for the Compiz Configuration


I've done my best to search but have not come up with much. Help is appreciated!

---

