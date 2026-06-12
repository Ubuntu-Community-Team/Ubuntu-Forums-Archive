---
title: "Ubuntu Desktop problems"
date: 2014-06-13
forum: Desktop Environments
---

### Post by Grim_Gent on 2014-06-13
I"m running Ubuntu 14.04 64bit 3.13.0-29-generic.
When I login to Ubuntu, all I get is a wallpaper and there does'nt seem to be any keyboard shortcuts.
All the other desktops(GNOME etc etc) work.

My graphics card;
NVIDIA Corporation:C61[GeForce6150SE nForce 430]

---

### Post by Grim_Gent on 2014-06-13
I fixed it by entering these commands;
```

[TABLE="class: code-table, align: left"]
[TR]
[TH] Terminal Commands:[/TH]
[/TR]
[TR]
[TD] sudo apt-get install dconf-tools[/TD]
[/TR]
[TR]
[TD] dconf reset -f /org/compiz/[/TD]
[/TR]
[TR]
[TD] setsid unity[/TD]
[/TR]
[/TABLE]







```
from this site;
[http://www.noobslab.com/2014/04/thingstweaks-to-do-after-install-of.html](http://www.noobslab.com/2014/04/thingstweaks-to-do-after-install-of.html)

---

