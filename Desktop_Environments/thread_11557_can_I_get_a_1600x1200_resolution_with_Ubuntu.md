---
title: "can I get a 1600x1200 resolution with Ubuntu?"
date: 2005-01-17
forum: Desktop Environments
---

### Post by brjoon1021 on 2005-01-17
I just got a nice LCD with the native resolution as 1600x1200 and I did not see this option in the dropdown menu with Gnome. I am willing to use one of the other window managers.

---

### Post by DJ_Max on 2005-01-17
Your LCD screen may be able to do 1600x1200, but can your video card handle it? Your Video Card & Monitor need to be able to support 1600x1200.

---

### Post by daniels on 2005-01-17
Edit /etc/X11/XF86Config-4, remove the HorizSync and VertRefresh lines.

---

### Post by brjoon1021 on 2005-01-18
Oh yeah. I have a great video card. I have not done much editing of code. Is this a pretty easy fix? Do I do it exactly as described?

Thanks

---

### Post by Rancoras on 2005-01-18
The man's a developer for Unbuntu, he should know  :D

---

### Post by daniels on 2005-01-18
Sure.  Just open it up with an editor as root (e.g. sudo gedit /etc/X11/XF86Config-4), look for the lines starting with HorizSync and VertRefresh (which will be one under another), and obliterate them completely.

---

### Post by DJ_Max on 2005-01-18
[QUOTE=Rancoras]The man's a developer for Unbuntu, he should know  :D[/QUOTE]
ROFL :mrgreen:

---

### Post by zygut on 2005-01-19
[QUOTE=daniels]Sure.  Just open it up with an editor as root (e.g. sudo gedit /etc/X11/XF86Config-4), look for the lines starting with HorizSync and VertRefresh (which will be one under another), and obliterate them completely.[/QUOTE]

I do this and restart X and I still have no resolutions better than 1024x768 --- this is on a thinkpad X40 (refresh rate is 60hz)

---

### Post by daniels on 2005-01-19
You do know the X40's panel only does 1024x768, right?

---

### Post by tomchuk on 2005-01-19
You'll want to change your device section in /etc/X11/XF86Config-4 to look something like this:

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"  ## whatever Ubuntu setup named it
        Driver          "radeon"  ## change to radeon
        BusID           "PCI:1:0:0"  ## whatever Ubuntu setup detected
        Option          "RenderAccel"   "true"  ## optional
        Option          "AGPMode"       "4"  ## optional
        Option          "AGPFastWrite"  "true"  ## optional
        Option          "MonitorLayout" "LVDS, TMDS"  ## need this - says you have the laptop LCD as primary and an external LCD as secondary
        Option          "CloneMode"     "1600x1200"  ## need this - resolution of LCD
#       Option          "PanelOff"      "true"  ## uncomment if you want to turn the laptop LCD off in clone mode
#       Option          "CloneHSync"    "30-80"  ## ext. LCD HSync
#       Option          "CloneVRefresh" "60-90"  ## ext. LCD VRefresh
EndSection

```

That is if you don't want the desktop to span both monitors and only want to clone the desktop to the bigger monitor. **man radeon** for more info. I've got a xorg config for a t40 with some serious xinerama configurations and screen layout options if you're interested in the desktop spanning both monitors, and not cloning.

---

### Post by daniels on 2005-01-19
Actually, if you ever need to use MonitorLayout, it's a bug -- every possible setup should be autodetected now.

---

