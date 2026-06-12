---
title: "Enabling direct rendering"
date: 2007-02-08
forum: Desktop Environments
---

### Post by ittiam on 2007-02-08
Hi i have been trying to enable direct rendering in my laptop for some time quite unsuccessfully! 

This is my output of **915resolution -l**

[i]Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel
[/i]
 
And my device section in xorg.conf

[i]Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        Option "XAANoOffscreenPixmaps"
        BusID           "PCI:0:2:0"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

[/i]

Can anyone suggest what am not doing or what am i doing wrong?

---

### Post by ittiam on 2007-02-08
One more thing in my /var/log/Xorg.0.log, i found this

[drm] failed to load kernel module "i915"

---

### Post by ittiam on 2007-02-14
isn't there anyone who can help me out with this? can i sound more desperate?](*,)

---

