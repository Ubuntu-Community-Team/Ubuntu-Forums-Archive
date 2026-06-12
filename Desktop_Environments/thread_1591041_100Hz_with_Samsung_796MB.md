---
title: "100Hz with Samsung 796MB"
date: 2010-10-08
forum: Desktop Environments
---

### Post by speeedfire on 2010-10-08
Hy!

I use ubuntu 10.04 with Samsung 796MB crt monitor and ati 3850, but the monitor is runinng in 85Hz.

I use this xorg.conf, but the system is running olny with 85hz.

```
Section "Monitor"
    Identifier "Configured Monitor"
    Vendorname "Generic CRT Display"
    Modelname "Monitor 1024x768"
    Horizsync 30-85
    Vertrefresh 50-160
    # 1024x768 @ 100.00 Hz (GTF) hsync: 81.40 kHz; pclk: 113.31 MHz
    Modeline "1024x768_100.00" 113.31 1024 1096 1208 1392 768 769 772 814 -HSync +Vsync
EndSection
```

This is the xorg log. [http://pastebin.com/2Lb03NKg](http://pastebin.com/2Lb03NKg)

---

