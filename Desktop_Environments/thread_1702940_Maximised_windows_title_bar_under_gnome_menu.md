---
title: "Maximised windows title bar under gnome menu"
date: 2011-03-08
forum: Desktop Environments
---

### Post by computerx138 on 2011-03-08
G'day,

Weird issue. I just bought a new monitor and am having some issues. When a window is maximised on the larger (active) monitor, the title bar (including the close, minimize and maximise/restore) buttons are appearing UNDER the Gnome system menu bar. This is so bizzare, I can't think of any way to fix it.

Here's my setup:

P.O.S PC incl sellotape and glue to hold it together
GeForce 210 (1xDVI 1xVGA) incl Nvidia proprietary driver
Ubuntu 10.10, up to date, TwinView setup
VGA: 1360x768 position absolute +0+0
DVI: 1920x1080 position absolute +0+768 active display

I think I can vaguely see what's happening, having the non-active monitor "above" the main, but I'm like a skyscraper. I have limited width, lots of height to work with. I'm not putting the 24" up and behind the 19"...

I would consider using the screens as separate X screens, if I could move windows easily between them, but that doesn't seem possible.

I would appreciate any suggestions,

Thanks.

---

### Post by Krytarik on 2011-03-08
Try using Compiz' "Window Rules" plugin to put gnome-panel below all the other "windows":
- "System -> Preferences -> CompizConfig Settings Manager -> Window Management -> Window Rules"
- enter "class=Gnome-panel" in the field "Below"

Of course that way would still mean, that gnome-panel and other windows overlap each other, but gnome-panel is at least below of them.

And yes, you can't move windows between separate xscreens.

---

### Post by computerx138 on 2011-03-09
Thanks, but I don't have compiz installed (or at least ccsm wasn't installed, and there's no admin menu)

---

### Post by Krytarik on 2011-03-09
> **computerx138 said:**
> Thanks, but I don't have compiz installed (or at least ccsm wasn't installed, and there's no admin menu)
Do you have "Visual Effects" enabled then?

If so, you are running Compiz. Then just install CCSM:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by computerx138 on 2011-03-09
Wow, I didn't know about compiz. I'm gonna be playing with this for hours!

Thanks!

---

### Post by Krytarik on 2011-03-09
This will be helpful in setting up those rules:
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

But consider what I wrote earlier regarding it:
[http://ubuntuforums.org/showthread.php?p=10488654](http://ubuntuforums.org/showthread.php?p=10488654)

---

