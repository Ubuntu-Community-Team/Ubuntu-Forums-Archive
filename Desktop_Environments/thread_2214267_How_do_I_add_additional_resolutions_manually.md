---
title: "How do I add additional resolutions manually?"
date: 2014-03-31
forum: Desktop Environments
---

### Post by menkaur on 2014-03-31
I'm trying to get my new laptop to work with my old tablet - Wacoom PL-550.

  Generally, it works, but ubuntu allows only 1 resolution on my system, which it  1920x1080:  

```
 
xrandr: Failed to get size of gamma for output default
    Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
         default connected primary 1920x1080+0+0 0mm x 0mm
        1920x1080       0.0* 

```  

While this is fine for work, when I try to use it with PL-550, on the tablet the image distortion makes my work hard. 

I've tried several tutorials on how to install Nvidia driver on my laptop, but each time I get unbooteable system.  

Than I've tried this:  

```
 
cvt 1024 768 60     
    # 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz     Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync 
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync     
    xrandr: Failed to get size of gamma for output default 
xrandr --addmode default "1024x768_60.00"     
    xrandr: Failed to get size of gamma for output default 
xrandr --output default --mode 1024x768_60.00     
    xrandr: Failed to get size of gamma for output default     
    xrandr: Configure crtc 0 failed 
xrandr --verbose --output default --mode 1024x768_60.00     
    xrandr: Failed to get size of gamma for output default     
    crtc 0: disable      
    screen 0: 1024x768 200x150 mm 130.01dpi     
    crtc 0: 1024x768_60.00   59.9 +0+0 "default"     
    xrandr: Configure crtc 0 failed     
    crtc 0: disable     
    screen 0: revert     
    crtc 0: revert  
```  


How do I get this to work?

---

