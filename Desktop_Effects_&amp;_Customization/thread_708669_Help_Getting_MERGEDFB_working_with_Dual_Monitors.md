---
title: "Help Getting MERGEDFB working with Dual Monitors"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by bantam59 on 2008-02-26
I am trying in Vane to get my dual monitors working with MergedFB, i cannot seem to get or find any answers so i am desperate someone will oblige.
i have followed the instructions word for word as described in this how to
[B]Step 1. This is about the simplest how to, simply copy the following lines to your "Device" Section:
Code[/B]

Option "MergedFB" "true" #Enable MergedFB function
  Option "MonitorLayout" "LVDS (TMDS), CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  Option "OverlayOnCRTC2" "true"
  Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"

[B]Step 2. Next, go to the "Monitor" Section and add the following
Code:[/B]

Horizsync    28-64 #You may wish to change the values to fit your specific monitor
    Vertrefresh    43-60

However the thing confusing me is this. WHICH monitor is it referring to in Step 1. ?
is it referring to my MAIN monitor? do i apply the proper specs that match my MAIN monitor? or is it referring to the 2nd monitor i am trying to add?

For Step 2. I have the same question, so i ADD additional settings to the monitor section or change them according to the monitor, if so WHICH monitor is this referring to?

i have trid numerous configurations and end up with either cloned screens with 640x480 resolution or a blank screen on both monitors.
**ALSO** Which drivers should i be using?  i have an ATI Radeon x600 dual head card, should i be using the proprietary drivers (fglrx) or no? or should i be using the plain ATI drivers?

Someone please help me out here.
Additional Info: I am running Kubuntu Gutsy , ATI Radeon x600 pcie, Pentium 4 , with 3gb ram, Main Monitor = eView 17f2 17 inch monitor , 2nd monitor Insignia 19inch monitor (BOTH CRT)
im at your mercy!
PS the link for the original How To can be found here.

[COLOR="Red"][http://ubuntuforums.org/showthread.php?p=1773710]("http://ubuntuforums.org/showthread.php?p=1773710")[/COLOR]

---

