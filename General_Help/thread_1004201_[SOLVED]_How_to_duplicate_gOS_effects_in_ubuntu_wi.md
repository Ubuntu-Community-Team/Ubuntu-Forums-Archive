---
title: "[SOLVED] How to duplicate gOS effects in ubuntu without installing gos-desktop?"
date: 2008-12-07
forum: General Help
---

### Post by malathion on 2008-12-07
In gOS there is a very slick compiz desktop wall-like effect where the windows move but the wallpaper and desktop icons do not. This is much more attractive because you do not see the borders of the wallpaper where it does not wrap around. I cannot figure out how to duplicate this effect in compiz outside of gOS. Is there some plugin I need to make this work?

---

### Post by Sugz on 2008-12-07
I highly agree, the desktop switching where JUST the windows move is much more attractive than the current compiz implementation.
I would also like to know if this is possible :D

---

### Post by malathion on 2008-12-09
Bump

---

### Post by Forlong on 2008-12-09
Could you please provide a link to a video that showsn this effect or something?
I (and I assume many others) have never used gOS and I'm not sure what it is you want to achieve.

---

### Post by malathion on 2008-12-10
After some more googling, I found that someone had asked my question here: [http://ubuntuforums.org/showthread.php?t=784758](http://ubuntuforums.org/showthread.php?t=784758)

The answer is the "static" plugin, here: [http://forum.compiz-fusion.org/showthread.php?t=7062&page=7](http://forum.compiz-fusion.org/showthread.php?t=7062&page=7)

I'm currently having some problems installing it, but I'll report back if I got any luck.

---

### Post by dcviana on 2008-12-10
Thank you for the tip. I installed it and worked like a charm. If you haven't seen yet, follow the instructions on this page to compile and install it.

[http://www.efaref.net/compiz/plugins/static.html]("http://www.efaref.net/compiz/plugins/static.html")

---

### Post by malathion on 2008-12-10
Yep. I was able to get it installed. It sticks the dock, and that's great, but unfortunately it doesn't stick the desktop. I've been informed on the compiz forums:
> **SmSpillaz said:**
> You cannot sticky the desktop, this is an intentional limitation by the compiz core to prevent the area behind the desktop from not drawing correctly.
Oh well, it's better than nothing!

---

### Post by employeeno5 on 2008-12-11
> In gOS there is a very slick compiz desktop wall-like effect where the windows move but the wallpaper and desktop icons do not. This is much more attractive because you do not see the borders of the wallpaper where it does not wrap around. I cannot figure out how to duplicate this effect in compiz outside of gOS. Is there some plugin I need to make this work?

Is the the latest version of gOS, gOS3 Gadgets? 

The newest effects from the KDE 4.2 window manager does exactly what you originally described for it's desktop wall effect.

The gOS 3 desktop was using [LXDE ]("http://lxde.org/")last time I checked. Could it be that they're using KWIN as their window manager for effects rather than compiz?

---

### Post by malathion on 2008-12-14
> **employeeno5 said:**
> Is the the latest version of gOS, gOS3 Gadgets? 

The newest effects from the KDE 4.2 window manager does exactly what you originally described for it's desktop wall effect.

The gOS 3 desktop was using [LXDE ]("http://lxde.org/")last time I checked. Could it be that they're using KWIN as their window manager for effects rather than compiz?

It was a much older version, I think from when they were using Epiphany still.

---

### Post by malathion on 2008-12-29
Good news! It seems my asking about this over at the compiz forums got the attention of a developer who added this functionality to the wall plugin itself. I just got it up and running and it looks great!

Until it gets added to the ubuntu repos, you will have to install from git to get this functionality. See here for instructions on how to do this: [http://forum.compiz-fusion.org/showthread.php?t=7744](http://forum.compiz-fusion.org/showthread.php?t=7744)

---

### Post by levelup3 on 2008-12-30
Thanks for all your post, I have the same problem and now it has been sorted!

---

### Post by Islington on 2008-12-30
thats awesome thanks.

---

### Post by Islington on 2008-12-30
(type=Desktop|Dock) my definition for which windows not to move.

---

