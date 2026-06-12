---
title: "MUltiples Monitors Config on Kali and Ubuntu"
date: 2018-10-25
forum: Desktop Environments
---

### Post by black-rincon on 2018-10-25
Hello,
I've been trying to solve that issue but I keep failing.
(I'm working on a Dell xps 8900. Nvidia GTX 745 video card. I'&#7743; using 2 HDMI monitors and one VGA, but only one HDMI works)

The normal output of the "xrandr -q" is:
[COLOR=#ff0000]
# xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1600 x 900, maximum 1600 x 900
default connected primary 1600x900+0+0 0mm x 0mm
   1600x900       0.00* 
   1024x768       0.00  
   800x600        0.00  
   640x480        0.00 [/COLOR]



After installing the NOUVEAU driver into my Ubuntu, and after that, the "xrandr -q" output showed the others two monitors(screens) :
[COLOR=#d35400]

~$ xrandr -q
Screen 0: minimum 8 x 8, current 1600 x 768, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
   1920x1080_60.00  59.96  
HDMI2 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 440mm x 250mm
   1600x900      60.00*+
   1440x900      74.98    59.90  
   1280x800      74.93    59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
  1024x768_60.00 (0x17f) 63.500MHz -HSync +VSync
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock  47.82KHz
        v: height  768 start  771 end  775 total  798           clock  59.92Hz

[/COLOR]But my Ubuntu is broken and I was unable to install the NOUVEAU driver at my Kali. (I was following that link to install the NOUVEAU driver at my Ubuntu: 

[https://nouveau.freedesktop.org/wiki/InstallNouveau/#distro-packages](https://nouveau.freedesktop.org/wiki/InstallNouveau/#distro-packages) )


Now, I only can use Kali, after trying to edit the Xorg at my Ubuntu...I cannot login into it.

I wold like to ask for a help to config my three monitors on Kali... 

tanks

---

