---
title: "Desktop Effects No Longer Working..."
date: 2009-11-13
forum: Desktop Environments
---

### Post by bmosov01 on 2009-11-13
I was messing around with screen resolution with a projector yesterday and now my desktop effects (and compiz) have stopped working completely.  Yesterday, compiz worked great (window animations, desktop cube, workspace slider, fire, rain, etc.), and now I am unable to enable my desktop effects.  I've been searching on threads all morning looking for a solution, but have been unable to find anyone with my exact problem.

I'm running Ubuntu Intrepid 8.10 on a Lenovo Thinkpad T400 using the Intel integrated graphics chip ( I also have an ATI Mobility Radeon card with discrete graphics, but I disabled it in the BIOS as it didn't seem to allow native resolution in Ubunto).  I downloaded Forlong's script compiz-check and have the following output:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

I've tried uninstalling compiz, and then reinstalling, but no luck.  I read quite a few posts from this thread: [http://www.uluga.ubuntuforums.org/showthread.php?t=799070&highlight=intrepid+intel+desktop+effects&page=8](http://www.uluga.ubuntuforums.org/showthread.php?t=799070&highlight=intrepid+intel+desktop+effects&page=8), but couldn't find an answer to my question.  

Lastly, I don't know if this is relevant or not, but I think the thing that screwed up my display in the first place was adjusting the virtual resolution.  When I was fiddling with the projector, I was able to get it to display properly, but had to readjust the resolution on my laptop screen, and then mirror displays.  Like I said, this worked, but upon changing my virtual resolution, I could no longer revert to 1400x900 native resolution.  I reverted my xorg.conf file and currently it is as follows:
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
(END) 

```

Anyway, I've been using Linux for about 6 months now, so I'm not a seasoned veterans, but not quite a noob either.  And since I had everything working great before yesterday, I know it's possible on my hardware (I know I had the discrete graphics disabled then too).  I'm currently at a loss....

Any help will be greatly appreciated!

---

### Post by bmosov01 on 2009-11-13
Any thoughts??

---

