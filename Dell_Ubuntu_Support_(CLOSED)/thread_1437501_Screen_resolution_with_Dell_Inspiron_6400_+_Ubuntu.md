---
title: "Screen resolution with Dell Inspiron 6400 + Ubuntu 9.10"
date: 2010-03-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ntekupal on 2010-03-24
Hi,

I have been struggling since weeks to set my screen resolution on Dell Inspiron 6400 15.4" WXGA with ubuntu 9.10 installed. Ofcourse, I searched on forums and people could not even get to 1280x800. But mine luckily showing 1280x800 resolution with 60Hz refresh rate but for some reason the screen looks still blurred. Not a sharp image I would see with Ubuntu 9.10 as it used to be with Windows XP earlier.I am not sure what resolution I used to have for Windows-XP. I tried using xrandr to change the resolution to 1280x1024 but not much luck. Here is the log what I tried with xrandr

**[COLOR="Red"]raj@raj-laptop:~$ xrandr[/COLOR]**
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)
**[COLOR="Red"]raj@raj-laptop:~$ cvt 1280 1024[/COLOR]**
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
[B][COLOR="Red"]raj@raj-laptop:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
[/COLOR][/B]**[COLOR="Red"]raj@raj-laptop:~$ xrandr --addmode LVDS1 1280x1024_60.00[/COLOR]**
[B]X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26[/B]

Is any one having similar issue ?
Expertise please throw some light on this issue.

[I]I am so fed up with all these simple things in Ubuntu, which makes me miss Windows now. Looks like if I cannot get around with the screen resolution then probably Windows is the only option I guess.
[/I]

Thanks in  advance.
Raj.

---

### Post by ntekupal on 2010-03-24
Beep........Beep.....

---

