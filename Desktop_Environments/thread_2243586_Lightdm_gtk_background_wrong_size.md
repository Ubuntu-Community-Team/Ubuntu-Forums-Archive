---
title: "Lightdm gtk background wrong size"
date: 2014-09-09
forum: Desktop Environments
---

### Post by groverj3 on 2014-09-09
Hello all,

I've tinkered with linux for a while now, but I'm in no way a superuser! I've built a new PC and I'm dual booting with windows 8, and I have almost everything working well. The last thing I need to mess with is really more just a slight annoyance than anything else, but at the login screen the background is only filling up part of the desktop. I'm running dual monitors, one of which is 1920x1080 and the other is 1366x768, and it appears the the background is the right size for the smaller monitor and sitting in the top right corner of the desktop leaving the unused portion of the screen to have a plain black background. The actual screen resolution is correct on both monitors, however. I was wondering if there's something I can tweak in my lightdm-gtk-greeter.conf, so here are the contents of the file:

```
#
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# icon-theme-name = Icon theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (none, slight, medium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
# show-indicators = semi-colon ";" separated list of allowed indicator modules. Built-in indicators include "~a11y", "~language", "~session", "~power". Unity indicators can be represented by short name (e.g. "sound", "power"), service file name, or absolute path
# show-clock (true or false)
# clock-format = strftime-format string, e.g. %H:%M
# keyboard = command to launch on-screen keyboard
# position = main window position: x y
# default-user-image = Image used as default user icon, path or #icon-name
# screensaver-timeout = Timeout (in seconds) until the screen blanks when the greeter is called as lockscreen
# 
[greeter]
background=/lib/plymouth/themes/xubuntu-logo/wallpaper.png
theme-name=Greybird
icon-theme-name=elementary-xfce-dark
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-indicators=power;~session;~language;~a11y;~power;
show-clock=true
clock-format=%d %b, %H:%M
keyboard=onboard
```

If it makes any difference, I am using a Geforce GTX 750 and my main monitor is hooked up via HDMI, the secondary monitor is through just an old-fashioned VGA cable with a DVI adapter.

Thanks!

---

### Post by ihoe3fze on 2014-09-10
Described issue has been fixed in latest greeter version - 1.9.0.
Use daily  PPA to install it: [https://launchpad.net/~lightdm-gtk-greeter-team/+archive/ubuntu/daily](https://launchpad.net/~lightdm-gtk-greeter-team/+archive/ubuntu/daily)

You may need some additional steps to configure greeter. So, questions:

1. Ubuntu version.
2. You say that resolution is correct, do you see greeter window on both monitors (what displays layout used - "mirror" or "separate monitors")?
3. Output of "xrandr -q" command.

---

### Post by groverj3 on 2014-09-11
Oh, of course. That information would certainly be helpful.

1. Xubuntu 14.04
2. The displays are not mirrored. 
3. ```
Screen 0: minimum 8 x 8, current 3286 x 1080, maximum 16384 x 16384DVI-I-0 connected 1366x768+1920+0 (normal left inverted right x axis y axis) 410mm x 230mm
   1366x768       59.8*+
   1280x800       59.8  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+   60.0     59.9     50.0     60.1     60.0     50.0  
   1680x1050      60.0  
   1600x1200      60.0  
   1440x900       59.9  
   1366x768       59.8  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x720       60.0     59.9     50.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        75.0     72.8     59.9     59.9  
DP-1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by ihoe3fze on 2014-09-11
> **groverj3 said:**
> 
2. The displays are not mirrored.

It must be enough in this case to update greeter from proposed PPA. Just report results (this version is **not stable**).

---

### Post by groverj3 on 2014-09-12
Finally got around to doing this.

Installing from the daily PPA fixed the issue with no additional configuration required. Thanks for the help!

---

