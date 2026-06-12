---
title: "Screen res &amp; monitor capabilities"
date: 2009-10-12
forum: Desktop Environments
---

### Post by 47tuc on 2009-10-12
The EDID information from my monitor indicates that it is only capable of 1024x768. However I am currently running 1280x960.
Here's the EDID info from get-edid:
```
 parse-edid: parse-edid version 1.4.1
parse-edid: EDID checksum passed.

    # EDID version 1 revision 2
Section "Monitor"
    # Block type: 2:0 3:fc
    Identifier "IBM E74"
    VendorName "IBM"
    ModelName "IBM E74"
    # Block type: 2:0 3:fc
    # Block type: 2:0 3:fd
    HorizSync 30-69
    VertRefresh 50-120
    # Max dot clock (video bandwidth) 110 MHz
    # Block type: 2:0 3:ff
    # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

    Mode     "1024x768"    # vfreq 84.997Hz, hfreq 68.677kHz
        DotClock    94.500000
        HTimings    1024 1072 1168 1376
        VTimings    768 769 772 808
        Flags    "+HSync" "+VSync"
    EndMode
    # Block type: 2:0 3:fc
    # Block type: 2:0 3:fd
    # Block type: 2:0 3:ff
EndSection
```compiz-check tells me this about my video setup:
 ```
Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX
```Is anyone able to explain to me how/why the video res is set to other than what the monitor says it's capable of?

---

