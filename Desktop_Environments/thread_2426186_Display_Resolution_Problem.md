---
title: "Display Resolution Problem"
date: 2019-09-05
forum: Desktop Environments
---

### Post by rbscairns on 2019-09-05
I recently installed Lubuntu 18.04 running with MS Windows XP Home on my PC. Win XP allows me to set my display resolution to 1280 x 720 60Hz. Lubuntu 18.04 only gives me a choice of:
[LIST]
[*]640 x 480
[*]848 x 480
[*]800 x 600
[*]1024 x 768
[/LIST]
xrandr returns:
```
~$ xrandr
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
DVI1 unknown connection primary (normal left inverted right x axis y axis)
   1368x768      59.88  
   1360x768      59.80  
   1280x800      59.81  
   1152x864      60.00  
   1280x720      59.86  
   1024x768      60.00  
   1024x576      59.90  
   960x540       59.63  
   800x600       60.32  
   640x480       59.94  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```
My display has VGA and DVI-D (Dual Link) connections. My PC has a DVI-I (Dual Link) connection with a VGA adapter. I am currently using the display with a VGA cable.

How can I set my display resolution to 1280 x 720 in Lubuntu 18.04? I would like this to occur automatically before I log in however it would be acceptable if it occurred automatically immediately after logging in.

---

### Post by Autodave on 2019-09-06
Try another, known good, VGA cable.  Cables fail and some that are cheaper fail to have one wire in them that reports the monitor's info to the graphics card.  Windows will ignore this, but Linux will not.

---

### Post by pcfan1234 on 2019-09-07
You can add you own modelines to you xorg.conf
I recommend buying a DVI cable instead of another adapter oder VGA cable.
Please give us info about your graphics card.

---

### Post by mörgæs on 2019-09-07
Yes the output from **lshw -C video** would be interesting.

---

### Post by rbscairns on 2019-09-08
I have decided to order a DVI-D cable before delving into adding modlines. The cable should become available this week.

lshw -C video returned:
```
*-display:0               
       description: VGA compatible controller
       product: Mobile 945GSE Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fbd00000-fbd7ffff ioport:dc80(size=8) memory:d0000000-dfffffff memory:fbcc0000-fbcfffff memory:c0000-dffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fbd80000-fbdfffff
```
I will return to this thread after I have tried my DVI cable.

---

### Post by rbscairns on 2019-09-15
Problem was solved by using a DVI-D cable rather than the VGA cable that I was using. I can now choose the correct resolution for me.

Again, thank you for all the guidance.

---

