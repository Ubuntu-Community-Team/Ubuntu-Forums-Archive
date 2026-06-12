---
title: "Beryl caused change in resolution"
date: 2007-04-07
forum: Desktop Effects &amp; Customization
---

### Post by remick182 on 2007-04-07
I just installed Edgy on my PC and was finishing up with installing all of the programs and codecs and what-not when I ran across a weird error.  I used Envy and Automatix2 to install everything I wanted on my Ubuntu OS.  That all went fine.  My nVidia card was correctly set up along with my Samsung widescreen monitor displaying 1440x900@59.

I watched a movie, then decided to add a couple more things.  I went here [[http://ubuntuguide.org/wiki/Ubuntu_Edgy]](http://ubuntuguide.org/wiki/Ubuntu_Edgy])  to install some games.  I jumped into them to make sure that they worked, and they did.  I then had the bright idea to try and give Beryl a second chance (I used it once before w/ poor results on my onboard video card).  After everything was done, I hit ALT-CTRL-BKSP to resart the X-server and lost my 1440x900@59.  I'm stuck with a blurry 1280x960@51.  I backed up my original xorg.conf in case of something like this, however, I still can't revert back to my 1440x900.  I don't have the option.  I rechecked xorg, I restarted it again, I even rebooted my PC with no joy.

Is there a way to fix this issue?  Possibly reinstalling the nVidia driver or something?

xorg.conf:

Section "Monitor"
    Identifier     "SyncMaster"
    HorizSync      25-100    
    VertRefresh    30-90
    Option         "DPMS"
    Modeline       "1440x900@59" 108.84 1440 1472 1880 1912 900 918 927 946
EndSection

Section "Device"
    Identifier     "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900_59" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900_59" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900_59" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900_59" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900_59" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900_59" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by reclusivemonkey on 2007-04-07
Do you have an onboard graphics card by any chance?

```

Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"

```

Would lead me to believe so. Is it disabled in the BIOS?

Personally, I would try removing the Modeline (AFAIK, this is completely unecessary any more), remove 

```

HorizSync 25-100
VertRefresh 30-90

```

and change all instances of "1440x900@59" to just "1440x900". I have a Nvidia card and a widescreen monitor and this works for me.

---

### Post by remick182 on 2007-04-08
Well, everything is fine now.  I played around with my xorg.conf and removed all resolutions from my 24 bit color depth section except for 1440x900.  Then I reset X and it came up fine at 51 instead of 59, but t looks fine, so what the hey?  Thanks for you help, I just wish I understood the behind-the-scenes workings of Linux a bit better...hehe.

---

