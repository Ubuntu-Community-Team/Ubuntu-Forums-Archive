---
title: "How to force windows to open on a certain screen with dual monitor?"
date: 2006-09-03
forum: Desktop Environments
---

### Post by daou on 2006-09-03
Is there a way to tell gnome to open screens on a certain display?
For example, with a dual monitor setup or a monitor+tv out setup. Currently gnome seems to open windows on an empty screen which is quite annoying when using another screen for the TV.

---

### Post by Ziox on 2006-09-04
i believe the window opens on the screen your cursor is located...

---

### Post by daou on 2006-09-05
Certain apps do, I've noticed that. But a lot of them, take for example Firefox that I open using the globe icon in the top bar opens on whichever screen is empty, or if neither are, gnome seems to throw dice and put it whereever it feels like.

---

### Post by chavo on 2006-09-05
You can try adding the --geometry argument to the commands, it will work for most apps. So e.g.
```
 gnome-terminal --geometry 80x20+1280+40 
```
will open an 80x20 gnome terminal just on the second screen assuming your first monitor is 1280x1024. Change the values to move the app wherever you wish.

There's also devilspie. This app can move windows, make them sticky, or make them skip the taskbar, etc. It's a little hard to configure bu it works well.

Or last but not least you can switch to KDE :P KDE's non-braindead window manager has these functions built in with a nice GUI configurator.

---

### Post by daou on 2006-09-05
Alright, thanks. I'll give that a shot.

---

