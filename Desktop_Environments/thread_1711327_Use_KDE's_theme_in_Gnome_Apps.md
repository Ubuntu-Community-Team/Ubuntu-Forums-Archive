---
title: "Use KDE's theme in Gnome Apps"
date: 2011-03-21
forum: Desktop Environments
---

### Post by kamaru44ken on 2011-03-21
Hi everyone.

I have the latest Ubuntu installed in my laptop. I have both KDE and Gnome installed. However, I prefer Gnome Desktop Environment but I want the KDE's theme (I dont know what it's called). Is there a way that I can use the KDE's theme in Gnome Apps. For example, gEdit will look like as if it is natively coded with KDE and will look something similar to KWrite. Any how-to?

PS: I dont want to use the KDE Workspace, I just want to use the KDE theme in my Gnome apps (like gedit, gnome-shell, etc.). I've been searching the net for that but I wasn't able to find one.

---

### Post by SantaFe on 2011-03-21
I know Synaptic has QTCurve, which when installed installs gtk2-engines-qtcurves that does what you want.  

> 
This package(gtk2-engines-qtcurves) together with kde-style-qtcurve aim to provide a unified look
and feel on the desktop when using KDE and GNOME applications.

This package is most useful when installed together with kde-style-qtcurve.


But not sure if it's just the color scheme it uses, or if it also brings things like styles (bespin, GTK, ect) are brought over as well. :o

---

### Post by Frogs Hair on 2011-03-21
There are some themes that come pretty close color wise  here . You may like some of the Elementary themes , I think to get the KDE application lay out you will have to use KDE. [http://gnome-look.org/](http://gnome-look.org/)

---

### Post by Zorael on 2011-03-21
Hmm. You could make a symbolic link of your **~/.gtkrc-2.0-kde4** file, which KDE sources upon session start to theme GTK programs, to also be **~/.gtkrc-2.0**, which GTK programs normally read for theming information. I'm not sure that would work but I also don't see why not.
```
$ mv ~/.gtkrc-2.0 ~/.gtkrc-2.0-old     # just to backup
$ ln -s ~/.gtkrc-2.0-kde4 ~/.gtkrc-2.0
```
Do note that this would make GNOME and KDE share GTK theming settings completely, so changes made in one will also be present in the other. If you just want to mirror the settings and not share them, just copy the **-kde4** file to the other instead of linking it.

If there is any way to add a theme in GNOME's settings, the QtCurve theme ([if installed](apt://gtk2-engines-qtcurve)) is located at **/usr/share/themes/QtCurve/gtk-2.0**. Perhaps you can just add the path in some theme configuration menu.

---

### Post by kamaru44ken on 2011-03-28
I have tried installing qtcurve but i don't know how to enable this theme. there's no option to use this unlike in kde.

---

### Post by kamaru44ken on 2011-03-28
i've tried looking at that site but haven't found one. maybe i need to search more.

---

### Post by kamaru44ken on 2011-03-28
> **Zorael said:**
> Hmm. You could make a symbolic link of your **~/.gtkrc-2.0-kde4** file, which KDE sources upon session start to theme GTK programs, to also be **~/.gtkrc-2.0**, which GTK programs normally read for theming information. I'm not sure that would work but I also don't see why not.
```
$ mv ~/.gtkrc-2.0 ~/.gtkrc-2.0-old     # just to backup
$ ln -s ~/.gtkrc-2.0-kde4 ~/.gtkrc-2.0
```Do note that this would make GNOME and KDE share GTK theming settings completely, so changes made in one will also be present in the other. If you just want to mirror the settings and not share them, just copy the **-kde4** file to the other instead of linking it.

If there is any way to add a theme in GNOME's settings, the QtCurve theme ([if installed]("apt://gtk2-engines-qtcurve")) is located at **/usr/share/themes/QtCurve/gtk-2.0**. Perhaps you can just add the path in some theme configuration menu.

hmm. im gonna try this and ill post a reply to see if this will work.

---

