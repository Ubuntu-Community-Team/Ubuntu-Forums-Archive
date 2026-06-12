---
title: "screen problem"
date: 2009-01-08
forum: General Help
---

### Post by CipherX on 2009-01-08
new and all, have no clue whats going on, but i know this is not what the desktop should look like

[http://s376.photobucket.com/albums/oo202/xXD-NogXx/?action=view&current=DSC01729.jpg](http://s376.photobucket.com/albums/oo202/xXD-NogXx/?action=view&current=DSC01729.jpg)

any ideas, comp is a dell latitude p3 256mb mem, ubuntu 8.10

---

### Post by gettinoriginal on 2009-01-08
System > Preferences > Screen Resolution/refresh rate, is this configured right ??

---

### Post by CipherX on 2009-01-08
thats the only screen i can get too, my friend who set it up is lost too

---

### Post by CipherX on 2009-01-10
the screen works fine when i start the computer with a lcd external monitor and then the laptop screen works fine until u turn off the laptop

---

### Post by mgol on 2009-01-10
> **gettinoriginal said:**
> System > Preferences > Screen Resolution/refresh rate, is this configured right ??
This is not connected. GNOME does not user's settings when configuring Your desktop login screen as there are no users logged yet, so how could it know which settings to follow...

> **CipherX said:**
> the screen works fine when i start the computer with a lcd external monitor and then the laptop screen works fine until u turn off the laptop

You mean that if You start the computer with an external LCD connected then You can disconnect it and use laptop default screen without any problems? Do You login using this external monitor or even before logging in screen gets better in this case? Could You explain it more clearly?

Could You post Your xorg.conf file? To do it, open Applications->Terminal and enter:
```
cat /etc/X11/xorg.conf
```
Then attach here the output of this command.

---

