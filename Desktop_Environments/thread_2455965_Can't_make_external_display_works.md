---
title: "Can't make external display works"
date: 2020-12-31
forum: Desktop Environments
---

### Post by dbehterev on 2020-12-31
Hello everyone. I have laptop Asus G14 that has GTX2060 on board and AMD graphics and two external displays connected. After upgrading Ubuntu 20.04 kernel from 5.7 to 5.10.4 I got a problem that display connected to the NVidia GPU doesn't work. The display that connected to the AMD graphics works as expected.
I installed nvidia-driver-455 using Additional Drivers applet and after generating xorg.conf file the second display begin works seamlessly but other two (laptop's built-in display and the first display don't work). Now I renamed xorg.conf file, so only one external display that connected to AMD and built-in display are working. 
As I understood, all config files located in /usr/share/X11/xorg.conf.d, but when xorg.conf file takes place all other config files are ignoring. So, my question: is it possible to force system to switch on the second external display? 
PS. Built-in "desktop settings" in OS show me in list my second external display, but it switched off and when I try to switch it on nothing happens. 
xrandr:
```

Screen 0: minimum 320 x 200, current 6400 x 1440, maximum 16384 x 16384
eDP connected 1920x1080+4480+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1920x1080    120.00*+  60.00  
   1680x1050    120.00  
   1280x1024    120.00  
   1440x900     120.00  
   1280x800     120.00  
   1280x720     120.00  
   1024x768     120.00  
   800x600      120.00  
   640x480      120.00  
HDMI-A-0 connected primary 2560x1440+1920+0 (normal left inverted right x axis y axis) 725mm x 428mm
   2560x1440     59.95*+  74.97  
   1920x1200     59.95  
   1920x1080     60.00    50.00    59.94  
   1600x1200     59.95  
   1280x1440     59.91  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x800      59.95  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
DP-1-0 connected
   1920x1080     60.00 +  59.94    50.00  
   1600x1200     60.00  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.93    59.94  
DP-1-1 disconnected
  1920x1080 (0x63) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1920x1080 (0x64) 148.500MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  56.25KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  50.00Hz
  1280x1024 (0x69) 135.000MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock  79.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  75.02Hz
  1280x1024 (0x6a) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x720 (0x6e) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1280x720 (0x6f) 74.250MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock  37.50KHz
        v: height  720 start  725 end  730 total  750           clock  50.00Hz
  1024x768 (0x71) 78.750MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.02KHz
        v: height  768 start  769 end  772 total  800           clock  75.03Hz
  1024x768 (0x73) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x76) 49.500MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
        v: height  600 start  601 end  604 total  625           clock  75.00Hz
  800x600 (0x77) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  720x576 (0x79) 27.000MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock  31.25KHz
        v: height  576 start  581 end  586 total  625           clock  50.00Hz
  720x480 (0x7b) 27.000MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
        v: height  480 start  489 end  495 total  525           clock  59.94Hz
  640x480 (0x7c) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
        v: height  480 start  481 end  484 total  500           clock  75.00Hz
  640x480 (0x80) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz

```
xrandr --listmonitors
```

Monitors: 2
 0: +*HDMI-A-0 2560/725x1440/428+1920+0  HDMI-A-0
 1: +eDP 1920/309x1080/174+4480+0  eDP

```
Thanks in advance for any help.

---

### Post by dino99 on 2021-01-01
if kernel 5.7 is working but not 5.10, then the problem is with 5.10 kernel not supporting mixed gpus

---

### Post by dbehterev on 2021-01-02
no,  being used 5.7 Kernel I spent ton of hours making 2 external displays connected to different GPU working together. As I've said with xorg.conf external display connected to the GTX2060 is working as expected but other two (another external display connected to the AMD built-in GPU and laptop's display) didn't work. 
My xorg.conf file with which my external display connected to the GTX2060 works:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
I renamed this original config file and so took place this config files in /usr/share/X11/xorg.conf.d/ folder (with which two other displays work):
10-amdgpu.conf:
```

Section "OutputClass"
    Identifier "AMDgpu"
    MatchDriver "amdgpu"
    Driver "amdgpu"
    Option "PrimaryGPU" "no"
EndSection

```
10-radeon.conf:
```

Section "OutputClass"
        Identifier "Radeon"
        MatchDriver "radeon"
        Driver "radeon"
EndSection

```
10-nvidia.conf
```

Section "OutputClass"
    Identifier "nvidia"
    MatchDriver "nvidia-drm"
    Driver "nvidia"
    Option "AllowEmptyInitialConfiguration"
    ModulePath "/usr/lib/x86_64-linux-gnu/nvidia/xorg"
EndSection

```
With latter my external display connected to the 2060RTX shows in list of displays in Display Settings but it has off state and when I try to switch it on nothing happens.
So my question: Is it possible to somehow construct new xorg.conf file using current configuration (where 2 displays are working) and mix it with section xorg.conf where another external display also working (connected to the GPU 2060 RTX)?
If anybody experienced the same issue could you give me hint how you fixed it? Or may be it would better to rollback to Noveaue driver where also possible to make working the second display (it seems that on Kernel 5.7 it was a salvation)?
P.S. There were 2 reasons why I upgraded kernel to new:
* I periodically got green screen with no possibility to fix it, only hard reset. It could point on hardware problem but in Windows no any problems when gaming and blue death screens. 
* The system always was under heavy load. Gnome consumed 100% CPU and other application consumes all CPU resources.

---

### Post by dino99 on 2021-01-02
Did 'journalctl -b' expose some usefull errors (red lines) ?

---

