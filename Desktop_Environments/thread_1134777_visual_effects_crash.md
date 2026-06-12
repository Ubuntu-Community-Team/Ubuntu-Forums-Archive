---
title: "visual effects crash"
date: 2009-04-23
forum: Desktop Environments
---

### Post by phoenixjgibson on 2009-04-23
i was updating to jaunty, and i was stupid enough to mess with compiz/desktops effects while it was still updating, and i turned on some kind of texture smoothing thing and my desktop crashed and i couldnt see anything or access any menus. my question is, how can i disable visual effects through terminal, or otherwise fix this problem? this happened on my admin user, so i cant make any changes to my sytem without this account...any help would be greatly appreciated!

the effect is "bicubic filter"

---

### Post by gettinoriginal on 2009-04-24
Copy and paste this to your terminal, it sets all compiz settings back to default.
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by Mapusaurus on 2009-04-24
I tried the Bash commands above and nothing happened; they said it was a parsing error. Any other suggestions?:confused:

Never mind! I managed to log on as a different user and at the Login screen selected Safe Gnome and was then able to reset everything through the GUI. I've turned off Desktop effects and now there are no problems. Desktop Effects in 9.04 don't seem to work with my Intel Graphics card; but then, they didn't work very well in 8.10! Can't say I really miss desktop effects though -seems like more trouble than it's worth- and apart from that I'm very happy with Ubuntu.

---

