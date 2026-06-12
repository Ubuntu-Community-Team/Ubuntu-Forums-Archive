---
title: "Emerald Themes in Karmic"
date: 2010-02-22
forum: Desktop Environments
---

### Post by razmatt on 2010-02-22
Hi all
I have just installed Karmic with compiz and the Compiz settings manager.
I also installed the emerald theme manager from synaptic (as I often used emerald on my dreamliunx laptop) but for some reason when I open the theme manager and try to apply a theme, it just doesn't seem to work....... :confused:
Any help would be greatly appreciated
Have A Nice Day
Razmatt

---

### Post by stinkeye on 2010-02-22
Your probably still using GTK as your window decorator.
Install fusion-icon
```
sudo apt-get install fusion-icon
```

 and add it to startup applications using
```
fusion-icon -n
```
in the command box.

fusion-icon will then load at start into the notification area.
Right click on fusion-icon to change your window decorator.
There is also a menu listing to open emerald theme manager in fusion-icon.

---

### Post by Hero of Time on 2010-02-22
When you enable Compiz, it will load the Window Decorator that is set in it's plugin. Open ccsm and check that setting. If it says 'compiz-decorator', change it to 'emerald --replace'.

---

### Post by skymera on 2010-02-22
> **Hero of Time said:**
> When you enable Compiz, it will load the Window Decorator that is set in it's plugin. Open ccsm and check that setting. If it says 'compiz-decorator', change it to 'emerald --replace'.

This is how i did it.

Though i found Emerald to be generally unstable and crashing fairly often.

---

### Post by stinkeye on 2010-02-22
> **skymera said:**
> This is how i did it.

Though i found Emerald to be generally unstable and crashing fairly often.
fusion-icon does exactly the same thing with a click of the mouse and you don't have to remember the commands.

---

