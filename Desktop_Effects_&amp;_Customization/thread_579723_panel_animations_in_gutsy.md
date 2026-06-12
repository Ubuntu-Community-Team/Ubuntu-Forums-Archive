---
title: "panel animations in gutsy"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by kryysler on 2007-10-18
Hi,
i installed gutsy today and i'm having a little problem with that icon animation in the gnome-panel. I am talking about that animation, that even in metacity, comes up when you click in any icon on the gnome-panel. It is like a border that starts rising until it fills the screen. It's really annoying so if any one has a solution it would be great. 
Oh, i've already tried to gconf-editor -> apps -> panel -> global. Uncheck enable animations.  Don't seem to find any option in gconf that works.

---

### Post by kryysler on 2007-10-18
come on guys, somebody got to have an idea. share your knowledge.

---

### Post by kryysler on 2007-10-19
this is unbelivable, no one has anything to say..

---

### Post by superyounan1 on 2007-10-19
thats weird, turning the animation setting off in gconf should do it. Dist-upgrades sometimes reset these options, try it again maybe, 
```
gconftool-2 --type bool --set /apps/panel/global/enable_animations
false 
```

you can also try Applications/System Tools/Configuration Editor/apps/metacity/general/reduced_resources

read the description in gconf, it will make a number of changes, but the animations should be turned off along with them

> this is unbelivable, no one has anything to say..

as you know, most of us are just regular users like you who help if they can. sometimes the answer doesn't come, happens to everyone. please don't use an irritated tone

---

### Post by kryysler on 2007-10-19
yep, it is wierd.. already tried all those things. and i did a clean install of gutsy so....

---

### Post by nooblot on 2007-10-22
haha I asked the same question yesterday 
[http://ubuntuforums.org/showthread.php?p=3606349](http://ubuntuforums.org/showthread.php?p=3606349)

Post#4 made me a happy noob :)

Now that looks better !:guitar:

---

### Post by kryysler on 2007-10-23
Good that this thread did help somebody at least. But i still got my problem. Does compiz disable the panel animation effects or does they run in parallel? Just wondering because the new fglrx is coming this week and i will get compiz up and working. Thx

---

### Post by kryysler on 2007-10-28
more ideas plz.. I really would like to get those borders away.

---

