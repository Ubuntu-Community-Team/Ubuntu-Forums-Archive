---
title: "multiple screens not working"
date: 2016-08-28
forum: Desktop Environments
---

### Post by sindi on 2016-08-28
Hi All

I have 4 screens on my pc with on 2 network card nvidia 3 of them working but number 4 not working and when i trying to apply from display sitting this error found ( The selected configuration for displays could not be applied  could not set the configuration for CRTC 64 ) .

So please i need to work on 4 screen  how is that . 


Best Regards

Note:

from this code it's connected

```
xrandr
Screen 0: minimum 320 x 200, current 4310 x 1080, maximum 16384 x 16384
DVI-D-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080     60.00*+  50.00    59.94    24.00    23.98  
   1920x1080i    60.00    50.00    59.94  
   1280x1024     60.02  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
VGA-1 connected 1366x768+1920+0 (normal left inverted right x axis y axis) 410mm x 230mm
   1366x768      59.79*+
   1024x768      75.08    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    60.00  
   720x400       70.08  
DVI-I-1-1 connected 1024x768+3286+0 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
HDMI-1-2 connected
   1920x1080     60.00 +  50.00    59.94    24.00    23.98  
   1920x1080i    60.00    50.00    59.94  
   1280x1024     60.02  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
VGA-1-2 disconnected
  1024x768 (0x45) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x46) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x47) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x49) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
  1920x1080 (0x4a) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1920x1080 (0x4b) 148.500MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  56.25KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  50.00Hz
  1920x1080 (0x4c) 148.352MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.43KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  59.94Hz
  1920x1080i (0x4d) 74.250MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.75KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  60.00Hz
  1920x1080i (0x4e) 74.250MHz +HSync +VSync Interlace
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  28.12KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  50.00Hz
  1920x1080 (0x4f) 74.250MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock  27.00KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  24.00Hz
  1920x1080i (0x50) 74.176MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.72KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  59.94Hz
  1920x1080 (0x51) 74.176MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock  26.97KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  23.98Hz
  1280x1024 (0x52) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x720 (0x53) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1280x720 (0x54) 74.250MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock  37.50KHz
        v: height  720 start  725 end  730 total  750           clock  50.00Hz
  1280x720 (0x55) 74.176MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  44.96KHz
        v: height  720 start  725 end  730 total  750           clock  59.94Hz
  720x576 (0x56) 27.000MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock  31.25KHz
        v: height  576 start  581 end  586 total  625           clock  50.00Hz
  720x480 (0x57) 27.027MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.50KHz
        v: height  480 start  489 end  495 total  525           clock  60.00Hz
  720x480 (0x58) 27.000MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
        v: height  480 start  489 end  495 total  525           clock  59.94Hz
  640x480 (0x59) 25.200MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
        v: height  480 start  490 end  492 total  525           clock  60.00Hz
```

output

