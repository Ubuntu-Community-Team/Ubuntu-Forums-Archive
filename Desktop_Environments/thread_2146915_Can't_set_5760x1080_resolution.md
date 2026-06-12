---
title: "Can't set 5760x1080 resolution"
date: 2013-05-20
forum: Desktop Environments
---

### Post by xinform3n on 2013-05-20
Hello,

First of all, thanks for your time.

_*In short:*_

I can't set 5760x1080 resolution on my Ubuntu 13.04.
I don't see this resolution in the display settings tools.
I have tried this CLI procedure without succes:

```
sudo xrandr --newmode "5760x1080" 424.75  5760 6088 6696 7632  1080 1083 1093 1114 -hsync +vsync
sudo xrandr --addmode DVI-I-3 5760x1080
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32
```

_*Long story:*_

I'm using Ubuntu 13.04 since a short time in dual boot with Windows 7.
I've recently upgraded my old display settings with a new one, but I can't use the appropriate resolution.[INDENT]*old display settings:*
[/INDENT]
[INDENT]Three 1280x1024 display connected to a Matrox TripleHead2GO connected to a Nvidia 480GTX (TH2GO emulate a screen of 3840x1024).

[/INDENT]
[INDENT]*new display settings:*
[/INDENT]
[INDENT]Three 1920x1080 display connected to a Matrox TripleHead2GO connected to a Nvidia 480GTX(TH2GO emulate a screen of 5760x1080).[/INDENT]
 
After the hardware change, I don't see the new resolution in the display settings GUI.
I have tried to boot with Windows 7, I can set the new resolution, so it isn't a hardware issue.

I have tried to configure manualy the resolution:

```
cvt 5760 1080 50
# 5760x1080 49.96 Hz (CVT) hsync: 55.65 kHz; pclk: 424.75 MHz
Modeline "5760x1080_50.00"  424.75  5760 6088 6696 7632  1080 1083 1093 1114 -hsync +vsync

sudo xrandr --newmode "5760x1080" 424.75  5760 6088 6696 7632  1080 1083 1093 1114 -hsync +vsync

xrandr
Screen 0: minimum 8 x 8, current 3840 x 1024, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-I-3 connected 3840x1024+0+0 (normal left inverted right x axis y axis) 1082mm x 288mm
   3840x1024      60.0*+
   3072x768       60.0  
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
  5760x1080 (0x2b9)  424.8MHz
        h: width  5760 start 6088 end 6696 total 7632 skew    0 clock   55.7KHz
        v: height 1080 start 1083 end 1093 total 1114           clock   50.0Hz

sudo xrandr --addmode DVI-I-3 5760x1080
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32
```

When I try to apply the new mod to the screen, I've got this error and I don't find a way to understand it.
Any pointers ? Is this a bug ? Is this a hard limit ?

Original post on askubuntu.com [here]("http://askubuntu.com/questions/297246/how-to-manually-set-a-special-resolution")

---

### Post by dino99 on 2013-05-20
i have no experience with the matrox hardware, but i suppose you might use the latest nvidia driver (319) from that ppa: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

also glance at your logs: .xsession-errors and /var/log/dmesg & /var/log/xorg0.log

Matrox have listed compatible OS, but Linux is ignored (even if osx is present) so maybe linux is missing some driver module

---

### Post by xinform3n on 2013-05-22
Thank you for this good idea !
I have tried the Nvidia drivers 319, but unfortunately it doesn't work better.

Always the same error with xrandr:
```
sudo xrandr --addmode DVI-I-3 5760x1080
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32
```

How can I read this error ?

---

### Post by S_Barkdull on 2013-08-13
You may want to run Matrox's Compatability checker to see what resolutions are supported by your hardware. You can get the checker here:

[http://www.matrox.com/graphics/en/support/compatibility/gxm/home/](http://www.matrox.com/graphics/en/support/compatibility/gxm/home/)

It is possible that your Nvidia hardware does not support 5760x1080 (aka 3 x 1920x1080)

---

### Post by 1clue on 2013-08-13
Try putting them in other configurations to see if it's a problem with 5760 width.

I'm running dual monitors one over the other.  I think the smallest square would be 3 vertically oriented monitors, or if you physically turn each monitor sideways and put the 3 side by side.

---

