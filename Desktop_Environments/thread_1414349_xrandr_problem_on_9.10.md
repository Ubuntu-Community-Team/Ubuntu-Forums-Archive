---
title: "xrandr problem on 9.10"
date: 2010-02-23
forum: Desktop Environments
---

### Post by inxcrome on 2010-02-23
hi..

i have a crt monitor connected my laptop and only using that,have some problems with resolution..

firstofall, i dont know its a bug or something but i wanna notice that; for my CRT :  the higher res. is "1024x768" and 3 reflesh rate section (75 - 70 -60) if i choose 75 ubuntu destktop not cover all of my monitor, there is black spaces left and right of the monitor.. in res. 70 its ok! in res. 60 its worst then 75..

i wantta increase the res. and tried to doing follows in that [page]("http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/") and [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)  **but when try to add new mode to xrander, X always crash and need a reset everytime**.. it's crashing also i try to change my laptop's mon res. too..


so how can add upper res values.. and whats the problem about xrandr..


[PHP]
:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 306mm x 230mm
   1024x768       75.1     70.1*    60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
   640x350        70.1  
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)

[/PHP]

---

### Post by inxcrome on 2010-02-24
up..

---

### Post by inxcrome on 2010-02-25
up 2..

---

### Post by inxcrome on 2010-03-01
upper..

---

### Post by MJBoa on 2010-03-01
What drivers are you using? Can't you adjust the screen size through your monitor when you switch to 70 Hz?

---

### Post by efflandt on 2010-03-01
I can tell that your laptop has Intel video chip, but what is the make/model of your CRT or what resolutions/frequencies is it capable of.  For example if it does 1280x1024, start with that mode at 60 hz before trying higher frequencies.  I have seen some 17" CRT's that do not do more that 1024x768.

**cvt 1280 1024**
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

or **gtf 1280 1024 60**
# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

Then see if one of those works (although your things may get big on your laptop screen):

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
xrandr --output VGA1 --mode 1280x1024_60.00

If you want to turn your laptop display off use:

xrandr --output LVDS1 --off

---

### Post by inxcrome on 2010-03-02
@efflandt; i tried but as i said when doing "xrandr --addmode VGA1 1280x1024_60.00
"   both screens goes blackened and freeze.. need to reset etc.etc..etc..

---

