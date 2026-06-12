---
title: "nvidia driver forcing horiz/vert"
date: 2008-04-25
forum: Desktop Environments
---

### Post by quintok on 2008-04-25
I just did a fresh install of ubuntu hardy and everything went fine up until I installed the nvidia driver using "Hardware Drivers".  After the restart my monitor (LG L1730S) went to power saving mode with an error saying:
81.3KHZ / 65HZ - out of range
So I edited my xorg.conf file to limit the refresh rate/etc of the monitor
> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "LG"
    ModelName      "L1730S"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection
as stipulated by the monitor's manual.
I rebooted and it spat out the same issue.  Am I attempting to do the right thing?  

n.b. When I change to the 'nv' driver from 'nvidia' the monitor is okay and will display the monitors resolution of 1280x1024x75 just fine

Thanks.

---

