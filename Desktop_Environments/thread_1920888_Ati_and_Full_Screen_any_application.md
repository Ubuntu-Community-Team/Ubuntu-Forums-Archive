---
title: "Ati and Full Screen any application"
date: 2012-02-05
forum: Desktop Environments
---

### Post by madzombie on 2012-02-05
I installed ati driver from ati web site. I use dual monitor. One is default laptop monitor. Other is external LCD monitor. However, I can't run application as full screen if, I run application as full screen. One part of application was showing on external monitor, one was showing on default laptop monitor. my xorg conf file is ;

```
 Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
#   Option         "Xinerama" "on"
    Option         "Clone" "off"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option      "VendorName" "ATI Proprietary Driver"
    Option      "ModelName" "Generic Autodetecting Monitor"
    Option      "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option      "VendorName" "ATI Proprietary Driver"
    Option      "ModelName" "Generic Autodetecting Monitor"
    Option      "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option      "TexturedVideoSync" "on"
    BusID       "PCI:1:0:0"
EndSection


Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    Option      "TexturedVideoSync" "on"
    BusID       "PCI:1:0:0"
EndSection


Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes   "1366x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes   "1920x1080"
    EndSubSection
EndSection
```



How can solve this problem ? Because, I can't run any application (browser, ...) as full screen. screenshot :

[http://imageshack.us/f/850/screenshotat20120205145.png/](http://imageshack.us/f/850/screenshotat20120205145.png/)

---

### Post by mustangkr500 on 2012-02-05
Have you detected both the displays and set up dual monitor mode?

---

### Post by madzombie on 2012-02-06
How can i detect ?
xrandr -q output ;

```
Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 8192 x 8192
LVDS1 connected 1366x768+1920+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080      59.9*+
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1280x960       75.0  
   1152x864       75.0     60.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

```

---

