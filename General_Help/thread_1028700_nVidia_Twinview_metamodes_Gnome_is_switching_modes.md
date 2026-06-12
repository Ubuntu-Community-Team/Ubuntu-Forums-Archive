---
title: "nVidia Twinview metamodes: Gnome is switching modes on me?!?"
date: 2009-01-02
forum: General Help
---

### Post by ultim8 on 2009-01-02
Hey guys,

I'm setting up my Xorg.conf file to handle two monitors (laptop screen and an LCD screen).  In the conf file I have two metamodes set up, one for the LCD screen and laptop, and one for the laptop by itself (for when I'm not connected to the LCD screen):
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1600x1200 +0+0, DFP: 1920x1200_60 +1600+0; CRT: NULL, DFP: 1920x1200_60 +0+0" 
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```
When I boot up and GDM loads, both screens are visable.  If I tail /var/log/Xorg.0.log at this time everything looks good (only relevant output shown):
```
...
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT:1600x1200+0+0,DFP:1920x1200_60+1600+0"
(II) NVIDIA(0):     "CRT:NULL,DFP:1920x1200_60+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 3520 x 1200
...
...
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "CRT:1600x1200+0+0,DFP:1920x1200_60+1600+0"
...
```
But when I log in and Gnome loads my LCD screen goes blank and my tail of /var/log/Xorg.0.log has one line added to it:
```
(II) NVIDIA(0): Setting mode "CRT:NULL,DFP:1920x1200_60+0+0"
```
It would appear like Gnome is changing the metamode on me...

So my questions are:
[LIST=1]
[*]Is my understanding of metamodes correct (try the first mode, if it doesn't work then try the 2nd...)
[*]Is it Gnome that is changing the metamode?
[*]Can I fix it so that it does NOT change the mode?
[*]how can I change the mode (i.e. a hotkey command, or a command line function)? [COLOR="Red"]<EDIT>OK, I found can do this by typing "xrandr -s 0" for the first mode or "xrandr -s 1" for the second mode.  I can also change metamodes from nvidia-settings.[/COLOR]
[/LIST]

p.s. Please no blind answers of "just use nvidia-settings".  I used nvidia-settings to get the Xorg.conf file I currently have.  I want to try to set this up using multiple metamodes.

---

### Post by cavevimmentis on 2009-11-03
Not using Ubuntu, but I am experiencing exactly the same thing - nVidia TwinView with metamodes for two side-by-side monitors, in which GDM shows the correct setup, then the metamode changes on starting GNOME, and only one monitor is used.  xrandr -s 0 works here too.

Have you made any progress on this since you posted?  If so, any info would be helpful; otherwise, I'll keep working on it and post any findings here.

---

### Post by cavevimmentis on 2009-11-03
In my case, it looks like it was gnome-settings-daemon doing the switching - determined by removing the metamode it was switching to, discovering that it cause an unmarked error message (unmarked in that it didn't say which program threw it), using pstree to find what looked like the process owning the window, and messing around.  Googling around some bug reports, I found one related to '~/.config/monitors.xml' that caused the same error message, so I moved that to a backup location, and everything worked gloriously, even after putting the other metamode back into xorg.conf!

See if that works for you

---

### Post by TechieAu on 2010-01-25
> **cavevimmentis said:**
> Googling around some bug reports, I found one related to '~/.config/monitors.xml' that caused the same error message, so I moved that to a backup location, and everything worked gloriously, even after putting the other metamode back into xorg.conf!

See if that works for you

That worked a treat, thanks for sharing!

---

### Post by jaygo on 2010-08-17
worked great for me too. Thanks bunches!

---

