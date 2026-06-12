---
title: "Xorg correctly detects screen size &amp; resolution, but DPI sets wrongly"
date: 2021-02-20
forum: Desktop Environments
---

### Post by ruwolf on 2021-02-20
I have installed Xubuntu 20.10.
Xorg correctly detects screen size & resolution, but DPI sets wrongly.
This is part of my /var/log/Xorg.0.log:
```

[    13.634] (II) RADEON(0): EDID for output eDP
[    13.634] (II) RADEON(0): Manufacturer: CMN  Model: 15cb  Serial#: 0
[    13.634] (II) RADEON(0): Year: 2014  Week: 2
[    13.634] (II) RADEON(0): EDID Version: 1.4
[    13.634] (II) RADEON(0): Digital Display Input
[    13.634] (II) RADEON(0): 6 bits per channel
[    13.634] (II) RADEON(0): Digital interface is DisplayPort
[    13.634] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    13.635] (II) RADEON(0): Gamma: 2.20
[    13.635] (II) RADEON(0): No DPMS capabilities specified
[    13.635] (II) RADEON(0): Supported color encodings: RGB 4:4:4 
[    13.635] (II) RADEON(0): First detailed timing is preferred mode
[    13.635] (II) RADEON(0): Preferred mode is native pixel format and refresh rate
[    13.635] (II) RADEON(0): redX: 0.565 redY: 0.330   greenX: 0.323 greenY: 0.577
[    13.635] (II) RADEON(0): blueX: 0.160 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    13.635] (II) RADEON(0): Manufacturer's mask: 0
[    13.635] (II) RADEON(0): Supported detailed timing:
[    13.635] (II) RADEON(0): clock: 136.6 MHz   Image Size:  344 x 193 mm
[    13.635] (II) RADEON(0): h_active: 1920  h_sync: 1964  h_sync_end 1992 h_blank_end 2070 h_border: 0
[    13.635] (II) RADEON(0): v_active: 1080  v_sync: 1082  v_sync_end 1086 v_blanking: 1100 v_border: 0
[    13.635] (II) RADEON(0):  N156HGE-EBB
[    13.635] (II) RADEON(0):  CMN
[    13.635] (II) RADEON(0):  N156HGE-EBB
[    13.635] (II) RADEON(0): EDID (in hex):
[    13.635] (II) RADEON(0):     00ffffffffffff000daecb1500000000
[    13.635] (II) RADEON(0):     021801049522137802ef059054529329
[    13.635] (II) RADEON(0):     25505400000001010101010101010101
[    13.635] (II) RADEON(0):     0101010101015e358096703814402c1c
[    13.635] (II) RADEON(0):     240058c110000018000000fe004e3135
[    13.635] (II) RADEON(0):     364847452d4542420a20000000fe0043
[    13.635] (II) RADEON(0):     4d4e0a202020202020202020000000fe
[    13.635] (II) RADEON(0):     004e3135364847452d4542420a200039
[    13.635] (II) RADEON(0): Printing probed modes for output eDP
[    13.635] (II) RADEON(0): Modeline "1920x1080"x60.0  136.62  1920 1964 1992 2070  1080 1082 1086 1100 -hsync -vsync (66.0 kHz eP)
[    13.635] (II) RADEON(0): Modeline "1680x1050"x60.0  146.36  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    13.635] (II) RADEON(0): Modeline "1400x1050"x60.0  121.79  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    13.635] (II) RADEON(0): Modeline "1280x1024"x59.9  109.10  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[    13.635] (II) RADEON(0): Modeline "1440x900"x60.0  106.68  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (56.0 kHz)
[    13.635] (II) RADEON(0): Modeline "1280x960"x60.0  101.34  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.8 kHz)
[    13.635] (II) RADEON(0): Modeline "1280x854"x60.0   89.34  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.2 kHz)
[    13.635] (II) RADEON(0): Modeline "1280x800"x60.0   83.71  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.8 kHz)
[    13.635] (II) RADEON(0): Modeline "1280x720"x60.0   74.65  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.9 kHz)
[    13.635] (II) RADEON(0): Modeline "1152x768"x59.9   71.95  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.8 kHz)
[    13.635] (II) RADEON(0): Modeline "1024x768"x59.9   63.53  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    13.635] (II) RADEON(0): Modeline "800x600"x60.0   38.31  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    13.635] (II) RADEON(0): Modeline "848x480"x59.9   31.65  848 872 952 1056  480 483 493 500 -hsync +vsync (30.0 kHz)
[    13.635] (II) RADEON(0): Modeline "720x480"x59.9   26.85  720 744 808 896  480 483 493 500 -hsync +vsync (30.0 kHz)
[    13.635] (II) RADEON(0): Modeline "640x480"x59.9   23.98  640 664 720 800  480 483 487 500 -hsync +vsync (30.0 kHz)
[    13.635] (II) RADEON(0): Output VGA-0 disconnected
[    13.635] (II) RADEON(0): Output HDMI-0 disconnected
[    13.635] (II) RADEON(0): Output eDP connected
[    13.635] (II) RADEON(0): Using exact sizes for initial modes
[    13.635] (II) RADEON(0): Output eDP using initial mode 1920x1080 +0+0
[    13.635] (II) RADEON(0): mem size init: gart size :7fb62000 vram size: s:40000000 visible:f0f5000
[    13.636] (==) RADEON(0): DPI set to (96, 96)
[    13.636] (==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)

```
Why is it computed wrongly?
1920 pix / 344 mm = 142 DPI, not 96 DPI.
Please, how can I set in way, when it will be computed and configured correctly?

---

