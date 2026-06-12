---
title: "Ubuntu running slow on Dell Dimension 2400"
date: 2008-11-27
forum: Desktop Environments
---

### Post by poke4christ on 2008-11-27
My mother has a Dell PC that is low end and a little old.  About a year back it was running pretty slow on it's boot of windows and I decided ubuntu would be better for it and still serve her purpose.  Well, it hasn't ended up that way.

It ran fairly well at first, but it's just become very slow.  I didn't think you got those kinds of problems with Ubuntu since it didn't have a registry or a need for defragmenting.  We even uped the ram from 256MB to 768 MB.  That hasn't seemed to help that much.

Specifically, the GUI enviroment is very slow.  Words take time to show as does switching programs.  In addition, video rarely runs smoothly.  I'm wondering if the video driver is appropriate for the integrated card on the motherboard.

Here are the specs.

Dell Dimension 2400
Processor:  Intel Celeron 2.6Ghz
Chip Set: Intel 845GV
Ram: 256 + 512 (may be different types)
Video: integrated Intel 3D Extreme Graphics

Let me know if there is any other info you need.  Any help is appreciated.  Thanks in advance.

Zach

---

### Post by poke4christ on 2008-11-27
Just checked the xorg.conf.  Here's the video driver info.

```
Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection
```

---

### Post by poke4christ on 2008-11-27
Well, I ran the updates and it seems to have fixed the problem.  I've run them in the past every time I've been here, but this is the first time I've seen any impact.  It's awesome.  Text now has no delay and video runs excelently.  Programs and tabs switch fairly fast and are probably only held back by the old/crapy hardware. This is what I've expected.  I guess it just needed better configuration provided by one of the updates.  Who knows which one.

---

