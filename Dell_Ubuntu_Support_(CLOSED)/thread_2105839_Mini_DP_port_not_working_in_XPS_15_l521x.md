---
title: "Mini DP port not working in XPS 15 l521x"
date: 2013-01-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kappolo on 2013-01-17
Hi everyone,

I've installed Ubuntu 12.10 in my XPS 15 l521x. I had some issues (i.e. HidPoint is quite unstable for my Logitech wireless mouse/keyboard and works pretty randomly), but now the big one that is stopping me is that I'm unable to make my Mini Display-Port working.
I have a Mini DP to VGA (branded Apple) connected to an external monitor. The monitor is working and recognized in Windows 8, but there's no way I can make it work through Ubuntu (it doesn't even detect the display).

```
$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080      60.0*+   59.9     40.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

$ lspci | grep -i VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 640M] (rev ff)

```

Honestly I'm running out of ideas and this functionality is necessary for me. Do you have any suggestion\advice that I can follow?

Thanks!

---

### Post by steffd19 on 2013-02-13
I searched for a long time so I share the solution for XPS 15 l521x with Ubuntu 12.10 :

Don't install Bumblebee otherwise uninstall it.

If the file /etc/X11/xorg.conf doesn't exist, create it and copy/paste :

```
Section "Device"
    Identifier "Device0"
    Driver "intel"
    BusID "PCI:00:02:0"
EndSection


Section "Device"
    Identifier "Device1"
    Driver "nvidia"
    BusID "PCI:01:00:0"
EndSection

Section "Monitor"
   Identifier  "Monitor0"
   HorizSync   30-94
   VertRefresh 48-85
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Screen"

   Identifier  "Screen0"
   Device      "Device0"
   Monitor     "Monitor0"
   DefaultDepth    24
   SubSection "Display"
       Depth       24
       Modes       "1920x1080"
   EndSubSection

   Option         "TwinView" "true"
   Option         "MetaModes" "1280x1024, 1280x1024; 1024x768, 1024x768"
   Option         "SecondMonitorHorizSync" "30-83"
   Option         "SecondMonitorVertRefresh" "56-75"
   Option         "TwinViewOrientation" "RightOf"

EndSection

Section "Screen"
   Identifier  "Screen1"
   Device      "Device1"
   Monitor     "Monitor1"
   DefaultDepth    24
   SubSection "Display"
       Depth       24
       Modes       "1920x1080"
   EndSubSection
EndSection


Section "ServerLayout"
    Identifier  "Default Layout"
    Screen  0   "Screen0" 
    Screen  1   "Screen1" RightOf "Screen0"
    Option      "Clone" "on"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection
```Do CTRL + ALT + F1 then enter :

```
sudo service lightdm restart
```Warning :  if an error is made in the / etc/X11/xorg.conf file -> startup = crash !

But on mine,  it works :)

---

