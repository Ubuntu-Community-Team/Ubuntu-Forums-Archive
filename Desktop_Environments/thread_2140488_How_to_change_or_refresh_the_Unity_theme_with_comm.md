---
title: "How to change or refresh the Unity theme with command line?"
date: 2013-04-29
forum: Desktop Environments
---

### Post by NBPX on 2013-04-29
I'm  developing my own theme based on Radiance. It's on .themes folder on my home folder and I can change the theme manually with Unity Tweak Tool. 

I would like to update the theme programmatically with shellscript after some change on a .css file of the theme.

---

### Post by diesch on 2013-04-29
GTK theme:
```
gsettings set org.gnome.desktop.interface gtk-theme your_theme
```

Window manager theme:
```
gsettings set org.gnome.desktop.wm.preferences theme your_theme
```

---

### Post by NBPX on 2013-04-29
Thanks! 

What is the difference between [COLOR=#000000]GTK theme and Windows manager theme?[/COLOR]

---

### Post by diesch on 2013-04-29
Basically the GTK theme is about what's inside a window and the window manager theme is about the window borders.

---

### Post by vasa1 on 2013-04-29
> **diesch said:**
> Basically the GTK theme is about what's inside a window and the window manager theme is about the window borders.Is your solution limited to Unity or can users of K/L/Xubuntu use it as well?

Edit: it doesn't seem to do anything in Lubuntu 13.04. No error message in the terminal either.
```
gsettings set org.gnome.desktop.interface gtk-theme Radiance
```
(I have installed light-themes and so Ambiance and Radiance are available to me and both are functional.)

---

### Post by diesch on 2013-04-29
It uses the Gnome configuration system and works in Unity and Gnome but not in KDE, XFCE and LXDE.

I didn't check, but I guess it's basically the same as Unity Tweak Tool is doing.

---

### Post by vasa1 on 2013-04-29
Okay and thanks for clarifying!

---

### Post by NBPX on 2013-05-02
How to update the theme of a window, that is already open, without to reopen it?

This command changes the system theme, but based on preliminar tests, it is necessary to reopen the windows to see the result.

I know it's possible. The tweak tools do it.

---

