---
title: "Full VGA Monitor Resolution"
date: 2010-03-26
forum: Desktop Environments
---

### Post by noobie1234 on 2010-03-26
Hello
I am running ubuntu 10.04 and cannot set my 19" VGA monitor to it's full resolution.  I also have a monitor connected by DVI.

The supported resolution of the 19" is 1280x1024 at 60khz but that option is not available in System -> Preferences -> Monitors.

I have tried to follow a tutorial on cvt and xrandr but i get the following terminal output:
> richard@richard-desktop:~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

richard@richard-desktop:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  29
  Current serial number in output stream:  29
Any help appreciated
noobie1234

---

### Post by gordintoronto on 2010-03-26
Google "nomodeset" to find threads where it is used to solve your problem.

By the way, you are running a test version of Ubuntu, and you should expect it to break. You would be much better off using 9.10, which is the current version of Ubuntu.

A note: VGA resolution is actually 640x480, and it was exciting stuff in 1985.

---

