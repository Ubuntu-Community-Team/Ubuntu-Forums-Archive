---
title: "Openbox wallpaper changer"
date: 2010-01-11
forum: Desktop Environments
---

### Post by MooPi on 2010-01-11
I'm a big fan of Openbox and have a simple way to rotate my wallpaper. I use crontab to change my wallpaper from 8am to midnight,(when I would use the computer). The added benefit of changing on the hour is it brings my attention to the time, which I lose track of when I'm busy.I use "feh" to display my wallpaper and photos so here is my simple changer.
```
# m h  dom mon dow   command
 00 00  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/universe.jpg
 00 08  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/zapp.jpg
 00 09  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/wisper.jpg
 00 10  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/universe.jpg
 00 11  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/timezone.jpg
 00 12  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/seeds.jpg
 00 13  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/roadtrip.jpg
 00 14  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/moonphase.jpg
 00 15  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/goldfish.jpg
 00 16  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/earth.jpg
 00 17  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/deepblue.jpg
 00 18  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/cosmos.jpg
 00 19  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/boobles.jpg
 00 20  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/wisper.jpg
 00 21  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/seeds.jpg
 00 22  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/roadtrip.jpg
 00 23  *   *   *    env DISPLAY=:0 feh --bg-scale ~/background/timezone.jpg
```

---

### Post by DeadPanDan on 2012-08-23
Thanks for posting this. Here's one for a more rapid switching.


# m h  dom mon dow   command
 0,20,40 *   *   *   *    env DISPLAY=:0 feh --bg-scale ~/Pictures/27key.png
 15,35,55 *   *   *   *    env DISPLAY=:0 feh --bg-scale ~/Pictures/Babbage_Dif$
 30,50,10 *   *   *   *    env DISPLAY=:0 feh --bg-scale ~/Pictures/typewriter-$
 45,5,25 *   *   *   *    env DISPLAY=:0 feh --bg-scale ~/Pictures/Vespa-GTS.jpg

---

