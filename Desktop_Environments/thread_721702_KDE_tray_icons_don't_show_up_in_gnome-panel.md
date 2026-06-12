---
title: "KDE tray icons don't show up in gnome-panel"
date: 2008-03-11
forum: Desktop Environments
---

### Post by Zeroangel on 2008-03-11
Hey all, I am a kubuntu user who needs to drop into GNOME once in awhile. Problem is the system tray icons for my favorite KDE apps (Kmail, Ktorrent, and AmaroK) sometimes do not dock themselves properly on the gnome-panel but instead show up as their own 'windows'. This is especially noticable with kmail.

How do I get them to dock properly?

---

### Post by wilberfan on 2008-03-14
I'm having this same problem--but I'm not sure it's just KDE apps?   So far, Mobloquer, XChat, Update Notification are all showing up in a separate window in the upper-left of the screen.

In the case of Mobloquer, I'm gettin a "hole" right over the Ubuntu menu!  (You can see the wallpaper underneath--right through the panel...)

All this seems to have started within the last couple of days?

EDIT: Screen capture attached

SOLVED:  I can't speak to Zeroangel's KDE problem, but MY gnome problem was solved when I ran the following:

```
sudo debconf gnome-panel
```

I'm convinced I inadvertently deleted the system tray, and this seemed to 'reset' everything...  :)

---

### Post by Akedz on 2008-05-29
this is actually happening to me in kde. recently switched to kubuntu 8.04. sometimes i log in and the system tray icons appear as they should, but sometimes they all appear as their own windows, just like the first poster. need some help because this is really annoying.

---

### Post by nailbnny on 2008-07-10
Brilliant. Thanks for the solution.  This little bug is quite annoying.

---

