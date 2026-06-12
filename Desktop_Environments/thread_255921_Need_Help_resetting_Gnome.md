---
title: "Need Help resetting Gnome"
date: 2006-09-12
forum: Desktop Environments
---

### Post by themacmeister on 2006-09-12
I was too busy messing around with XGL and Compiz, and now my regular Gnome session broke. I managed to restore window decorations with Metacity (the default for Gnome?). Unfortunately, the Human theme, amongst many others has reverted to a Dark Pink colour - not orangey brown.

With KDE, I believe you could reset your desktop by deleting the .kde folder in your home directory. Gnome looks a little more complex than that.

Could someone pls let me know if there is a way to reset Gnome to defaults, and if not, what I might be able to do to fix this anomally.

---

### Post by ayoli on 2006-09-12
In a terminal, type in:
```
rm -rf ~/.gnome* && rm -rf .gconf*
```
logout, then logon.
You should recover default presets.

---

### Post by themacmeister on 2006-09-12
This did not quite solve my problem, but while looking through the DEBIAN menu (thank you Automatix!) I discovered GTK2-Theme-Chooser, and it was set incorrectly. Setting this to Human solved my issues... many thanks for the help!

[[img=http://img180.imageshack.us/img180/3213/screenshotuf2.th.jpg]](http://img180.imageshack.us/my.php?image=screenshotuf2.jpg)

---

### Post by ayoli on 2006-09-12
ah, if you used a theme chooser i should have said ```
rm -rf ~/.gtkrc*
```

---

