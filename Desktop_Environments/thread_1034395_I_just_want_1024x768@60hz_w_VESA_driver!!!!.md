---
title: "I just want 1024x768@60hz w/ VESA driver!!!!"
date: 2009-01-08
forum: Desktop Environments
---

### Post by Underpants on 2009-01-08
Going crazy over here. I have a system that I know is capable of the resolution that I'd like it to use. I've been toying with my modelines and this is where it is right now. I can't get it past 800x600 resolution.

Comments? Suggestions?

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"

#HorizSync 30 - 107
#VertRefresh 48 - 170


# V-freq: 60.00 Hz  // h-freq: 47.80 KHz
#Modeline "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796
#Modeline "1024x768@60" 64.56 1024 1056 1296 1328 768 783 791 807
Modeline "1024x768@75" 85.52 1024 1056 1376 1408 768 782 792 80

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"


SubSection "Display"
#                Depth           16
#                Modes           "1024x768"
        EndSubSection


EndSection
```

---

### Post by MIKE SILVA on 2009-09-07
Hi!,

One question: You need "vesa"?
If you delete the part "vesa" on xorg.conf
save and reboot?

What happen? For me it works better without "vesa". 

Regards

---

### Post by SlugSlug on 2009-09-07
try this

[https://launchpad.net/envy](https://launchpad.net/envy)

---

### Post by Zimmer on 2009-09-07
Check the xorg.log first to see what is going on..  what video card have you got? Have you solved this already? (it was JAnuary when you posted!!)

---

