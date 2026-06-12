---
title: "Possible to get window resize shortcut keys?"
date: 2010-10-28
forum: Desktop Environments
---

### Post by infinite012 on 2010-10-28
I have Ubuntu 10.10 running on a partition off of my Win7 hard drive. The thing I really like about Windows 7 is when I hit windows key+left or win+right, the current window will snap over to the left half or right half of the screen, respectively.

Is there a way to get this same functionality from Ubuntu?

Thanks.

---

### Post by VCoolio on 2010-10-28
But of course. Install wmctrl and use commands like these (change the last five numbers for workspace - x-coordinate - y-coordinate - width - height (coordinates of top left corner of the window):
```
"wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,30,950,970"
"wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,960,30,950,970"
```
I use these for a 1920 x 1080 resolution with margins for conky on top and a panel at the bottom; configure to your needs.
If you're using compiz you may like the tiling plugin.

---

### Post by infinite012 on 2010-11-03
Thanks that worked out pretty well.

I changed the commands for my desktop settings (1920x1080, wanted the window to resize all the way to the bottom of the screen):
Bound to Window+Left: wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,20,960,1100

Bound to Window+Right: wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,960,20,960,1100

Bound to Window+Up: wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz

Thanks!

---

