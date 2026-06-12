---
title: "Xinerama with one display rotated &gt; cursor woes"
date: 2006-04-11
forum: Desktop Environments
---

### Post by incunabulum on 2006-04-11
Hi there,

currently, I am configuring my laptop to use an external lcd as second monitor. The second monitor is rotated 90 degrees. 

The problem I now have is that the direction of the cursor is not rotated on the rotated screen, i. e. on the second screen mouse handling goes to hell. if you move the mouse to the left, on the internal lcd the cursor moves to the left. On the rotated screen the cursor moves to the top of the display....

*So, is there any option to rotate the mouse cursor directions on only one screen????*

Here the relevant snippets from my xorg.conf 
```

Section "Device"
        Identifier      "Intel-LCD"
        Driver          "i810"
        #Driver         "vesa"
        BusID           "PCI:0:2:0"
        Option          "VBERestore" "true"
        VideoRam        16384
        # MonitorLayout "pipeA, pipeB". I'm not sure what a pipe is...
        # LFP = local flat panel...
        Option          "MonitorLayout" "CRT,LFP"
        Screen          0
EndSection

Section "Device"
        Identifier      "Intel-external"
        Driver          "i810"
        #Driver         "vesa"
        BusID           "PCI:0:2:0"
        VideoRam        16384
        Option          "Display"       "CRT"
        Option          "MonitorLayout" "CRT,LFP" # put crt on pipe A
        Screen          1
EndSection

Section "Screen"
        Identifier      "Local LCD"
        Device          "Intel-LCD"
        Monitor         "LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "External LCD"
        Device          "Intel-external"
        Monitor         "LCD-external"
	Option 		"Rotate" "CCW"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Dual1600"
        Screen 0        "Local LCD" Absolute 0 0 
        Screen 1        "External LCD" LeftOf "Local LCD"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
Section "ServerFlags"
        Option "Xinerama" "true"
EndSection

```


by, inc

---

### Post by mbeach on 2006-04-13
I came here to ask the exact same question.

I've rotated my display (using Option "Rotate" "CCW" in the device section) and surprisingly it worked (because I'm using onboard Intel 82915G/GV/910GL Express Chipset) but the mouse cursor is behaving as you describe.

I did notice that if you move the physical mouse (not the representation on screen) to the top left corner and click, you can activate the menu.  Interesting. 

Also, if I enable remote desktop and VNC to the machine, the VNC dot (cursor) works perfectly.  I would think something has to be changed having to do to with the mouse layer overlay on the graphical display to change it's orientation. 

I am trying this on the Dapper Drake, flight 6.

Sorry no solution but if I find one elsewhere I'll post it here.

---

### Post by mbeach on 2006-04-13
as it turns out I'm using the i810 driver as well and this is what ended up working for me (all taken from the man page for i810).  I do have some issues on after the monitor goes into power save mode, but I'll worry about those later.  I'm doing this on 6.06 flight 6.

in the device section I'm now using:
```

Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option "SWCursor" "true"
        Option "Rotate" "CCW"
EndSection

```

---

### Post by incunabulum on 2006-04-18
mbeach,

in my case (i810 driver also) the SWCursor option only works if I rotate both screens. 

Just rotating the external screen either gives me complete giberish on the screen or the symptoms described above aka the cursor is not rotated....

Any further ideas?

---

