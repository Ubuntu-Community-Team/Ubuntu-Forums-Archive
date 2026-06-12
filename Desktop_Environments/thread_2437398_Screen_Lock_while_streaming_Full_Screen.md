---
title: "Screen Lock while streaming Full Screen"
date: 2020-02-23
forum: Desktop Environments
---

### Post by charlbur on 2020-02-23
Hi, I am having a problem with my Xubuntu 19.10 where the screen saver enables and locks the screen 5 minutes after you start streaming in full screen mode.  5 minutes is the time set for my screen saver to activate.

On the Xfce Reddit forum a setting in the screen saver settings window was mentioned to "[COLOR=#1A1A1B][FONT=&quot]not to activate while a window is in fullscreen mode".  I have looked in the Xubuntu 19.10 screen saver settings and this setting is not displayed.  

Is there another way to stop the screen saver from being activated and the screen locking while streaming in full screen? Thanks

**System Details:**
[/FONT][/COLOR]Kernel: 5.3.0-40-generic x86_64 
bits: 64 
Desktop: Xfce 4.14.1 
Distro: Ubuntu 19.10 (Eoan Ermine)
Device-1: Intel 3rd Gen Core processor Graphics 
driver: i915 
v: kernel 
Display: x11 
server: X.Org 1.20.7 
driver: modesetting

---

### Post by him610 on 2020-02-23
Don't know about screensaver settings.
You could try this to see if works for you 
Settings>Power Manager: 
tab System, push the 'When inactive for' slider all the way to the left (Never); 
tab Display, push the 'Blank after' slider all the way to the left (Never)

---

### Post by TheFu on 2020-02-23
I use this:
$ more ~/bin/blank_screen.sh 
```
#!/bin/bash

# ###########################################################
while getopts 'yn' OPTION
do
  case $OPTION in
  y)    xset s off &
        xset -dpms &
        xscreensaver-command -exit
        echo "Screen Blanking Disabled"
        ;;
  n)   xset +dpms &
       xset s on &
       xscreensaver &
       xscreensaver-command -activate
       echo "Screen Blanking Enabled"
        ;;
  esac
done
```
But I'm not runnng XFCE.  Using fvwm here. Perhaps something similar would work there?

---

### Post by Holger_Gehrke on 2020-02-23
On my laptop with XUbuntu 18.04 there's an icon for the power-manager in the notification-area. A right-click on that icon gives a context-menu offering 'Presentation-Mode' which inhibits known screen-savers / screen-lockers. The icon can be activated in the settings of the power-manager. Another way to activate presentation-mode is using xfconf-query.
```

#presentation mode on:
xfconf-query --channel xfce4-power-manager --property /xfce4-power-manager/presentation-mode --set true
#presentation mode off:
xfconf-query --channel xfce4-power-manager --property /xfce4-power-manager/presentation-mode --set false

```

Holger

---

### Post by him610 on 2020-02-23
Thought I would investigate this thread. This is applicable to Xubuntu 20.04, 
Settings>Screensaver, tab Screensaver, top left Enable Screensaver, top right slider to enable/disable
There are a couple of other controls at the bottom if one decides to leave the Screensaver enabled. 
Refer to attachment. 
It works; I tried it on another computer.

---

### Post by charlbur on 2020-02-24
Thanks for all the answers, I must of had an "idiot" moment](*,) and not scrolled down far enough on the Screen Saver settings screen.  I looked again and scrolled down all the way this time, miraculously there the setting was.  I am not sure why I didn't notice it the first time round but thanks to all :oops:.

@[COLOR=#000000]Holger_Gehrke, [/COLOR]I like the presentation mode option and will also try that in future.

---

### Post by TheFu on 2020-02-24
If you do presentations, please consider setting up a different userid just for that purpose.  Don't connect the userid to anything that will have notifications.

---

