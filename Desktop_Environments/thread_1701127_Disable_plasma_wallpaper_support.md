---
title: "Disable plasma wallpaper support"
date: 2011-03-06
forum: Desktop Environments
---

### Post by zoltar_32 on 2011-03-06
hi everybody.
i'm using xscreensaver as wallpaper with awesomeWM, for that i set it to run in the root window.
i tried the same with KDM, but realized KDM doesn't use the root window but controls the desktop wallpaper through plasma-desktop.
so using *xscreensaver -root &* doesn't work with KDE.
then, i tried to avoid the problem by running xscreensaver in the the plasma-desktop window using its windowid  (xwininfo).
it works great, except when i click the desktop, or maximize/minimise windows, when it happens, the screen flickers and shows the original plasma wallpaper ( or the desktop plain color if no wallpaper is set).
my question is simple : is there a way to disable plasma desktop control other the desktop wallpaper ( and use the root window to set he wallpaper ie: xsetroot)?
or
is there a way to avoid the flickering when setting xscreensaver in the plasma-desktop window?
what do you people use for animated wallpapers in KDE?
any help would be appreciated, thank you in advance....

---

