---
title: "desktop icons align and arrange"
date: 2014-04-30
forum: Desktop Environments
---

### Post by nLpPyXR on 2014-04-30
Simple question: how do I configure my Trusty Tahr Lubuntu (core) to **auto** align and arrange desktop icons?

Bonus points: preferably in a horizontal manner (bottom left corner of the screen, from left to right)

---

### Post by bapoumba on 2014-05-01
OK, saw your thread yesterday and was hoping someone would answer :)
I'm not sure it is possible [https://wiki.archlinux.org/index.php/PCManFM](https://wiki.archlinux.org/index.php/PCManFM)

Saw a post from vasa on another forum, but I cannot retrieve it.

Here is what I have in /home/bapoumba/.config/pcmanfm/lubuntu/dektop-items-0.conf, after moving a file on the desktop (look at the bottom) :
```
[*]
wallpaper_mode=stretch
wallpaper_common=1
wallpapers_configured=1
wallpaper=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
desktop_bg=#000000
desktop_fg=#ffffff
desktop_shadow=#000000
desktop_font=Ubuntu 11
show_wm_menu=0
sort=mtime;ascending;
show_documents=0
show_trash=0
show_mounts=1

[test.png]
x=3
y=15
```

I keep my desktop empty and only show removable media when there is one plugged in.

Edit : a right click allows to snap to grid.

---

### Post by nLpPyXR on 2014-05-02
thank you for replying to the thread, but that didn't work for me...

eh, perhaps I should just get walls with nothing interesting in the left side or alternatively install a dock.

---

### Post by vasa1 on 2014-05-02
> **nLpPyXR said:**
> Simple question: how do I configure my Trusty Tahr Lubuntu (core) to **auto** align and arrange desktop icons?

Bonus points: preferably in a horizontal manner (bottom left corner of the screen, from left to right)
I don't know what "Trusty Tahr Lubuntu (core)" comes with but in regular Lubuntu, PCManFM, the file manager also "manages" the desktop. However, in my brief experience, I found the options quite limited and didn't find anything relating to arranging desktop icons the way you desire.

What exactly are you aiming for in terms of actual function? Maybe someone can suggest something?

---

### Post by Kostchtchie on 2014-10-26
I found that selecting all your desktop icons and then Right-Click, Snap to Grid, really helped me organize my desktop space, cheers!

---

