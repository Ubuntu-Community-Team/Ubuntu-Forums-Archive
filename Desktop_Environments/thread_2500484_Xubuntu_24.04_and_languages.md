---
title: "Xubuntu 24.04 and languages"
date: 2024-09-03
forum: Desktop Environments
---

### Post by benlarcher-1 on 2024-09-03
Hi,
When I install Xubuntu 24,04 in my language, the installation stays in  English (before the new installer, it used to get installed directly in  the user language).
Anyway, you can still change the language (and  Regional preferences) and reboot.
But even so, Thunar folders name (or Nautilus or something else) is  still in English (The rest is OK). 
xdg-user-dirs-update doesn’t work even if user-dirs.locale is ok and includes ```
fr_FR
```
Editing « user-dirs.dirs »  doesn’t work  either and makes a mess.
Anyone has the same thing or an idea of what to do ?
PS : I contacted the developers of Thunar ([https://gitlab.xfce.org/xfce/thunar/-/issues/1417](https://gitlab.xfce.org/xfce/thunar/-/issues/1417)) but apparently it comes from user-dirs.dirs

---

### Post by benlarcher-1 on 2024-09-03
How to solve (not user friendly at all...)

[LIST=1]
[*]Create the folders in your language
[*]Edit the $HOME/.config/user-dirs.dirs (Be aware that .config is hidden and you should display hidden files)
[*]Reboot
[*]Delete the old files in English
[/LIST]

---

