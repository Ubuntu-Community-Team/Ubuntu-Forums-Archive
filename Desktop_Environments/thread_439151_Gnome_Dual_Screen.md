---
title: "Gnome Dual Screen"
date: 2007-05-10
forum: Desktop Environments
---

### Post by Psicolonia on 2007-05-10
hi everyone, this should be easy for you!

I've got everything working fine (almost) my only problem is that my primaryscreen is not the Laptop LCD!

here's my device section:

```
Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option  "DRI"                           "true"
        Option  "MergedFB"                      "true"
        Option  "MonitorLayout"                 "CRT,LFP"
        Option  "SecondPosition"                "LeftOf"
        Option  "MetaModes"                     "1280x768-1024x768"
	Option  "MergedXineramaSecondIsScreen0" "true"
        Option  "SecondMonitorHorizSync"        "28-49"
        Option  "SecondMonitorVertRefresh"      "60-72"
        Option  "MergedNonRectangular"          "true"
EndSection
```

Everything is fine even the screen sizes: 1024 at the left and 1280 at the main screen. (wich is not...)

So basically i would like to make the laptop screen the main screen without changing anything else. By the way I'm treid false on MergedXinerama.

Addicional, anyone can tell me how to enable compiz like this? everything goes blank if I have compiz activated!

Thanks in advance!!
Reply With Quote

---

### Post by jocko on 2007-05-10
I'm not sure this will help, but try changing:
```

        Option  "MonitorLayout"                 "CRT,LFP"

```
to:
```

        Option  "MonitorLayout"                 "LFP,CRT"

```

---

### Post by Psicolonia on 2007-05-10
that messes everything up! display size, and all! :(

---

### Post by jocko on 2007-05-10
> **Psicolonia said:**
> that messes everything up! display size, and all! :(

Ooops.. I realized you probably need to change the metamodes and sync rates as well to reflect the changed order of the monitors.

I'm just guessing here, but I guess the first monitor listed in MonitorLayout will be the primary monitor, and the first resolution in MetaModes will be the resolution of the primary monitor...
Try reversing the metamode to "1024x768-1280x768" and change the second monitor sync rates to reflect the capabilities of your CRT instead.
(But keep a backup of your original xorg.conf in case this messes things up.)

---

### Post by xfeed on 2007-05-10
hi 

changing

Option  "SecondPosition"                "LeftOf"

to

Option  "SecondPosition"                "RightOf"

---

### Post by Psicolonia on 2007-05-10
Changing sync rates blew it too. (changing everything.)

About changing to "RightOf" i have my monitor on the left :( and when i'm working right off everything goes smooth too and my primary screen is correct. only... I have to go through the right side of the screen to get the left screen content... it's pretty wierd!!!

thanks to everybody that's helping!

---

### Post by Torres on 2007-05-20
hi,

i have the exact same problem,
so if anybody could help, i would be very thankfull

---

