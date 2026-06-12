---
title: "restore original gdm theme"
date: 2010-09-04
forum: Desktop Environments
---

### Post by palz2015 on 2010-09-04
I installed xfce to try it out. Nothing against it, its a nice environment.

But when trying to return to the default gdm theme (just by setting theme and wallpaper), I still have the blue xubuntu logo and a white bar at the bottom with xfce icons. How do I completely reset the settings?

---

### Post by palz2015 on 2010-09-04
Also it changed my plymouth theme!!! Just like in  karmic. So intrusive

---

### Post by tom4everitt on 2010-09-04
Normally you can choose which desktop manager to use at the login page. Or is it the login page your trying to change back?

If you don't want xfce anymore, I guess you could just uninstall it:
```

sudo apt-get remove --purge xfce

```

---

### Post by palz2015 on 2010-09-04
Its the login page. It uses xfce icons and the rat logo. I could change the theme to ambience but it doesnt change the logo or icons.

---

### Post by tom4everitt on 2010-09-05
Ok, I see. 

Go to System -> Administration -> Login screen

There you can choose your login page (there's probably a fancy terminal way of doing it too, don't remember it at the moment though).

---

