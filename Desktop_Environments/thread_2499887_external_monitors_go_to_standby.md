---
title: "external monitors go to standby"
date: 2024-08-14
forum: Desktop Environments
---

### Post by evenan on 2024-08-14
Not sure where to start

This is an Lenovo thinkpad connected to an usb-c docking station,
connected via DisplayPort to two external monitors.

The monitors go to standby

I have trierd to boot the 6.8.0-39 kernel, but that didn't change anything.

This used to work, I think the only change is updating ubuntu.

Regards,

Even

There is this error in the xorg log not sure if it matters
[COLOR=#3b3b3b][FONT=Droid Sans Mono][COLOR=#3b3b3b][    [/COLOR][COLOR=#0000ff]40[/COLOR][COLOR=#3b3b3b].[/COLOR][COLOR=#0000ff]353[/COLOR][COLOR=#3b3b3b]] ([/COLOR][COLOR=#098658]II[/COLOR][COLOR=#3b3b3b]) NVIDIA([/COLOR][COLOR=#0000ff]0[/COLOR][COLOR=#3b3b3b]): Setting mode [/COLOR][COLOR=#a31515]"DP-4: nvidia-auto-select @3408x2130 +0+0 {Transform=(1.331238,0.000000,0.000000,0.000000,1.331238,0.000000,0.000000,0.000000,1.000000), ViewPortIn=3408x2130, ViewPortOut=2560x1600+0+0, ResamplingMethod=Bilinear}"[/COLOR]
[COLOR=#3b3b3b][    [/COLOR][COLOR=#0000ff]41[/COLOR][COLOR=#3b3b3b].[/COLOR][COLOR=#0000ff]473[/COLOR][COLOR=#3b3b3b]] randr: failed to create shared pixmap[/COLOR]
[COLOR=#3b3b3b][    [/COLOR][COLOR=#0000ff]41[/COLOR][COLOR=#3b3b3b].[/COLOR][COLOR=#0000ff]473[/COLOR][COLOR=#3b3b3b]] failed to add fb -[/COLOR][COLOR=#0000ff]22[/COLOR]
[COLOR=#3b3b3b][    [/COLOR][COLOR=#0000ff]41[/COLOR][COLOR=#3b3b3b].[/COLOR][COLOR=#0000ff]473[/COLOR][COLOR=#3b3b3b]] ([/COLOR][COLOR=#a31515]**EE**[/COLOR][COLOR=#3b3b3b]) modeset(G4): failed to set mode: Invalid argument[/COLOR]
[COLOR=#3b3b3b]

[/COLOR]
[/FONT][/COLOR]


```
uname -a
-> Linux Gunda-44 6.8.0-40-generic #40-Ubuntu SMP PREEMPT_DYNAMIC Fri Jul  5 10:34:03 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

```
```
lspci
->
00:00.0 Host bridge: Intel Corporation Raptor Lake-P 6p+8e cores Host Bridge/DRAM Controller
00:01.0 PCI bridge: Intel Corporation Device a70d
00:04.0 Signal processing controller: Intel Corporation Raptor Lake Dynamic Platform and Thermal Framework Processor Participant
00:06.0 PCI bridge: Intel Corporation Raptor Lake PCIe 4.0 Graphics Port
00:08.0 System peripheral: Intel Corporation GNA Scoring Accelerator module
00:14.0 USB controller: Intel Corporation Alder Lake PCH USB 3.2 xHCI Host Controller (rev 01)
00:14.2 RAM memory: Intel Corporation Alder Lake PCH Shared SRAM (rev 01)
00:14.3 Network controller: Intel Corporation Raptor Lake PCH CNVi WiFi (rev 01)
00:15.0 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #0 (rev 01)
00:15.3 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #3 (rev 01)
00:16.0 Communication controller: Intel Corporation Alder Lake PCH HECI Controller (rev 01)
00:16.3 Serial controller: Intel Corporation Alder Lake AMT SOL Redirection (rev 01)
00:1c.0 PCI bridge: Intel Corporation Device 51b8 (rev 01)
00:1c.7 PCI bridge: Intel Corporation Alder Lake PCH-P PCI Express Root Port #9 (rev 01)
00:1d.0 PCI bridge: Intel Corporation Alder Lake PCI Express Root Port #9 (rev 01)
00:1f.0 ISA bridge: Intel Corporation Raptor Lake LPC/eSPI Controller (rev 01)
00:1f.3 Multimedia audio controller: Intel Corporation Raptor Lake-P/U/H cAVS (rev 01)
00:1f.4 SMBus: Intel Corporation Alder Lake PCH-P SMBus Host Controller (rev 01)
00:1f.5 Serial bus controller: Intel Corporation Alder Lake-P PCH SPI Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation AD107GLM [RTX 2000 Ada Generation Laptop GPU] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 22be (rev a1)
06:00.0 Non-Volatile memory controller: KIOXIA Corporation NVMe SSD Controller XG8 (rev 01)
0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5261 PCI Express Card Reader (rev 01)
20:00.0 PCI bridge: Intel Corporation Thunderbolt 4 Bridge [Maple Ridge 4C 2020] (rev 02)
21:00.0 PCI bridge: Intel Corporation Thunderbolt 4 Bridge [Maple Ridge 4C 2020] (rev 02)
21:01.0 PCI bridge: Intel Corporation Thunderbolt 4 Bridge [Maple Ridge 4C 2020] (rev 02)
21:02.0 PCI bridge: Intel Corporation Thunderbolt 4 Bridge [Maple Ridge 4C 2020] (rev 02)
21:03.0 PCI bridge: Intel Corporation Thunderbolt 4 Bridge [Maple Ridge 4C 2020] (rev 02)
22:00.0 USB controller: Intel Corporation Thunderbolt 4 NHI [Maple Ridge 4C 2020]
48:00.0 USB controller: Intel Corporation Thunderbolt 4 USB Controller [Maple Ridge 4C 2020]



```

---

### Post by evenan on 2024-08-14
Added xrandr --verbose output


```
$ xrandr --verbose
Screen 0: minimum 8 x 8, current 2560 x 1600, maximum 32767 x 32767
DP-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x21c
    Timestamp:  2582382
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
        0 1 
    CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: DisplayPort 
    ConnectorNumber: 0 
    _ConnectorLocation: 0 
    non-desktop: 0 
        supported: 0, 1
DP-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x21d
    Timestamp:  2582382
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
        0 1 
    CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: DisplayPort 
        supported: DisplayPort
    ConnectorType: DisplayPort 
    ConnectorNumber: 0 
    _ConnectorLocation: 0 
    non-desktop: 0 
        supported: 0, 1
DP-2 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x21e
    Timestamp:  2582382
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
        0 1 
    CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: DisplayPort 
    ConnectorNumber: 1 
    _ConnectorLocation: 1 
    non-desktop: 0 
        supported: 0, 1
DP-3 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x21f
    Timestamp:  2582382
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
        0 1 
    CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: DisplayPort 
        supported: DisplayPort
    ConnectorType: DisplayPort 
    ConnectorNumber: 1 
    _ConnectorLocation: 1 
    non-desktop: 0 
        supported: 0, 1
HDMI-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x220
    Timestamp:  2582382
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
        0 1 
    CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: HDMI 
    ConnectorNumber: 2 
    _ConnectorLocation: 2 
    non-desktop: 0 
        supported: 0, 1
DP-4 connected primary 2560x1600+0+0 (0x222) normal (normal left inverted right x axis y axis) 344mm x 215mm
    Identifier: 0x221
    Timestamp:  2582382
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
    _MUTTER_PRESENTATION_OUTPUT: 0 
    CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
        0 1 
    CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
    Backlight: 100 
        range: (0, 100)
    EDID: 
        00ffffffffffff0009e5e00a00000000
        2c1f0104b5221578037ce5a4554c9f26
        0f505400000001010101010101010101
        0101010101016b6e00a0a04084603020
        360058d71000001a000000fd0c3ca51f
        1f4e010a202020202020000000fe0042
        4f452043510a202020202020000000fe
        004e4531363051444d2d4e59310a0180
        7013790000030114a52f0185ff099f00
        2f001f003f0683000200050000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000003e90
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: DisplayPort 
        supported: DisplayPort
    ConnectorType: Panel 
    ConnectorNumber: 3 
    _ConnectorLocation: 3 
    non-desktop: 0 
        supported: 0, 1
  2560x1600 (0x222) 282.670MHz +HSync -VSync *current +preferred
        h: width  2560 start 2608 end 2640 total 2720 skew    0 clock 103.92KHz
        v: height 1600 start 1603 end 1609 total 1732           clock  60.00Hz
  2560x1600 (0x223) 777.340MHz -HSync -VSync
        h: width  2560 start 2608 end 2640 total 2720 skew    0 clock 285.79KHz
        v: height 1600 start 1603 end 1609 total 1732           clock 165.00Hz
None-5-1 connected (normal left inverted right x axis y axis)
    Identifier: 0x2c7
    Timestamp:  37596
    Subpixel:   unknown
    Clones:    
    CRTCs:      4
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    _MUTTER_PRESENTATION_OUTPUT: 0 
    PRIME Synchronization: 1 
        supported: 0, 1
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 35 
        supported: 35
    non-desktop: 0 
        range: (0, 1)
  2560x1600 (0x2c9) 245.760MHz +preferred
        h: width  2560 start 2560 end 2560 total 2560 skew    0 clock  96.00KHz
        v: height 1600 start 1600 end 1600 total 1600           clock  60.00Hz
DVI-I-4-4 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x2a6
    Timestamp:  37596
    Subpixel:   unknown
    Clones:    
    CRTCs:      5
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    PRIME Synchronization: 1 
        supported: 0, 1
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 37 
        supported: 37
    non-desktop: 0 
        range: (0, 1)
DVI-I-3-3 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x285
    Timestamp:  37596
    Subpixel:   unknown
    Clones:    
    CRTCs:      6
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    PRIME Synchronization: 1 
        supported: 0, 1
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 37 
        supported: 37
    non-desktop: 0 
        range: (0, 1)
DVI-I-2-2 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x264
    Timestamp:  37596
    Subpixel:   unknown
    Clones:    
    CRTCs:      7
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    PRIME Synchronization: 1 
        supported: 0, 1
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 37 
        supported: 37
    non-desktop: 0 
        range: (0, 1)
DVI-I-1-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x243
    Timestamp:  37596
    Subpixel:   unknown
    Clones:    
    CRTCs:      8
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    PRIME Synchronization: 1 
        supported: 0, 1
    link-status: Good 
        supported: Good, Bad
    CONNECTOR_ID: 37 
        supported: 37
    non-desktop: 0 
        range: (0, 1)


```

---

### Post by evenan on 2024-08-17
Works now. not sure why

At one point I did sign the dkms driver.

Tried the 0.1.28 fwdriver -> didn't work, so had to go back to 0.1.20
(This is a Lenovo thinkpad P1-Gen6)

$ lsusb -d 17e9:    -> returns nothing

$ dkms status
evdi/1.14.4, 6.8.0-40-generic, x86_64: installed
virtualbox/7.0.16, 6.8.0-39-generic, x86_64: installed
virtualbox/7.0.16, 6.8.0-40-generic, x86_64: installed

$ sudo systemctl status displaylink-driver
&#9675; displaylink-driver.service - DisplayLink Driver Service
     Loaded: loaded (/usr/lib/systemd/system/displaylink-driver.service; static)
     Active: inactive (dead)


$ xrandr
Screen 0: minimum 8 x 8, current 13648 x 2880, maximum 32767 x 32767
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-4 connected primary 3408x2130+0+750 (normal left inverted right x axis y axis) 344mm x 215mm
   2560x1600     60.00*+ 165.00  
DP-3.2 connected 5120x2880+8528+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440     60.00*+ 180.00   170.00   165.00   144.00   120.00  
   1920x1080    119.88    60.00    59.94    50.00  
   1280x1440     59.91  
   1280x1024     75.02    60.02  
   1280x720      59.94    50.00  
   1024x768     119.99    99.97    75.03    70.07    60.00  
   800x600      119.97    99.66    75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480      119.52    99.77    75.00    72.81    59.94    59.93  
DP-3.3 connected 5120x2880+3408+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440     60.00*+ 180.00   170.00   165.00   144.00   120.00  
   1920x1080    119.88    60.00    59.94    50.00  
   1280x1440     59.91  
   1280x1024     75.02    60.02  
   1280x720      59.94    50.00  
   1024x768     119.99    99.97    75.03    70.07    60.00  
   800x600      119.97    99.66    75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480      119.52    99.77    75.00    72.81    59.94    59.93  
DVI-I-4-4 disconnected (normal left inverted right x axis y axis)
DVI-I-3-3 disconnected (normal left inverted right x axis y axis)
DVI-I-2-2 disconnected (normal left inverted right x axis y axis)
DVI-I-1-1 disconnected (normal left inverted right x axis y axis)
None-5-1 connected (normal left inverted right x axis y axis)
   2560x1600     60.00 +

$ sudo lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 27c6:6594 Shenzhen Goodix Technology Co.,Ltd. Goodix USB2.0 MISC
Bus 001 Device 004: ID 04f2:b74f Chicony Electronics Co., Ltd Integrated Camera
Bus 001 Device 005: ID 8087:0033 Intel Corp. AX211 Bluetooth
Bus 001 Device 006: ID 17ef:30af Lenovo USB2.0 Hub
Bus 001 Device 007: ID 17ef:30ac Lenovo USB2.0 Hub             
Bus 001 Device 008: ID 17ef:30a9 Lenovo 40AY
Bus 001 Device 009: ID 17ef:30b0 Lenovo ThinkPad USB-C Dock Audio
Bus 001 Device 010: ID 17ef:30ae Lenovo USB2.0 Hub             
Bus 001 Device 011: ID 046d:0a8f Logitech, Inc. H390 headset with microphone
Bus 001 Device 012: ID 04e8:61fb Samsung Electronics Co., Ltd PSSD T7 Shield
Bus 001 Device 013: ID 17ef:609b Lenovo Professional Wireless Keyboard and Mouse Combo
Bus 001 Device 014: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 002: ID 17ef:30ab Lenovo USB3.1 Hub             
Bus 004 Device 003: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
Bus 004 Device 004: ID 17ef:30ad Lenovo USB3.1 Hub             

Even

---

