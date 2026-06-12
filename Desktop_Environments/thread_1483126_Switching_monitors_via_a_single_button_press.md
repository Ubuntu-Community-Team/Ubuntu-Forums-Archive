---
title: "Switching monitors via a single button press?"
date: 2010-05-14
forum: Desktop Environments
---

### Post by Wintersdark on 2010-05-14
I've installed ubuntu 10.4 on my wife's laptop. She's loving it so far, but we've run into a sticky spot.  Not too big of a deal, but annoying.

She loves Compiz effects (largely, transparency and the desktop cube deal), and they work great.

However, we also use this laptop with our HDTV as a media center.  We can connect it to our TV easily enough, but if we mirror screens we're locked at 1024x768, which looks terrible on both the lappy's native 1280x800 and the TV's native 1920x1080.  If we extend the desktop, we can use both resolutions as needed but compiz/emerald (desktop effects) turn off and all our settings are lost so when we re-enable desktop effects, they all revert to the default settings, so I've got to spend the next 10-15 minutes setting everything back the way the wife likes them.

We don't have this problem if we disable one and enable the other, but this is kind of a pain in the ***: open destop settings, disable one monitor, enable the other, ensure TV is on and set to the right source to click the "keep these settings" box before it reverts, and repeat.

Assuming there's no way to force Compiz to play nice on both screens (at their native resolutions) simultaneously, can someone offer some advice on setting up, say, a script I can use to toggle between the two displays so the wifey can just click a button to change?  She gets edgy around the display settings dialogs, as a misclick can cause a lot of problems.  

xrandr -q says:
```


drea@sarah:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA-0 connected (normal left inverted right x axis y axis)
   1920x1080      59.9 +
   1280x1024      75.0     60.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  

```

LVDS is the laptop display, VGA-0 is the HDTV.

---

