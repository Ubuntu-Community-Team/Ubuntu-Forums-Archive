---
title: "Couple of problems"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by Nigmah on 2007-07-23
[COLOR=DarkOrange][B]OK first thing is I was having problems whenever i logged into xgl having no restart or shutdown buttons i fixed this by changing my startxgl.sh

From 
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

to:
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session

except now all my buttons and such look like im running windows 98 or os 9 which is really annoying.

Also i've tried multiple times to get my side buttons on my intellimouse 2.0(yes i've had it for a long time) but i can't get it to work here my xorg.conf looks like for my mouse
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "6 7"
        Option          "Resolution"            "100"
EndSection

also soon i'm going to be buying and installing the 8800 gts on my computer anything i should know before i do that(yea i know its not quite on topic)

[/B][/COLOR]

---

