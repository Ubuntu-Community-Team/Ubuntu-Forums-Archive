---
title: "Native resolution on Acer TravelMate 4060"
date: 2005-11-03
forum: Desktop Environments
---

### Post by rwh on 2005-11-03
Hi all,

I was robbed recently and my insurance company saw fit to provide me with an Acer TrevelMate 4060 as a replacement for a stolen laptop.  It has a widescreen LCD with a native resolution of 1280x800.  A fresh install of Ubuntu Breezy has X running at 1024x768, unfortunately.

Now here's the confusing part: my xorg.conf has all of the resolutions specified correctly (1280x800), but the actual resolution the desktop is using is 1024x768.  The System->Preferences->Screen Resolution tool also only has 1024x768 as an option.

Does anyone have any ideas on how to get it to run at the native resolution?  I'll include the relevant sections of my (automatically generated) xorg.conf below.

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection
```

---

