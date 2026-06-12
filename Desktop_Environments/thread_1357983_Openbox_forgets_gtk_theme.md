---
title: "Openbox forgets gtk theme"
date: 2009-12-17
forum: Desktop Environments
---

### Post by mooreted on 2009-12-17
I can set a GTK theme for my windows in Openbox, but every time I log back in, OB "forgets" the theme and I have to set it again.

Is there a way to make OB play nice with GTK themes?

---

### Post by VCoolio on 2009-12-18
How do you set it? If you have gnome-settings-daemon running at login then it should remember what you set with gnome-appearance-properties. Else you can set your theme in ~/.gtkrc-2.0 like this: gtk-theme-name = "theme-name". 
If you don't have gnome-settings-daemon as startup application and you set your theme every time with gnome-appearance-properties, then you could make gnome-settings-daemon start by default. It's started automatically if you run gnome-appearance-properties.

---

### Post by mooreted on 2009-12-18
Thank you; that was the problem. gnome-settings-daemon was not starting when logging into OB. I'll add that to my autostart.

---

### Post by VCoolio on 2009-12-18
> **mooreted said:**
> Thank you; that was the problem. gnome-settings-daemon was not starting when logging into OB. I'll add that to my autostart.

It's up to you, but I prefer using the .gtkrc-2.0 file; you can use lxappearance to change gtk and icon themes, it will edit the file for you. Saves you a process running all the time.

---

### Post by mooreted on 2009-12-20
> **VCoolio said:**
> It's up to you, but I prefer using the .gtkrc-2.0 file; you can use lxappearance to change gtk and icon themes, it will edit the file for you. Saves you a process running all the time.

Good point :)

Thanks again.

---

