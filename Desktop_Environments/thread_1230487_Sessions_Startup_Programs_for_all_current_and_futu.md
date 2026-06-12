---
title: "Sessions Startup Programs for all current and future users?"
date: 2009-08-03
forum: Desktop Environments
---

### Post by garg on 2009-08-03
I'm using Ubuntu 8.04 and I wanted to know if there was a way to set the Startup Programs for all current and future users. Currently, if you go to Sessions Preferences, I can set a pygtk gui script to run for the specific user but is there a way to have it so all current and future users all launch the same program on start up?

Where can I set that?

Thank you :)

---

### Post by asmoore82 on 2009-08-03
the startup apps you set for yourself will be *.desktop files in ~/.config/autostart/;
you'll want to copy the one you want up to /usr/share/gnome/autostart/

Example:
```
sudo cp -v ~/.config/autostart/mypygtk.desktop /usr/share/gnome/autostart/
```
(`~` is your "$HOME" folder)

---

### Post by garg on 2009-08-03
Thank you! That worked perfectly!

---

