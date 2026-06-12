---
title: "No Window Decorator"
date: 2010-06-14
forum: Desktop Environments
---

### Post by inhuman!!! on 2010-06-14
I installed e16 for testing and after uninstalling it when I log into my gnome session I have no window decoration. I can have it back by reloading window manager from Fusion Icon, But every time I restart window decoration is gone. I just uninstalled e16 but I think after installing it it changed something somewhere and I don't know what.

---

### Post by limestone on 2010-06-14
gnome's window manager is Metacity.. open a terminal and enter metacity or metacity --replace to se if it's still installed

---

### Post by inhuman!!! on 2010-06-14
it is installed

---

### Post by limestone on 2010-06-14
So it does appear.. Try open System-preferences-startup apps and create one for metacity, it should work.

---

### Post by inhuman!!! on 2010-06-14
OK. I'll be back after restart to check it out. Thanks

---

### Post by inhuman!!! on 2010-06-14
It worked, But It doesn't solve my problem. you see now only metacity works and for compiz to work I have to reload window manager again.
I don't think this is the solution.

---

### Post by limestone on 2010-06-14
aaah.. you use a different window manager?? don't know how compiz manager works but emerald starts with emerald --raplace probably same with compiz..

---

### Post by inhuman!!! on 2010-06-14
OK. I got it. instead of "metacity --replace" I should use "gtk-window-decorator --replace"
Thanks

Edit:
No. This was not the answer. I still have no window decorator after restart.

---

### Post by limestone on 2010-06-14
> **inhuman!!! said:**
> OK. I got it. instead of "metacity --replace" I should use "gtk-window-decorator --replace"
Thanks
yep, just keep posting if it's not good.. And don't forget to mark post as solved when solved.

---

### Post by limestone on 2010-06-14
yep, just keep posting if it's not good.. And don't forget to mark post  as solved when solved.

---

### Post by inhuman!!! on 2010-06-14
Sorry. It didnt work. I should check with other user to see if its system wide or just my profile.

---

### Post by inhuman!!! on 2010-06-14
Root user doesnt have such problem. just noticed that after logging out of root and logging back to my user window decoration was working for a sec and then it was gone. I think something crashes.

---

### Post by eggdeng on 2010-06-14
Seems to be a bit of a mix up here with window managers (metacity, compiz) which draw windows, and window decorators ( gtk-window-decorator, emerald) which draw the window border and close, minimize, maximize buttons.
If you don't have CCSM installed, install it (with plugins and emerald) with
```
sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-extra emerald
```
Then in CompizConfig Settings Manager -> Window Decorator, change the default command to
```
/usr/bin/emerald
```
and restart gnome.

Edit: I just saw you have Fusion-Icon installed, so make sure you have emerald ```
sudo apt-get install emerald
``` & this setting should be available from there.

---

### Post by inhuman!!! on 2010-06-14
No. Thats not it. I think I have everything I nees. But installing e16 changed something in my window decorator setting and after removing it the settings are not changed back.
I didnt have any problem before.

---

### Post by nix-idioteque on 2010-06-15
Hah, yes I did the exact same thing and what had fixed it for me was simply opening up appearance, visual effects and I dunno...  It just searched for a driver and asked me if I wanted to change my settings.  Fixed it on the spot

---

