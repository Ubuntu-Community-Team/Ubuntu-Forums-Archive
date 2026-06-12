---
title: "Quake 2 on appears off center.on my screen"
date: 2017-09-02
forum: Gaming &amp; Leisure
---

### Post by ravalox on 2017-09-02
I've just installed Quake 2 on my system and when I run it fullscreen it simply can't seem to frame properly on my screen.  It seems to be trying to use my sessions existing screen resolution; it seems strange it would be locked into my desktops resolution, shouldn't it simply draw at its own resolution in fullscreen?   My laptop has a resolution of 1600 by 900 so I think this is an issue of wide screen but I can't seem to get Yamagi quake to run at that resolution.

---

### Post by again? on 2017-09-10
You can try some of these things that work with my counterstrike install.
I'm using gnome-shell and it appears not to draw where the launcher and panel are until I hit F11 a couple of times.
[ATTACH=CONFIG]276673[/ATTACH]

If I want to play at a lower resolution than the native default of the desktop I check xrandr for available modes.
eg
```
user@GU17:~$ xrandr
Screen 0: minimum 8 x 8, current 1680 x 1050, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050     59.88*+  59.95  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)
```

I then set the game to use one of those modes.
When using lower resolutions the output is stretched to fill the desktop on my machine.

If I want it not to stretch and render with black bars to the side instead, I need to set my 
desktop resolution to the same as the game.
So if I have set my game to use 1024x768, before starting the game I set my desktop to the same with xrandr.
```
xrandr -s 1024x768
```

---

