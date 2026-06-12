---
title: "Beryl - No handle or status bar"
date: 2007-03-15
forum: Desktop Environments
---

### Post by toddhd on 2007-03-15
I am running Edgy Eft, and just upgraded to Beryl 0.2.0 today. I still have the same problem I had before. When I start Beryl, all open windows are missing the handle (the area above the menu that would have the close/min/max butons) and no status bar (under the window). In fact, there is no way to drag the window unless I use ALT+LM. 

I went into the Theme manager, and I have tons of themes there, but no matter what I click on, nothing changes.

I have reinstalled both Ubuntu and Beryl and my nVidia drivers repeatedly, and the same problem occurs every time. I'm really at a loss. 

I did search on the forums, and tried suggestions that I saw (i.e. [http://ubuntuforums.org/showthread.php?t=369703](http://ubuntuforums.org/showthread.php?t=369703)) but nothing seems to help.

Please, please, please, if anyone is willing to work with me, I'll be happy to provide whatever troubleshooting info you require. Thank you!

---

### Post by Slim Odds on 2007-03-15
Put this:```
Option         "AddARGBGLXVisuals" "True"
``` in the device section of xorg.conf for you video card

---

### Post by toddhd on 2007-03-15
This screenshot may help explain
[http://www.seaburydesign.com/screenshot.png]("http://www.seaburydesign.com/screenshot.png")

---

### Post by toddhd on 2007-03-15
> **Slim Odds said:**
> Put this:```
Option         "AddARGBGLXVisuals" "True"
``` in the device section of xorg.conf for you video card

Thanks. I did that and rebooted. No change. Below is the section I added it to. Note that the line in question was already in the screen section as well.

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection

---

### Post by Slim Odds on 2007-03-15
You also need this:     Option         "XAANoOffscreenPixmaps"

and this:

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by toddhd on 2007-03-15
> **Slim Odds said:**
> You also need this:     Option         "XAANoOffscreenPixmaps"

and this:

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Which section does:
Option         "XAANoOffscreenPixmaps"
go into?

---

### Post by toddhd on 2007-03-15
I added that line to the Devices section of my xorg.conf, and added the extra section as well. No change. Well, not 100% true - since the first change above, all windows I open now open Maximized, and I have no way to shrink them.

---

### Post by toddhd on 2007-03-16
*bump*ing in hopes of getting more assistance :KS

---

### Post by jenhsun on 2007-03-16
> **toddhd said:**
> I am running Edgy Eft, and just upgraded to Beryl 0.2.0 today. I still have the same problem I had before. When I start Beryl, all open windows are missing the handle (the area above the menu that would have the close/min/max butons) and no status bar (under the window). In fact, there is no way to drag the window unless I use ALT+LM. 

I went into the Theme manager, and I have tons of themes there, but no matter what I click on, nothing changes.

I have reinstalled both Ubuntu and Beryl and my nVidia drivers repeatedly, and the same problem occurs every time. I'm really at a loss. 

I did search on the forums, and tried suggestions that I saw (i.e. [http://ubuntuforums.org/showthread.php?t=369703](http://ubuntuforums.org/showthread.php?t=369703)) but nothing seems to help.

Please, please, please, if anyone is willing to work with me, I'll be happy to provide whatever troubleshooting info you require. Thank you!

I have the same problem as yours before.
I think here is your answer:
[http://forum.beryl-project.org/viewtopic.php?f=35&t=1631](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631)

By the way, here is more complete setup steps for Beryl
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

---

### Post by toddhd on 2007-03-18
Just as a followup for others, I finally got this working. The problem was that my defualt video settings had a depth of 16. I changed the depth to 24 in my xorg.conf, and all of a sudden my nVidia and Beryl worked like a charm!

---

### Post by jenhsun on 2007-03-18
> **toddhd said:**
> Just as a followup for others, I finally got this working. The problem was that my defualt video settings had a depth of 16. I changed the depth to 24 in my xorg.conf, and all of a sudden my nVidia and Beryl worked like a charm!

Good to hear that, toddhd.
After I fixed my problem about the issue of display the windows handle /title bar, enjoy the beryl and the other effect, then well, I just close it for effective and performance because my old hardware condition.

---

