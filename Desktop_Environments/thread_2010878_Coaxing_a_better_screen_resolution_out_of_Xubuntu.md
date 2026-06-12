---
title: "Coaxing a better screen resolution out of Xubuntu"
date: 2012-06-26
forum: Desktop Environments
---

### Post by cyningstan on 2012-06-26
I am using Xubuntu on an old machine connected to a small widescreen TV that has a VGA input.  It is happily using 1024x768, but given that it's widescreen, I'd like to try and get a widescreen mode working - ANY reasonable widescreen mode from 1024x600 upwards.

The detail: this is a home-built machine with a Voodoo Banshee 3 16Mb graphics card supporting resolutions up to 1900x1440.  I can't find a comprehensive mode list for it.  The "monitor" is an Evotel 16" ELED16L5HD with VGA input, supporting 1360x768 at 60Hz.  I'm running Xubuntu 12.04.

What I've tried:

1. Just changing the resolution with Settings -> Settings Manager -> Display.  1024x768 is the highest shown, and the only widescreen mode is 680x384.

2. Creating an Xorg.conf of my own, intending to stuff ModeLines in it and experiment.  But even before putting any ModeLines in there, the default Xorg.conf gives me a black screen on running startx with the appropriate -config parameter.  So I've put this solution aside for the moment.

3. Playing with xrandr.  Before playing, it gave the following output:
```
nero:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1280 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       60.0* 
   800x600        60.0     56.0  
   640x480        60.0  
   680x384        60.0  
   512x384        60.0  
   400x300        60.0     56.0  
   320x240        60.0  

```On adding a modeline
```
nero:~$ xrandr --newmode "1360x768_60.00" 84.72 1360 1424 1568 1776 768 769 772 795 -HSync +Vsync:
xrandr: Failed to get size of gamma for output default
nero:~$ xrandr --addmode default 1360x768_60.00
xrandr: Failed to get size of gamma for output default
nero:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1360 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       60.0* 
   800x600        60.0     56.0  
   640x480        60.0  
   680x384        60.0  
   512x384        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
   1360x768_60.00   60.0  

```After manually adding the 1360x768 modeline I found in a modeline list:
```
nero:~$ xrandr --output default --mode 1360x768_60.00xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
```

I'm not sure where to go after this, or what else to look for.  Can anyone please point me in the right direction?

---

