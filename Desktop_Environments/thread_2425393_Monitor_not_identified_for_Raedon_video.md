---
title: "Monitor not identified for Raedon video"
date: 2019-08-25
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2019-08-25
I have a computer with a AMD Raedon chip set running 18.04 LTS I cannot set the display to the correct resolution. The monitor preferences show an unknown monitor and doesn't show all of the available resolutions. I have printed out some information below. I have searched for solutions but the information I've found seem to point mostly to Nvidia chip sets.


```
$ lspci |grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4250]
$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
HDMI-0 disconnected (normal left inverted right x axis y axis)
```

---

### Post by cruzer001 on 2019-08-25
I would try adding the correct resolution to xrandr.

[https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

---

### Post by Autodave on 2019-08-25
What cables and adapters are you using to connect the monitor?  If VGA, the cheaper cables do not have the extra wire in them to give the monitor info to the PC.  Whether VGA or not, I would definitely try another cable.

---

### Post by rsteinmetz70112 on 2019-08-26
I'm using a VGA cable. The Monitor has a VGA and HDMI the motherboard has a VGA and DVI. I'll try another cable but I recently changed the monitor and the previous monitor worked just fine with this cable. In fact this monitor worked until recently.

---

### Post by rsteinmetz70112 on 2019-08-26
Swapped out the cable and everything is good. Thanks.

---

