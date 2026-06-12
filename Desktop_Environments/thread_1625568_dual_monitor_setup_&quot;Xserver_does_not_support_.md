---
title: "dual monitor setup &quot;Xserver does not support the size requested&quot;"
date: 2010-11-19
forum: Desktop Environments
---

### Post by m000 on 2010-11-19
Hello,
I have been using a dual monitor setup with "big desktop" enabled for the last year. My two monitors run on 1600x1200 and 1280x1024 resolutions respectively. My graphics card is an ATI Radeon HD 2400 XT and I use the fglrx driver. My xorg.conf is very simple and is shown later in the post.

My problems began when I upgraded the 1600x1200 monitor and got a full-HD 1920x1080 monitor. In theory I only had to change the Virtual size to 3200 1080 in xorg.conf. 

But when I do that and login I get a "Xserver does not support the size requested" popup and a cloned 1280x1024 display. 

My xorg.conf after changing the Virtual size:
```
Section "Monitor"
        Identifier     "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth 24
        SubSection "Display"
                # Virtual 2880 1200              # old monitor
                Virtual 3200 1080                # new monitor
        EndSubSection
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "fglrx"
EndSection
```
I ran xrandr but it does not detect my monitor correctly neither allows me to add the 1900x1080 mode.

```
user@host:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1440 x 1440
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1400x1050      60.0 +
   1440x900       59.9 +
   1280x720       60.0 +
   1280x1024      75.0     60.0*
   1280x960       75.0     60.0
   1280x800       75.0     60.0
   1152x864       75.0     60.0
   1280x768       74.9     59.9
   1024x768       75.0     60.0
   800x600        75.0     60.3
   720x480        60.0
   640x480        75.0     60.0
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+
   1280x960       60.0
   1280x800       60.0
   1152x864       60.0
   1280x768       59.9
   1280x720       60.0
   1024x768       60.0
   800x600        60.3
   720x480        60.0
   640x480        60.0
TV disconnected (normal left inverted right x axis y axis)

user@host:~$ xrandr --prop
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1440 x 1440
DFP1 disconnected (normal left inverted right x axis y axis)
        SignalFormat:   TMDS
        ConnectorType:  DVI-I
DFP2 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
        EDID_DATA:
                10952d0010952d0010ac67404c364b30
                2814010380331d78ea1d15a059569f27
                0d5054a54b00714f8180d1c001010101
                010101010101023a801871382d40582c
                4500fd1e1100001e000000ff00505430
                5056303954304b364c0a000000fc0044
                454c4c205032333131480a20000000fd
                00384c1e5311000a2020202020200023
        SignalFormat:   TMDS
        ConnectorType:  DVI-I
   1400x1050      60.0 +
   1440x900       59.9 +
   1280x720       60.0 +
   1280x1024      75.0     60.0*
   1280x960       75.0     60.0
   1280x800       75.0     60.0
   1152x864       75.0     60.0
   1280x768       74.9     59.9
   1024x768       75.0     60.0
   800x600        75.0     60.3
   720x480        60.0
   640x480        75.0     60.0
CRT1 disconnected (normal left inverted right x axis y axis)
        SignalFormat:   VGA
        ConnectorType:  DVI-I
CRT2 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
        EDID_DATA:
                f0942d00f0942d004dd9702201010101
                330d01030c221b78eac5c9a3574a9c23
                12484ca1080081808140010101010101
                010101010101302a009851002a403070
                1300520e1100001e000000fd0030411c
                410b000a202020202020000000fc0053
                444d2d485337330a20202020000000ff
                00363238363930340a20202020200066
        SignalFormat:   VGA
        ConnectorType:  DVI-I
   1280x1024      60.0*+
   1280x960       60.0
   1280x800       60.0
   1152x864       60.0
   1280x768       59.9
   1280x720       60.0
   1024x768       60.0
   800x600        60.3
   720x480        60.0
   640x480        60.0
TV disconnected (normal left inverted right x axis y axis)
        SignalFormat:   SVideo
        ConnectorType:  TV-SVideo
        tv_standard: NTSC-M
        tv_vertical_position: 0 (0x00000000)    range:  (-5,5)
        tv_horizontal_position: 0 (0x00000000)  range:  (-5,5)
        tv_horizontal_size: 0 (0x00000000)      range:  (-5,5)

user@host:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
user@host:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
user@host:~$ xrandr --addmode DFP2 "1920x1080_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  33
  Current serial number in output stream:  34
```
More strangely, I created a dual-head setup (an independent desktop on each screen) using aticonfig which works fine. Also, when I disconnect the second monitor, the full-hd monitor is detected correctly and works fine on 1920x1080.

I suspect there is some limitation on the Virtual desktop size. But the information I have found online suggest that my old setup shouldn't work either, so they lack credibility.

I have spent the last couple of days to get the "big desktop" setup working correctly with no results. Any help would be greatly appreciated...

---

