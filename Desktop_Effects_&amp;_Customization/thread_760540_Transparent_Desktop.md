---
title: "Transparent Desktop ?"
date: 2008-04-20
forum: Desktop Effects &amp; Customization
---

### Post by pro003 on 2008-04-20
anyone have any idea how to set transparent menu, right click menu, etc.  ?:confused:

something like this pic; 

[http://www.fvwm.org/screenshots/desktops/Nuno_Alexandre-1600x1200/screenshot.jpg](http://www.fvwm.org/screenshots/desktops/Nuno_Alexandre-1600x1200/screenshot.jpg)


I'd appreciate anyones help...

---

### Post by liquid circuit on 2008-04-20
I am assuming you are using compiz-fusion, and it is working correctly....  You'll need compizconfig-settings-manager
```
sudo apt-get install compizconfig-settings-manager
```

Then run it by clicking through ***System > Preferences > Advanced Desktop Effects Settings***.

Click on ***General Options***.
Click on the ***Opacity Settings*** tab.
Click the ***Add*** button
In the ***Opacity windows*** field, paste the following:
```
Tooltip | Menu | PopupMenu | DropdownMenu
```
then set ***Opacity window values*** to a number between 0 (fully transparent; a very bad idea) and 100 (fully opaque).
Click ***OK***.

---

### Post by pro003 on 2008-04-20
ok thanks, that's almost what I had in mind - but could you tell me how to increase the opacity of borders of menu and drop down menu etc, and especially font opacity, but to keep background transparent? 

any idea?

---

### Post by liquid circuit on 2008-04-20
Eesh, sorry.  No clue.

---

### Post by pro003 on 2008-04-20
ok, thanks liquid man...

will wait for someone with the clue... however I do get a nice picture/screen when toggle negative mode 'super+m' but still - it's not quite that....

---

