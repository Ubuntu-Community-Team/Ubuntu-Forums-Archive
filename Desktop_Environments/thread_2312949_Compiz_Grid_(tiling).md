---
title: "Compiz Grid (tiling)"
date: 2016-02-08
forum: Desktop Environments
---

### Post by v3.xx on 2016-02-08
This plugin is working as it should, but I wish to have control of the window sizes (like x-tile) and this cannot be adjusted using ccsm.  So I'm thinking there should be a configure file with x/y parameters, but I'm not finding it.

Anyone try this?

---

### Post by CantankRus on 2016-02-08
Make your own grid placements using wmctrl
[http://ubuntuforums.org/showthread.php?t=1673250&p=10386910#post10386910](http://ubuntuforums.org/showthread.php?t=1673250&p=10386910#post10386910)

**Note:** If you want resizing to work with maximized windows, you first have to remove the maximized states.
eg: first command removes maximized states while the second command resizes and places....
```
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz **[COLOR="#FF0000"]&&[/COLOR]** wmctrl -r :ACTIVE: -e 0,450,260,850,531
```

---

### Post by v3.xx on 2016-02-09
I totally forgot about wmctrl.  That's my next stop, THANKS :D

---

### Post by v3.xx on 2016-02-11
If one quotes one's self is it truly a quote :-k

> Well after messing around with code and programs, I seem to have found the best answer for me.

I think by far that x-tile would be the best choice if only it was maintained.  I also tried some other so called gui tiling programs (example; devilspie) and found them to be more of a mix of code and gui (a UI?).  The best option for me seems to be "wmctrl".  This program has several uses one of which is tiling and it supports metacity.  Its a terminal only program which makes it somewhat painful to work with, but my needs have changed and this looks like the best option for me.

I have found out that I was not happy with a 4way split on the larger monitor and a simple split screen (two windows) is the way I went.  I also found out that I like a 3way screen on a VM (like the pic above).  Such simple layouts are doable (for me) using wmctrl and marco.  I have found some scrips on line that claim to automate this process with wmctrl, but they either only partially worked or were buggy.

Maybe I have overlooked a simpler solution (I like simple); leaving this thread open for now.

[https://ubuntu-mate.community/t/split-screen-4-ways/3750/4](https://ubuntu-mate.community/t/split-screen-4-ways/3750/4)

---

