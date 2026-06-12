---
title: "Display Settings with HDTV"
date: 2010-01-17
forum: Desktop Environments
---

### Post by puffball8963 on 2010-01-17
Hi guys im fairly new to linux but im trying to run a samsung full hdtv as my monitor and of course linux does not natively detect it. Every display setting I change to cuts off a new part of the screen. Is there anything to do to correct this problem Im running the 9.10 btw.

---

### Post by efflandt on 2010-01-17
It depends how your HDTV is connected.  DVI or HDMI are digital, and the display should communicate to the video source what resolutions it is capable of.

But VGA apparently may not really know what resolutions the display is capable of even with pnp (plug and pray).  For example X on my laptop VGA recognizes that my HDTV is 40", yet it defaults to 1024x768 which ends up stretched horizontally.  It has no clue that it is natively 1366x768.  Although WinXP seems to think it is 1360x764 and that is close enough to be sharp.

X offers a 1280x720 which you would think would be 720p widescreen mode, but that ends up overscanned, so I cannot even see the top menu bar and my HDTV cannot autosync or even manually sync to whatever that is.  That may be because my laptop display is 1280x800.

See [https://wiki.ubuntu.com/X/Config/Resolution?highlight=%28X%29|%28modelines%29]("https://wiki.ubuntu.com/X/Config/Resolution?highlight=%28X%29%7C%28modelines%29") (although I am not sure if that is up to date for 9.10), and in a terminal do **man xrandr**.

For some reason **cvt 1366 768** comes up with a 1368x768 mode, and I had to go down to 1360 to get any less than 1368, but experiment and see what works best for you.  Following is an example that worked for my laptop (note "$" indicates a prompt for a commandline, do not type the dollar sign):

```
$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 890mm x 500mm
   1280x720       60.0 +
   1024x768       75.1     70.1     60.0* 
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       60.1 +
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)

$ cvt 1360 768
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

$ xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync

$ xrandr --addmode VGA1 1360x768_60.00

$ xrandr --output VGA1 --mode 1360x768_60.00
```If you mess up or want to try something different, just log out of X and log back in.  Once you determine what works best, the link above gives ways to make that automatic.

PS: Looking through /var/log/xorg.0.log I found that through VGA it does recognize my display as model FLM-4034B and EDID for that lists a 1360x765 mode (maybe why WinXP worked well using 1360x764).  But when checking standard video modes for my card it lists 1360x768x60 as "monitor does not support reduced blanking" and "exceeds panel dimensions" (maybe for laptop display?), so it does not include that in available modes.  cvt 1360 765 returns a 1360x765_60.00 modeline that works perfectly with xrandr (sharp fonts).

---

