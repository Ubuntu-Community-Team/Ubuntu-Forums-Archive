---
title: "Make terminals show desktop wallpaper?"
date: 2013-08-02
forum: Desktop Environments
---

### Post by Fenderian_Mayhew on 2013-08-02
I have for years wanted, what i now know is called, composted tranparency for terminals. It is finally here as a default. now however I yern for the ability to have a terminal show the desktop wallpaper only, and not the windows underneath. 

Has this been preserved? or must i disable composting in compiz, as well as open gl and many nice gui features :( Heres hoping not.

I use Variety for a wallpaper changer and Unity 2D.

---

### Post by TheFu on 2013-08-02
I've never heard of selective opacity being an option. The only way that I'm aware to show the wallpaper is to minimize all other windows.  BTW, transparent or opaque windows have been available since the mid-90s. FVWM had those then - btw, FVWM still exists and still supports it. You can install and use fvwm under Ubuntu, if you like. It will show up as a DE choice on the login screen, just like other window managers and DEs do.  OTOH, fvwm settings are controlled by a text file - no fancy GUI that I've seen.

---

### Post by zombifier25 on 2013-08-03
I can confirm that when you turn on opacity on window managers that does not support compositing, it will show the desktop background.
You said that you use Unity 2D, which uses the window manager Metacity. Try turning compositing off in Metacity:
```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```

---

### Post by zteam2 on 2013-08-03
Yes, the Terminal can definitly use transparency, just open your terminal and  go to Edit -> profilesettings ->  Background and select the amount of transparency you want, from here you can also set a custom terminal background. 
Showing the desktop without minmizing your windows however is not possible.

---

