---
title: "Really Messed up  unity"
date: 2012-01-03
forum: Desktop Environments
---

### Post by Shinjuurou on 2012-01-03
Well when trying to get Compiz i messed up unity i was able to fix it by reset unity and uninstalling it but after i tried other things. But no when i have nothing open the top bar doesnt have any desktop options on it now its just blank until i open a program. also the multi workplace thing doesnt work it only shows the one i have the others are black and dont work at all when i click them they open up the home folder. also somehow all of the visual things for the log on and shut down aren't their anymore its just a very plain thing it also is showing processes going like when its shutting down instead of just the regular dots or whatever. im running 11.10 Thanks!

---

### Post by stinkeye on 2012-01-03
What did you uninstall?

---

### Post by Shinjuurou on 2012-01-03
All the compiz stuff but not the thing just called compiz thats used with unity right?so I didnt do anything to that

---

### Post by Finolin on 2012-01-03
[LIST]
[*]to reset the Unity launcher icons:
  unity --reset-icons
[*]to reset Unity:
  unity --reset
[*]to reset Compiz:
  gconftool-2 --recursive-unset /apps/compiz-1 unity --reset
[/LIST]

---

### Post by stinkeye on 2012-01-03
> **Shinjuurou said:**
> All the compiz stuff but not the thing just called compiz thats used with unity right?so I didnt do anything to that
Compiz is the window manager for unity and is installed by default.

**compizconfig-settings-manager** is not installed and is just a progam to change compiz plugin settings.
It is a bit buggy in that it can cause compiz not to reload properly when changing some settings.Can be recovered as you have found.
Uninstalling **compizconfig-settings-manager** does nothing really.
It's what else you may have uninstalled that concerns me.

These are the compiz related apps on the install cd
```
libcompizconfig0	
compiz	
compiz-core	
compiz-gnome	
compiz-plugins-default	
compiz-plugins-main-default	
compizconfig-backend-gconf
```
Search in the software centre or synaptic and reinstall if necessary.
or
in the terminal to reinstall all default apps
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Shinjuurou on 2012-01-04
i did the install but when i reset it gives this error
WARN  2012-01-04 23:19:38 glib <unknown>:0 Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

What does this mean?

---

