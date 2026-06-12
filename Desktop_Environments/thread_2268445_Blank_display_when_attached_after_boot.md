---
title: "Blank display when attached after boot"
date: 2015-03-09
forum: Desktop Environments
---

### Post by jonathan74 on 2015-03-09
Hi all,

I'm using Lubuntu as the base for a digital signage platform. The problem I'm having is with being able to attach a display after the system has already booted. The display remains blank. I've spent a few hours trying to figure this out, and I'm wondering if anyone has some ideas.

OS: Lubuntu 14.04
Displays: Dell U2711 (27" LCD) and a standard LG 32" TV both give the same result
Hardware: Intel Atom NUC DE3815TYKHE, connected to the screen via HDMI. I've configured the BIOS to always use HDMI.

The system works fine as long as the display is plugged in turned on at startup.

I've tried configuring the display with gtf and xrandr with no success. I can control it if it's been plugged in at startup, but not otherwise:

```
if [ ! -t 0 ] 
then
    gtf 1920 1080 60
    xrandr --newmode Manual1 172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
    xrandr --addmode HDMI1 Manual1
    xrandr --output HDMI1 --mode Manual1
fi

```

Here is the output of xrandr when the display is plugged in. This same output also appears once the display has been plugged in, after being unplugged on startup.

```

user@hostname:~$ DISPLAY=:0 xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080      60.0*+   50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1920x1080i     60.1     50.0     60.0  
   1280x1024      60.0  
   1360x768       60.0  
   1152x864       60.0  
   1280x720       59.8     60.0     50.0     59.9  
   1440x576i      50.1  
   1024x768       60.0  
   800x600        60.3  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        60.0     59.9     59.9  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

Can anyone shed some light on how to always supply a signal for HDMI1 even if the display is not plugged in?

Thanks in advance.

---

### Post by jonathan74 on 2015-03-25
Bump.

---

