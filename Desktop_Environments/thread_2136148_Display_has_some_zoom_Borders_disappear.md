---
title: "Display has some zoom? Borders disappear?"
date: 2013-04-16
forum: Desktop Environments
---

### Post by hirscherne on 2013-04-16
Hello,

I've just plugged in my monitor (a Samsung XL2370) after moving but there is some strange zoom effect that seems to have moved the menu bars (as well as dash) off-screen:

[[IMG]http://farm9.staticflickr.com/8118/8656067250_76cd61f73b.jpg[/IMG]]("http://www.flickr.com/photos/germanium/8656067250/")

You can see that the menu appears to start somewhere off the screen.

The resolution is the screen's native 1920x1080, according to xrandr

```

$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```

Is there any zoom that's causing this? How can I reset my monitor settings so that it's all sharp and crisp again?

Thank you!

---

### Post by hirscherne on 2013-04-17
Anybody? This is really weird...

---

### Post by hirscherne on 2013-04-17
I solved this. My monitor has a 4:3, a 16:9 and a user-defined setting. For some reason, 16:9 was selected.

---

