---
title: "KDE settings in Ubuntu (the one with Gnome)"
date: 2009-11-25
forum: Desktop Environments
---

### Post by Zeemvel on 2009-11-25
Hi, I use Ubuntu with Gnome, but also use a few KDE applications (e.g. KolourPaint). These KDE apps have the KDE file dialog. In that file dialog KDE does single click to open file by default. I want it to use double click. The setting to make it double click is normally somewhere in the settings under Kubuntu, but I'm not using Kubuntu, but Ubuntu, and I only find Gnome settings, no settings of KDE file dialogs.

How can I change the behaviour of the file dialog anyway?

Thanks!

---

### Post by Zorael on 2009-11-25
Open up your **~/.kde/share/config/kdeglobals** file in a text editor, and find the bit with the header **[KDE]**. If there is a **SingleClick** line there, tell it to be **false**. If not, add it. Like below;
```
[KDE]
AutoSelectDelay=-1
ChangeCursor=true
DoubleClickInterval=400
ShowDeleteCommand=false
ShowIconsOnPushButtons=true
**SingleClick=false**
StartDragDist=4
StartDragTime=500
WheelScrollLines=3
```

An alternative would be to install KDE's settings manager (System Settings, package name **systemsettings**) and change it there. You can also change it in Dolphin.

---