```

xrandr --verbose
Screen 0: minimum 320 x 200, current 4310 x 1080, maximum 16384 x 16384
DVI-D-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x9d
    Timestamp:  18299
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    dithering depth: 6 bpc 
        supported: auto, 6 bpc, 8 bpc
    dithering mode: off 
        supported: auto, off, static 2x2, dynamic 2x2, temporal
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    color vibrance: 150 
        range: (0, 200)
    vibrant hue: 90 
        range: (0, 180)
    underscan vborder: 0 
        range: (0, 128)
    underscan hborder: 0 
        range: (0, 128)
    underscan: off 
        supported: auto, off, on
HDMI-1 connected primary 1920x1080+0+0 (0x4a) normal (normal left inverted right x axis y axis) 1600mm x 900mm
    Identifier: 0x9e
    Timestamp:  18299
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff004dd9020901010101
        0114010380a05a780a0dc9a057479827
        12484c21080081800101010101010101
        010101010101023a801871382d40582c
        450040846300001e011d007251d01e20
        6e28550040846300001e000000fc0053
        4f4e592054560a2020202020000000fd
        00303e0e460f000a20202020202001a2
        020329f0501f10140513041211161503
        0207060120230907078301000068030c
        00200080000fe20009023a80d072382d
        40102c458040846300001e011d00bc52
        d01e20b828554040846300001e011d80
        18711c1620582c250040846300009e01
        1d80d0721c1620102c25804084630000
        9e000000000000000000000000000047
    dithering depth: 6 bpc 
        supported: auto, 6 bpc, 8 bpc
    dithering mode: off 
        supported: auto, off, static 2x2, dynamic 2x2, temporal
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    color vibrance: 150 
        range: (0, 200)
    vibrant hue: 90 
        range: (0, 180)
    underscan vborder: 0 
        range: (0, 128)
    underscan hborder: 0 
        range: (0, 128)
    underscan: off 
        supported: auto, off, on
  1920x1080 (0x4a) 148.500MHz +HSync +VSync *current +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1920x1080 (0x4b) 148.500MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  56.25KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  50.00Hz
  1920x1080 (0x4c) 148.352MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.43KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  59.94Hz
  1920x1080i (0x4d) 74.250MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.75KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  60.00Hz
  1920x1080i (0x4e) 74.250MHz +HSync +VSync Interlace
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  28.12KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  50.00Hz
  1920x1080 (0x4f) 74.250MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock  27.00KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  24.00Hz
  1920x1080i (0x50) 74.176MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.72KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  59.94Hz
  1920x1080 (0x51) 74.176MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock  26.97KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  23.98Hz
  1280x1024 (0x52) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x720 (0x53) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1280x720 (0x54) 74.250MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock  37.50KHz
        v: height  720 start  725 end  730 total  750           clock  50.00Hz
  1280x720 (0x55) 74.176MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  44.96KHz
        v: height  720 start  725 end  730 total  750           clock  59.94Hz
  1024x768 (0x45) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x46) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  720x576 (0x56) 27.000MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock  31.25KHz
        v: height  576 start  581 end  586 total  625           clock  50.00Hz
  720x480 (0x57) 27.027MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.50KHz
        v: height  480 start  489 end  495 total  525           clock  60.00Hz
  720x480 (0x58) 27.000MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
        v: height  480 start  489 end  495 total  525           clock  59.94Hz
  640x480 (0x59) 25.200MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
        v: height  480 start  490 end  492 total  525           clock  60.00Hz
  640x480 (0x49) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
VGA-1 connected 1366x768+1920+0 (0xa1) normal (normal left inverted right x axis y axis) 410mm x 230mm
    Identifier: 0x9f
    Timestamp:  18299
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       1
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff004c2d6708414d545a
        0f1701030e2917782afc91a25753a127
        0c5054bfee0001010101010101010101
        010101010101662156aa51001e30468f
        33009ae61000001e000000fd00384b1e
        5109000a202020202020000000fc0053
        4d533139413130300a202020000000ff
        0048344c443430303333340a20200004
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    color vibrance: 150 
        range: (0, 200)
    vibrant hue: 90 
        range: (0, 180)
  1366x768 (0xa1) 85.500MHz +HSync +VSync *current +preferred
        h: width  1366 start 1436 end 1579 total 1792 skew    0 clock  47.71KHz
        v: height  768 start  771 end  774 total  798           clock  59.79Hz
  1024x768 (0xa2) 78.800MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.06KHz
        v: height  768 start  769 end  772 total  800           clock  75.08Hz
  1024x768 (0xa3) 75.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock  56.48KHz
        v: height  768 start  771 end  777 total  806           clock  70.07Hz
  1024x768 (0x45) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  832x624 (0xa4) 57.284MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock  49.73KHz
        v: height  624 start  625 end  628 total  667           clock  74.55Hz
  800x600 (0xa5) 50.000MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock  48.08KHz
        v: height  600 start  637 end  643 total  666           clock  72.19Hz
  800x600 (0xa6) 49.500MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
        v: height  600 start  601 end  604 total  625           clock  75.00Hz
  800x600 (0x46) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x47) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0xa7) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
        v: height  480 start  481 end  484 total  500           clock  75.00Hz
  640x480 (0xa8) 31.500MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock  37.86KHz
        v: height  480 start  489 end  491 total  520           clock  72.81Hz
  640x480 (0xa9) 30.240MHz -HSync -VSync
        h: width   640 start  704 end  768 total  864 skew    0 clock  35.00KHz
        v: height  480 start  483 end  486 total  525           clock  66.67Hz
  640x480 (0x59) 25.200MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
        v: height  480 start  490 end  492 total  525           clock  60.00Hz
  720x400 (0xaa) 28.320MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock  31.47KHz
        v: height  400 start  412 end  414 total  449           clock  70.08Hz
DVI-I-1-1 connected 1024x768+3286+0 (0x45) normal (normal) 0mm x 0mm
    Identifier: 0x41
    Timestamp:  25624
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       4
    CRTCs:      4 5
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    dithering depth: 6 bpc 
        supported: auto, 6 bpc, 8 bpc
    dithering mode: off 
        supported: auto, off, static 2x2, dynamic 2x2, temporal
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    color vibrance: 150 
        range: (0, 200)
    vibrant hue: 90 
        range: (0, 180)
    underscan vborder: 0 
        range: (0, 128)
    underscan hborder: 0 
        range: (0, 128)
    underscan: off 
        supported: auto, off, on
    subconnector: DVI-A 
        supported: Unknown, DVI-D, DVI-A
  1024x768 (0x45) 65.000MHz -HSync -VSync *current
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x46) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x47) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  848x480 (0x48) 33.750MHz +HSync +VSync
        h: width   848 start  864 end  976 total 1088 skew    0 clock  31.02KHz
        v: height  480 start  486 end  494 total  517           clock  60.00Hz
  640x480 (0x49) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
HDMI-1-2 connected (normal)
    Identifier: 0x42
    Timestamp:  25624
    Subpixel:   unknown
    Clones:    
    CRTCs:      4 5
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff004dd9020901010101
        0114010380a05a780a0dc9a057479827
        12484c21080081800101010101010101
        010101010101023a801871382d40582c
        450040846300001e011d007251d01e20
        6e28550040846300001e000000fc0053
        4f4e592054560a2020202020000000fd
        00303e0e460f000a20202020202001a2
        020329f0501f10140513041211161503
        0207060120230907078301000068030c
        00200080000fe20009023a80d072382d
        40102c458040846300001e011d00bc52
        d01e20b828554040846300001e011d80
        18711c1620582c250040846300009e01
        1d80d0721c1620102c25804084630000
        9e000000000000000000000000000047
    dithering depth: 6 bpc 
        supported: auto, 6 bpc, 8 bpc
    dithering mode: off 
        supported: auto, off, static 2x2, dynamic 2x2, temporal
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    color vibrance: 150 
        range: (0, 200)
    vibrant hue: 90 
        range: (0, 180)
    underscan vborder: 0 
        range: (0, 128)
    underscan hborder: 0 
        range: (0, 128)
    underscan: off 
        supported: auto, off, on
  1920x1080 (0x4a) 148.500MHz +HSync +VSync +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1920x1080 (0x4b) 148.500MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  56.25KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  50.00Hz
  1920x1080 (0x4c) 148.352MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.43KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  59.94Hz
  1920x1080i (0x4d) 74.250MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.75KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  60.00Hz
  1920x1080i (0x4e) 74.250MHz +HSync +VSync Interlace
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  28.12KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  50.00Hz
  1920x1080 (0x4f) 74.250MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock  27.00KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  24.00Hz
  1920x1080i (0x50) 74.176MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.72KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  59.94Hz
  1920x1080 (0x51) 74.176MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock  26.97KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  23.98Hz
  1280x1024 (0x52) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x720 (0x53) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1280x720 (0x54) 74.250MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock  37.50KHz
        v: height  720 start  725 end  730 total  750           clock  50.00Hz
  1280x720 (0x55) 74.176MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  44.96KHz
        v: height  720 start  725 end  730 total  750           clock  59.94Hz
  1024x768 (0x45) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x46) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  720x576 (0x56) 27.000MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock  31.25KHz
        v: height  576 start  581 end  586 total  625           clock  50.00Hz
  720x480 (0x57) 27.027MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.50KHz
        v: height  480 start  489 end  495 total  525           clock  60.00Hz
  720x480 (0x58) 27.000MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
        v: height  480 start  489 end  495 total  525           clock  59.94Hz
  640x480 (0x59) 25.200MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
        v: height  480 start  490 end  492 total  525           clock  60.00Hz
  640x480 (0x49) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
VGA-1-2 disconnected (normal)
    Identifier: 0x43
    Timestamp:  25624
    Subpixel:   unknown
    Clones:    
    CRTCs:      4 5
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    scaling mode: None 
        supported: None, Full, Center, Full aspect
    color vibrance: 150 
        range: (0, 200)
    vibrant hue: 90 
        range: (0, 180)
  1024x768 (0x45) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x46) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x47) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x49) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
  1920x1080 (0x4a) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1920x1080 (0x4b) 148.500MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  56.25KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  50.00Hz
  1920x1080 (0x4c) 148.352MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.43KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  59.94Hz
  1920x1080i (0x4d) 74.250MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.75KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  60.00Hz
  1920x1080i (0x4e) 74.250MHz +HSync +VSync Interlace
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock  28.12KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  50.00Hz
  1920x1080 (0x4f) 74.250MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock  27.00KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  24.00Hz
  1920x1080i (0x50) 74.176MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.72KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  59.94Hz
  1920x1080 (0x51) 74.176MHz +HSync +VSync
        h: width  1920 start 2558 end 2602 total 2750 skew    0 clock  26.97KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  23.98Hz
  1280x1024 (0x52) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x720 (0x53) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1280x720 (0x54) 74.250MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock  37.50KHz
        v: height  720 start  725 end  730 total  750           clock  50.00Hz
  1280x720 (0x55) 74.176MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  44.96KHz
        v: height  720 start  725 end  730 total  750           clock  59.94Hz
  720x576 (0x56) 27.000MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock  31.25KHz
        v: height  576 start  581 end  586 total  625           clock  50.00Hz
  720x480 (0x57) 27.027MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.50KHz
        v: height  480 start  489 end  495 total  525           clock  60.00Hz
  720x480 (0x58) 27.000MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock  31.47KHz
        v: height  480 start  489 end  495 total  525           clock  59.94Hz
  640x480 (0x59) 25.200MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.50KHz
        v: height  480 start  490 end  492 total  525           clock  60.00Hz
ubuntu@ubuntu:~$ xrandr --verbose
```

I waiting to install ubuntu if i can fix this all this now from live ubuntu  16.04

---

### Post by sindi on 2016-08-30
Note: I think this problem from Ubuntu because i installed windows and the all display working so the network cards its support 4 monitors .... What about Ubuntu .

Best Regards

---

### Post by sindi on 2016-09-07
No one can help me please 

Best Regards

---

### Post by sindi on 2016-09-21
Up

---

