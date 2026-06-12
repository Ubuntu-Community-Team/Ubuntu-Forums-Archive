---
title: "Xubuntu Wallpaper Problem [10.04]"
date: 2010-08-25
forum: Desktop Environments
---

### Post by kerem34 on 2010-08-25
I have changed background image, its ok but there is an annoying problem.
Everytime I open my netbook or logout-login my new wallpaper shows up normally for 2 seconds and then [MY VERY FIRST WALLPAPER] shows up for 1 second and then it turns back to normal. ](*,) I have deleted my very first wallpaper from pictures folder but it does not make any change. Whatever wallpaper I use this annoying thing happens. How can I prevent this from happening.

Please help me,
Thanks in advance

---

### Post by xtnsgo on 2010-08-25
There may be a copy of your old wallpaper in ~/.cache/wallpaper.  Or it may, for some reason, be hanging out in /usr/share/backgrounds (wp's you add shouldn't be in there, but who knows?).  

Alternatively, is there a possibility your old wallpaper was the same as your boot screen background?  Maybe you could try changing your boot screen to "none" in preferences.  

Sorry I don't have more for you (haven't used xfce/xubuntu in a bit) but good luck!

---

### Post by kerem34 on 2010-08-26
You are great!!

[[IMG]http://img823.imageshack.us/img823/2461/screenshotop.th.png[/IMG]](http://img823.imageshack.us/i/screenshotop.png/)

I found the old wallpaper in the **~/.cache/wallpaper** directory. If anyone have a similiar problem it could be solved like this, thanks to **xtnsgo** i can see norah jones without interruption :popcorn:

---

### Post by kerem34 on 2010-08-26
And i also kinda figured out the reason for this problem.
It happens when you choose "set as desktop background" using **firefox**.

---

### Post by xtnsgo on 2010-08-26
Glad I could help! :D

---

### Post by Me Mechant on 2011-02-24
I have the same problem, but even when i delete the wallpaper in my cache folder it always comes back when i restart my computer...please help.

Thanks!

---

