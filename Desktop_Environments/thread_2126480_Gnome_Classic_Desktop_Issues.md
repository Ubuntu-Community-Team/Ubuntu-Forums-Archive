---
title: "Gnome Classic Desktop Issues"
date: 2013-03-17
forum: Desktop Environments
---

### Post by cdo on 2013-03-17
My Gnome Classic desktop has some stuff appearing in the top toolbar and i don't know where it is coming from or how to get rid of it . Note the red boxes at the top in the screenshot . Additionally , some of the small icons also have appeared by themselves though some i have placed there myself by dragging and dropping . Issues only appear on this one desktop account and only in Classsic .



Help appreciated..

---

### Post by ibjsb4 on 2013-03-17
Can you Alt + right click on it and delete?

If not, reset it?
[http://ubuntuforums.org/showthread.php?t=1970604](http://ubuntuforums.org/showthread.php?t=1970604)
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+gnome+classic+panel&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+gnome+classic+panel&sa=Search&cof=FORID:9)

Or ..
```
sudo apt-get remove --purge gnome-panel
```

Then reinstall it?

---

### Post by stinkeye on 2013-03-17
This is for 12.10 upwards...not sure with 12.04 as I don't have it installed,
but won't harm to try.

Try resetting first via terminal with...
```
dconf reset -f /org/gnome/gnome-panel/
```

The panel should reload with default settings.
If it doesn't reappear, run...
```
gnome-panel & disown
```

---

### Post by cdo on 2013-03-17
> **stinkeye said:**
> This is for 12.10 upwards...not sure with 12.04 as I don't have it installed,
but won't harm to try.

Try resetting first via terminal with...
```
dconf reset -f /org/gnome/gnome-panel/
```

The panel should reload with default settings.
If it doesn't reappear, run...
```
gnome-panel & disown
```

Thanks dude... tried your suggestion and got some funky directions from termnal window . Had to  use package manager and install dconf - tools . That did the trick .

Much grateful

---

