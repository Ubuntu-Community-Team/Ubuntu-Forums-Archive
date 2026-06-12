---
title: "three monitor setup with ati &amp; nvidia"
date: 2009-11-14
forum: Desktop Environments
---

### Post by sunnstorm7 on 2009-11-14
I know, it's not a perfect marriage between these two cards, but here they are

```
03:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
04:08.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
```I'm attempting to set up a triple-monitor display with this configuration.  Ubuntu 9.10 did a great job in dual-displaying on the ATI, however it seems to be ignoring the nvidia as a valid display entirely.  Does anyone have any ideas?  

I used to be able to figure this out with xorg.conf, but it seems many things have changed since 8.04.  All that remains in the file after configuring my dual display with the stock display helper is the following:

```
Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        SubSection "Display"
                Virtual 2560 1024
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection
```

---

