---
title: "Different wallpapers on virtual desktops"
date: 2010-05-27
forum: Desktop Environments
---

### Post by Kodpoet on 2010-05-27
So I've seen the tutorials where you simply tell nautilus to not draw the wallpaper and then use ccsm's wallpaper-plugin to set different wallpapers.

It's just that I don't seem to have said plugin :P Where could it be?

[IMG]http://i47.tinypic.com/280nw9g.png[/IMG]

---

### Post by ubername on 2010-05-27
compiz-fusion-plugins-extra now has to be added manually. (via synaptic, aptitude or whatever you prefer)

---

### Post by hok00age on 2010-05-28
> **Kodpoet said:**
> So I've seen the tutorials where you simply tell nautilus to not draw the wallpaper and then use ccsm's wallpaper-plugin to set different wallpapers.

It's just that I don't seem to have said plugin :P Where could it be?

[IMG]http://i47.tinypic.com/280nw9g.png[/IMG]

Run:
```
sudo add-apt-repository ppa:compiz/ppa && sudo apt-get update
```

```
sudo apt-get install compiz-fusion-plugins-extra
```

Hope it works! :)

---

### Post by Kodpoet on 2010-05-30
I was under the impression I allready had that package, but it seems I didn't :P

Thank you both!

---

### Post by SoFl W on 2010-05-30
Ok, I just got around to playing with this features, how do I change the backgrounds to different pictures?  
I have different files listed in Desktop Cube-> Apperance
I have different files listed in Utility -> Wallpaper

neither give me a different background picture for each workplace.  
Do I need to assign them somewhere or am I missing a turn on this feature?


_**EDIT:**_ Found my answer **[HERE]("http://ubuntuforums.org/showpost.php?p=8980705&postcount=2")**
I messed around with this once before but not seriously.  It is almost working the I want.  Although this question has been asked a lot, this led me in the right direction.

You can't have icons or Conky with different backgrounds?

---

