---
title: "How to make Xubuntu 14.04 look and feel more like Ubuntu"
date: 2014-09-16
forum: Desktop Environments
---

### Post by Emblem Parade on 2014-09-16
I happen to really like Ubuntu's default look for Unity. Too bad Unity has too many usability flaws for me to make it my main desktop. Happily, Xubuntu is a great derivative, that indeed does everything I need. But it's a bit too raw out of the box. In this guide, I'll show you how I made my Xubuntu look and feel as beautiful and as smooth as Ubuntu.

[IMG]http://i.imgur.com/uBOZlWt.jpg[/IMG]

We'll be using the [Ambiance and Radiance Colors]("http://www.ravefinity.com/p/ambiance-radiance-colors-suite.html") theme, the [Faenza icons]("http://tiheum.deviantart.com/art/Faenza-Icons-173323228"), [DockbarX]("https://github.com/M7S/dockbarx") (with Xfce panel plugin), and [Compton]("https://github.com/chjj/compton") as our compositor.

**EXTRA AND UPDATED PACKAGES**
```
sudo add-apt-repository -y ppa:ravefinity-project/ppa
sudo add-apt-repository -y ppa:tiheum/equinox
sudo add-apt-repository -y ppa:nilarimogard/webupd8
sudo add-apt-repository -y ppa:richardgv/compton
sudo add-apt-repository -y ppa:gottcode/gcppa
sudo apt update
sudo apt install ambiance-colors radiance-colors faenza-icon-theme xfce4-dockbarx-plugin dockbarx-themes-extra compton
```

**SETTINGS**

***Appearance***

Style: "Ambiance-XFCE-LXDE-Orange"
Icons: "Faenza-Dark"
Fonts:
Default Font: "Ubuntu 12"

***Window Manager***

Style:
Theme: "Ambiance-XFCE-LXDE-Orange"
Title font: "Ubuntu Medium 11"
Button layout: "X _ [] Title"

***Window Manager Tweaks***

Compositor: *disable* "Enable display compositing" (we'll be using Compton instead)

***Panel***

Appearance:
Background:
Style: Solid color
Alpha: 60
Color: #4E4E4E

Items:

Remove "Window Button" and replace it with "DockbarX".

Double click on Whisker Menu
Icon:
Select icon from "Image Files", and then select the file you [download from here]("http://design.ubuntu.com/wp-content/uploads/logo-ubuntu_cof-orange-hex.svg")

Double click on DockbarX
Solid color
Color: #4E4E4E
Alpha: 60

You can configure DockbarX by running the "DockbarX Preference" application. The theme I like is "Brit", with the window list style "Deep".

***Session and Startup***

Application Autostart

Add:
Name: "Compton"
Description: "Compositor"
Command: "/usr/bin/compton -b"

**COMPTON**

We'll need to create a configuration file for it. You can use mine! Run Mousepad, and paste this:

```
# See: http://ubuntuforums.org/showthread.php?t=2144468

# Backend
# See: https://github.com/chjj/compton/wiki/perf-guide
backend = "glx";
glx-no-stencil = true;
glx-no-rebind-pixmap = true;
#glx-use-copysubbuffermesa = true; # may have negative effects on vsync
paint-on-overlay = true;
unredir-if-possible = true; # may fix some fullscreen apps

# Vsync
# See https://github.com/chjj/compton/wiki/vsync-guide
vsync = "opengl-swc";

# Shadow
shadow = true;
shadow-radius = 4; # the blur radius (default 12)
shadow-offset-x = -5; # the left offset (default -15)
shadow-offset-y = -5; # the top offset (default -15)
clear-shadow = true; # might help with irregularly shaped windows
no-dock-shadow = true;
no-dnd-shadow = true;
shadow-exclude = [
  "n:e:Notification",
  "n:e:Docky",
  "g:e:Synapse",
  "g:e:Conky",
  "n:w:*Firefox*",
  "n:w:*Chromium*",
  "n:w:*dockbarx*",
  "class_g ?= 'Cairo-dock'",
  "class_g ?= 'Xfce4-notifyd'",
  "class_g ?= 'Xfce4-power-manager'"
];

# Opacity
detect-client-opacity = true;

# Fading
fading = true;
fade-delta = 3; # the time between steps in a fade in milliseconds (default 10).
fade-in-step = 0.03; # opacity change between steps while fading in (default 0.028).
fade-out-step = 0.03; # oppacity change between steps while fading out (default 0.03).
#no-fading-openclose = true; # Fade windows in/out when opening/closing

# Window type settings
wintypes:
{
  tooltip = { fade = true; shadow = false; };
};
```

Save the file as ".compton.conf" (note the first ".") in your home folder.

**TERMINAL**

Run "Terminal Emulator". Right click, and choose "Preferences".

Appearance
Font: "Ubuntu Mono 13"
Background: "Transparent background", transparency: 0.90

Colors
Presets: Tango
Background color: #320927 (you need to set this again every time you load a preset!)

**YAY!**

Logout, login again, and everything should be awesome. :)

---

### Post by ibjsb4 on 2014-09-18
I am going to try your compton script when I get some time.

---

