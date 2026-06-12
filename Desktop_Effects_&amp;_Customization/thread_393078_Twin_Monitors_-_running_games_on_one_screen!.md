---
title: "Twin Monitors - running games on one screen!"
date: 2007-03-25
forum: Desktop Effects &amp; Customization
---

### Post by LadyFox on 2007-03-25
Hi there, 

I wonder if anyone can help me?

I have set up my Ubuntu box with twin screens (thanks to helpful peeps here) and its all running fine. Im using TwinView with both screens attached to a NVidia Fx5500. 

I have been experimenting with running games under Crossover, they work fine, but the problem is that the game spreads across both screens (UT2003 incase it helps).  I cant find a 'window' to resize it. 

I'd like to run the game in one window (because, for starters, i cant see the gun as its in the center of the screen) but i cant figure out how. 

Now, when i launch Firefox and go full screen, it fills up one monitor only. I can drag windows and files around to either monitor. So, whats going on with the game?

Can anyone advise?  I'll print my xorg.conf if that helps?

Cheers!

---

### Post by Nikron on 2007-03-25
You need to edit your metamodes so one screen has the ability to be set to null.

---

### Post by LadyFox on 2007-03-25
Hello

Thanks for the reply. Ok, so what exactly do i need to add/edit?  My xorg.conf has this right now: 

> 
Section "Device"
    Identifier     "nvidiaTwin"
    Driver         "nvidia"
Option "TwinView" "True"
Option "TwinViewOrientation" "LeftOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "string"
EndSection

Section "Screen"
    Identifier     "ScreenTwin"
    Device         "nvidiaTwin"
    Monitor        "TwinMoni"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


It is a bit fudged to be honest, though its working and doing what i want it to do right now.  Any advice would be great!

Cheers!

---

### Post by nille on 2007-08-23
> **LadyFox said:**
> 
I have been experimenting with running games under Crossover, they work fine, but the problem is that the game spreads across both screens (UT2003 incase it helps).  I cant find a 'window' to resize it. 


It maybe doesn't help you much, but I just wanted to say that there are linux binaries for UT2k3, so you won't have to run it in Crossover :)

See some guides here:
[http://ubuntuforums.org/showthread.php?t=420743]("http://ubuntuforums.org/showthread.php?t=420743")
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+UT2003]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+UT2003")

---

