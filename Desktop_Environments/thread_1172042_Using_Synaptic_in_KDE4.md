---
title: "Using Synaptic in KDE4"
date: 2009-05-28
forum: Desktop Environments
---

### Post by Neo Adventist on 2009-05-28
Hello!  I'm currently using KDE4 in Kubuntu 9.04

As a graphical package manager, I really prefer Synaptic over Adept or Kpackagekit.

Not wanting to download half of Gnome just to get Synaptic in KDE4, I did this:

```
 sudo apt-get install --no-install-recommends synaptic 
```

Synaptic works great as always.  But without the Gnome libraries, Synaptic is now butt-ugly and looks like a Win95 app.  XD

Is there some way of making Synaptic appear more KDE4-ish?  synaptiK?

---

### Post by Tibuda on 2009-05-28
In Gnome, if I switch the Qt theme to QGtkStyle, my ugly Qt applications will mimic my Gtk+ theme. Maybe there's something like that for Qt too.

EDIT: You have to install the gtk-qt-engine package, and change the Gtk+ theme to GtkQtEngine.

---

### Post by I_can_see_the_light on 2009-05-29
Yes, install gtk-qt-engine like danielrmt suggested, then you should be able to change the style of your gtk apps by opening system settings > appearance.

Then link the file .gtkrc-2.0-kde4 in your home folder to /root/.gtkrc-2.0

Like this: ```
sudo ln -s ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0
```

Edit: For security reasons it's better to ```
sudo cp ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0
``` but then you have to do that every time you change your kde theme.

---

### Post by Neo Adventist on 2009-05-29
Ahhhhh, much better on the eyeballs!  Thank you both!  :D

---

