---
title: "[mate] Reset screen settings without logout"
date: 2014-09-20
forum: Desktop Environments
---

### Post by Daimoneze on 2014-09-20
Hey all,

I play a Windows game (SWGEmu) in Wine. It runs great, but rather it's fullscreen or not, for some reason part of the game's init sequence appears to involve changing the display's brightness. However, when I close the game, these settings are not reversed, causing my display to be white-washed and saturated. The fix for this is to log out and back in, or restart lightdm via the service command, accomplishing the same. My question is, is there some method to reset or re-init the display settings to whatever they are when the DM/WM starts without logging out? Ideally I would implement such a thing in a script that launches the game then performs this action when the process closes.

TIA!

---

### Post by CantankRus on 2014-09-21
Test xrandr to reset brightness.
Have a look here...
 [http://www.ravikiranj.net/drupal/201307/code/commandline/how-adjust-monitor-brightness-command-line](http://www.ravikiranj.net/drupal/201307/code/commandline/how-adjust-monitor-brightness-command-line)

---

### Post by Daimoneze on 2014-09-21
Alright, this did do it! First I found out the handle for the display:
```
$ xrandr -q
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
LVDS-1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1440x900       59.9*+
   1152x864       60.0  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
DP-1 disconnected (normal left inverted right x axis y axis)
```

Then checked it's brightness:
```
$ xrandr --verbose |grep Brightness
    Brightness: 0.70
```
And with the handle information from the first block (LVDS-1) issue the command to change the brightness.
```
$ xrandr --output LVDS-1 --brightness 0.65
```
Confirmation that this will work came when I ran the game and checked xrandr again. It had set the brightness up to 1.2 and I was able to bump it back down while the game was running.

Note: none of these commands were run as root!

---

