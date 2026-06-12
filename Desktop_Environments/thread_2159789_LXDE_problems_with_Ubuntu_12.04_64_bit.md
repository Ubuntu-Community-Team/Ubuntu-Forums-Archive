---
title: "LXDE problems with Ubuntu 12.04 64 bit"
date: 2013-07-04
forum: Desktop Environments
---

### Post by SangeetKhatri on 2013-07-04
Okay so i like Unity, but i love LXDE more, that is why i installed LXDE in my Ubuntu 12.04 64bit but there is a small problem which is not letting me use LXDE comfortably.

When i start LXDE everything loads up just fine with PCManFM controlling the desktop, but as soon as Nautilus or the xArchiver or any other Ubuntu app kicks in the desktop changes to be controlled by Nautilus which gives a lot of bugs and then after i am not able to change the desktop background and things become a lot weird, like the minimize animation goes towards the center of the screen rather than going towards the panel.

Whenever i right click on desktop and click on "Change Desktop Background" after Nautilus replaces the desktop it opens up Ubuntu "Settings Manager" which shows only 4-5 icons. I mean things gets completely messed up.

Any way i can get the normal behavior back and i also do not mind using PCManFM at all. But I just want to solve this problem.

I want is that the Ubuntu/Unity should not interfere with the LXDE Desktop Environment and i want to use PCManFM desktop just as i use it on other LXDE distros

---

### Post by silv3rm00n on 2013-07-04
Yes, I noticed that too. The gnome desktop if installed messes with lxde and xfce.
However if lxde is the only desktop installed such problems do not appear. For example Lubuntu

Let me know if you find a solution to this.

---

### Post by edb66083 on 2013-07-05
I have had trouble in the past with installing other DEs, and using them when I login. It's a different experience than just using the straight distro that uses that DE. In other words, using LXDE on an Ubuntu install gives you a different experience than using LXDE on a Lubuntu install.

If you really prefer LXDE over Unity, then I would suggest doing a fresh install of Lubuntu. LXDE will behave better. Of course, Lubuntu 12.04 is not a LTS, so you would have to go with the current 13.04 and only get 9 months of support.

---

### Post by Bashing-om on 2013-07-05
Guys ..
Here is what I understand:
lxde = granny smith apple ->GTK2 engines
Nautilus = red delicious apple -> GTK3 engines

Would be interesting to see the difference returned between the two desk top environments:
```
sudo apt-get install transmission-gtk
transmission-gtk

```
By tweaking on the config files, can be made to work. But that is presently above my knowledge to advise further.

[INDENT][INDENT]but it's ubuntu, where there is a will there is a way[/INDENT][/INDENT]

---

