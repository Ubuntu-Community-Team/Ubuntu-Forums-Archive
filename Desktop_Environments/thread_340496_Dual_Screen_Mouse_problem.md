---
title: "Dual Screen Mouse problem"
date: 2007-01-17
forum: Desktop Environments
---

### Post by homer1976 on 2007-01-17
Hi

I've installed Edgy with a Radeon 9800 and fglrx.
I have two monitors, a normal 1280x1024 and a widescreen 1680x1050 res.
I installed Big Desktop by adding the usual lines to the "Device" section of xorg.conf


"
Option "Mode2"         "1680x1050" #Resolution for second monitor
Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
Option "HSync2" "65" #This sets the horizontal sync for the secondary display. 
Option "VRefresh2" "60" #This sets the refresh rate of the secondary display.
"


  ....which worked fine.... except


When I move the mouse cursor to the bottom of the 1280x1024 screen, the mapping to where the cursor clicks the desktop is off.... and its about the difference between the hight of the two monitors.



I don't know if thats overly clear so i'll try to explain it a different way.  When i go to the bottom of the 1280x1024 screen (to screw up the cursor mapping) and then click on the desktop.  The actual click will register about 20 pixels below where the cursor is pointing.

Has anyone else seen this problem. It is infuriating.  I want to start developing in Linux and drop XP, but this is the only thing stopping me.

TIA

Homer

---

