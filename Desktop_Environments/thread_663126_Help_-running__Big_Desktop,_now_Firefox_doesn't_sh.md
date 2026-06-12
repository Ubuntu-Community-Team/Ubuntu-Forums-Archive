---
title: "Help -running  Big Desktop, now Firefox doesn't show!"
date: 2008-01-09
forum: Desktop Environments
---

### Post by tjwolf on 2008-01-09
I finally found a posting that showed me how to minimally modify my xorg.conf to get a desktop which will span my laptop's native LCD (1680x1050) and an external LCD (1600x1200).  Everything seemed to work!  I started firefox and could easily drag it to my external monitor and back.

That was at work.  Now I'm at home with my laptop and no external monitor.  When I start firefox, I see the process running, but not the window!  I thought that maybe it's displaying in the part of the desktop that is no longer reachable (because of the missing external monitor), but when I look at the little desktops presentations  in the bottom right of the screen, I don't see it pop up *anywhere*.  But other X apps still seem to be working (e.g. Terminal, xclock, etc.)

I had to revert my xorg.conf file back to the original and restart X in order to get to this forum to post this.  Can anyone help?  Below is  the part of the xorg.conf file that I changed - feel free to criticize as I don't know what the hell I'm doing.  Many thanks in advance for all help.

tom

xorg.conf excerpt:
Section "Device"
        Identifier      "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
        Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off"
# --- The following was added for dual-head support:
        Option "DesktopSetup" "horizontal" # Enable Big Desktop
        Option "PairMode" "1680x1050+1600x1200" # Pair mode resolutions
        Option "DesktopSetup" "LVDS,AUTO"
#       Option "HSync2" "65.29" #The horizontal sync for the secondary display.
#       Option "VRefresh2" "59.954" #The refresh rate of the secondary display.
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0 0
                Virtual         1680 1200 # Combination of the two resolutions
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection

---

### Post by Coreigh on 2008-01-10
Two ides come to mind.
1) since you converted to post this, size and position the firefox window where you can see it and then close the application and re-open and close it again. Then try the dual-screen setup and see if it launches where you can see it.
2) Can you see the task bar buttons (window list buttons)? Right click on the button and try 'move' or try 'maximize' and the resize it again using the corners and the mouse.

'hope it works for you.

---

### Post by tjwolf on 2008-01-16
Hi Coreigh,
Thanks for trying to help, but your suggestions don't help:

1) I opened/closed firefox a couple times - each time firefox opens its window in location 0,0 (top left of my laptop screen).  But when I open it in the two-screen mode, it doesn't show up at all.

2) When I start firefox in the two-screen mode, I see the "Firefox starting" button in the task bar and then that disappears.  I see intense disk activity for another 10 seconds or so and then nothing!  Thinking that firefox core dumped, I did a quick check via 'ps' and see firefox is still running.  See the attached picture of my desktop - see in the terminal window that firefox is clearly there.  But also notice that there's no task bar button for firefox and there's no representation of it in the little desktops presentation in the lower right corner.  Since there is no taskbar button, I can't try your second suggestion.

So I'm at a loss for what to do - I just don't have enough X11 config skills to figure this one out :(
Any further suggestions would be much appreciated.

tom

---

### Post by maxlem on 2008-03-13
I have the same problem here. It only happens when I boot without the second screen plugged in. Firefox tries to load but it stops.

If I boot with the second screen plugged in and I unplug it, no problem. Konqueror doesn't care. 

Pretty weird bug. I guess ffox tries to occupy a screen position that doesn't exist.

---

