---
title: "Gnome-do rarely runs on startup"
date: 2010-01-19
forum: Desktop Environments
---

### Post by dapaintballer331 on 2010-01-19
It appears to be random, but 1/2 to 1/4 bootups gnome-do loads on startup. I see in in System>...>Startup

If I can't see it, the process is there, its jut not running. The only way to launch it manually is:

skill gnome-do
gnome-do

Any idea why it isn't loading automatically? I have version 0.8.2, the latest in the repo for jaunty.

---

### Post by stinkeye on 2010-01-20
> **dapaintballer331 said:**
> It appears to be random, but 1/2 to 1/4 bootups gnome-do loads on startup. I see in in System>...>Startup

If I can't see it, the process is there, its jut not running. The only way to launch it manually is:

skill gnome-do
gnome-do

Any idea why it isn't loading automatically? I have version 0.8.2, the latest in the repo for jaunty.
Sometimes if gnome do starts before compiz is loaded it can cause problems.

Try using
```
sleep 30 && gnome-do
```
in startup applications

or

if your using compiz try this solution
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=8376643&postcount=9[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=8376643&postcount=9") 
Ignore the first part about wmctrl.

---

