---
title: "Can't switch GTK2 theme"
date: 2005-08-12
forum: Desktop Environments
---

### Post by LokeDK on 2005-08-12
I have no idea how this happened but,
I am no longer able to change the gtk2 theme from the gnome-theme-manager - when I change theme, only the metacity theme changes but not the "window theme"
I've also switched to XFCE, but it's theme manager isn't able to change it either. The only way I can change it is gtk-theme-switch2.
Also checked for permissions on ~/.gtk* directories and files, ~/.gconf and so on. I have access to them, they're owned by my user.
Please help!
Thanks in advance.

---

### Post by Kimm on 2005-08-12
when your using XFCE you wount be able to use gnome-theme-manager to change the theme anymore, and as your not using metacity in XFCE (that can be alterd though) you can use the same window themes as in GNOME.

I acctually have a similar problem, after using gtk-theme-switch2 I can still switch themes to *some extent*, I can change most of the theme, but the buttons and scrollbars along with evey other clickable object are Industrial  :?  whilst the colors (only background) turn the color of the theme... very wierd.

Anyway, if you want to use metacity in XFCE (as aposed to xfwm4) click run program and type this:

```

killall xfwm4 && metacity --replace

```

then logout and save your session then login again, wam you have the same window manager as in GNOME (now you have to use gnome-theme-manager though).
If you want xfwm4 again just repeat the process but reversed (I acctually use xfwm4 in gnome instead of metacity ;-) )

---

### Post by LokeDK on 2005-08-12
Hi
Thank you for your answer. I know gnome-theme-manager is only for gnome, and XFCE has it's own.. but none of them are able to change the theme.
Hope there is a solution out there  :-?

---

### Post by rockett15 on 2005-08-27
This has happened to me also. I have a whole list of GTK themes that i'd installed and had previously used. But, now I can't change to anything but Clearlooks-Deepsky. You can change the theme in the list - but nothing actually happens other than change the metacity theme?

---

