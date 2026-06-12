---
title: "Make active window appear below panel"
date: 2011-06-26
forum: Desktop Environments
---

### Post by Kodeine on 2011-06-26
Salutations!

So I was thinking of having my bottom panel just for harbouring active windows. I thought also to uncheck expand so it will grow larger when more windows are active. All of which is not a problem. But there's one thing stopping me from doing this.

Currently the active window stops when it reaches either panel.
[IMG]http://i.imgur.com/A16I9.png[/IMG] 
[forgot to edit the green bar out. Ops. Ignore it.] So in either bottom corner nothing is displayed. How can I get the active window to go all the way to the bottom of the screen. Whilst the panel still appears above the active window? [Probably won't have transparent panel when doing this.]

Thanks bye!

---

### Post by Krytarik on 2011-06-26
Gnome Panel is not meant to be able to overlay windows statically. The only way to achieve this, is to set the respective panel to autohide, but, unfortunately, that feature doesn't play well with the edge detection of Compiz, meaning it won't unhide if the Gconf key "/apps/panel/toplevels/bottom_panel_screen0/auto_hide_size" is set too low, it begins to work from 3 pixel upwards, but even then it's more hit or miss, because if you move the mouse pointer too far to the edge, it won't affect the panel anymore. So, you have a target area of the value you set there minus 2 pixel at the edge.

Greetings.

---

