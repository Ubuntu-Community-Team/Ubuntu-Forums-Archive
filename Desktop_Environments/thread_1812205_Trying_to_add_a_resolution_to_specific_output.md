---
title: "Trying to add a resolution to specific output"
date: 2011-07-26
forum: Desktop Environments
---

### Post by blbuford on 2011-07-26
hello all,

I just installed 11.04 on my PC. I use my TV as my monitor because I use this machine to stream from Hulu, Netflicks or Icefilms. Ubuntu does not detect the resolution I want to use, which is 1152x648. An odd ball res I know, but everything fits best on that setting and I'm not concerned with HD. 
this is what I've tried so far:

$ xrandr --addmode DVI-0  1152x648
xrandr: cannot find mode "1152x648"

i then tried:
$ xrandr --newmode "1152x648_60.00"   59.25  1152 1200 1312 1472  648 651 656 674 -hsync +vsync
then:
$ xrandr --output DVI-0 --mode 1152x648
and it returned:
xrandr: cannot find mode 1152x648

I checked my work by entering xrandr and  the mode I added was in the s video  settings but not available for the DVI-0 monitor.

How would I go about adding this resolution to the DVI-0 output? 
Below I pasted what prints out when I input xrandr...not sure if it will help diagnose my error.

thanks in advance 
-brett



$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
DVI-0 connected 1280x720+0+0 (normal left inverted right x axis y axis) 698mm x 392mm
   1280x720       60.0*+
   1920x1080      60.0  
   1920x1080i     30.0  
S-video disconnected (normal left inverted right x axis y axis)
  1152x648_60.00 (0x16f)   59.2MHz
        h: width  1152 start 1200 end 1312 total 1472 skew    0 clock   40.3KHz
        v: height  648 start  651 end  656 total  674           clock   59.7Hz

---

