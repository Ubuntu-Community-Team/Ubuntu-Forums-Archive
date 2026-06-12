---
title: "Incorrectly drawn background on dual monitor using Lightdm xrandr xubuntu 14.04"
date: 2014-04-24
forum: Desktop Environments
---

### Post by pavel8 on 2014-04-24
Hi,

I have LCD panel connected to my notebook. The background in greeter is drawn  on external monitor in the upper left corner and it looks like it is the same size as on the notebook LCD.
[ATTACH=CONFIG]252466[/ATTACH]

I am running a fresh xubuntu 14.04 with xrandr script
 
```

#!/bin/bash

#Runs the xrandr when the session is started - this script is stardet via lightdm

xrandr | grep HDMI1 | grep " connected "
if [ $? -eq 0 ]; then
    # External monitor is connected
    xrandr --output HDMI1 --primary --mode 1920x1200 --pos 0x0 --rotate normal --output LVDS1 --mode 1366x768 --pos 1920x432 --rotate normal
    if [ $? -ne 0 ]; then
        # Something went wrong. Autoconfigure the internal monitor and disable the external one
        xrandr --output LVDS1 --auto --output HDMI1 --off
    fi
else
    # External monitor is not connected
    xrandr --output LVDS1 --auto --output HDMI1 --off
fi


```

called by lightdm's

```

[SeatDefaults]
greeter-setup-script="/home/user/.screenlayout/run_xrandr.sh"

```

which is configured in /usr/share/lightdm/lightdm.conf.d/70-xrandr.conf.

Well, the resolution of both screens seems to be ok but the size of background image on the external LCD is wrong (the resolution of that background image is much bigger then resolution of the LCD). Interestingly this did work on xubuntu 12.04.

Does anybody else deal with similar problem? Any suggestion how to make the lightdm+xrandr draw background correctly? Thank You.

Pavel

---

### Post by ruben9 on 2014-04-30
I am having the same issue.

Additionally, my background image disappears on both my laptop monitor and my external monitor when I unplug the external monitor.  Background turns black and stays that way after connecting the external monitor again.
Backgrounds also disappear when I go to the display settings and try to change the background image.

---

### Post by pavel8 on 2014-04-30
I have reported it as a bug on lightmd's launchpad ([https://bugs.launchpad.net/lightdm/+bug/1314603](https://bugs.launchpad.net/lightdm/+bug/1314603)). Similar behaviour is also reported on debian forum ([http://forums.debian.net/viewtopic.php?f=5&t=113632](http://forums.debian.net/viewtopic.php?f=5&t=113632)).

---

### Post by pavel8 on 2014-06-29
Well, there is solution: use the updated lightdm-gtk-greater by Andrew P. [https://launchpad.net/~kalgasnik/+archive/lightdm-gtk-greeter-background](https://launchpad.net/~kalgasnik/+archive/lightdm-gtk-greeter-background) 

It works for me.

Pavel

---

