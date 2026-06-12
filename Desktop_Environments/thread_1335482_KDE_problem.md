---
title: "KDE problem"
date: 2009-11-23
forum: Desktop Environments
---

### Post by Mr Nemo on 2009-11-23
[LEFT]I recently installed KDE on Ubuntu just to check it out. Everything installed fine and I can switch between Gnome and KDE without any problems. The problem is that KDE seems to have hijacked my pointer icons and I can't switch them back even if im in gnome. Ive tried to change it from appearances in Ubuntu and also in KDE but it keeps defaulting back to the default KDE pointer icons when I start gnome. Any way to fix this?
[/LEFT]

---

### Post by sbrown1992 on 2009-11-23
System > Preferences > Appearance

Go to the Theme tab
Click the Customise Button
Then go to the pointer tab, and choose a pointer :)

---

### Post by Zorael on 2009-11-23
You can also change the X default, which is for instance used in the greeter (login screen) before any user-specific settings have been read.
```
$ sudo update-alternatives --config x-cursor-theme
```
"oxy-white" is the KDE default. I imagine you know better than me what the GNOME default is.

---

### Post by Mr Nemo on 2009-11-23
Thank you Zorael.

---

