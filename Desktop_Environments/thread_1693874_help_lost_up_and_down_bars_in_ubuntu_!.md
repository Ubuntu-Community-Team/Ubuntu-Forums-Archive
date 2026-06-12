---
title: "help lost up and down bars in ubuntu !"
date: 2011-02-23
forum: Desktop Environments
---

### Post by beickus on 2011-02-23
help lost up and down bars in ubuntu !

this is what i got - 
( type)    xfce4-panel &


[1] 2286
ny104@ny104-laptop:~/Desktop$ 
(xfce4-mixer-plugin:2289): libxfce4mixer-CRITICAL **: xfce_mixer_get_track: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:2289): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_card: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:2289): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_track: assertion `GST_IS_MIXER_TRACK (track)' failed

---

### Post by Krytarik on 2011-02-23
I don't know how to solve the actual issue, but try to just remove the concerned panel item by removing it's respective file in "~/.config/xfce4/panel". This should at least bring you the panels back.

---

