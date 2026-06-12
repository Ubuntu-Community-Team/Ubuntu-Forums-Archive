---
title: "Where does KDE keep it's system tray icons?"
date: 2009-10-02
forum: Desktop Environments
---

### Post by acidPython on 2009-10-02
I'm changing the default system tray (widget) icons and would like to know where all the .png's are. I've looked in /usr/share/pixmaps but only found the WICD icons.

Ideally i'd be looking for the icon for Kmix, Kwallet and possibly the battery monitor widget.

Anyone done this before?

---

### Post by user333 on 2009-10-02
I think you should get a icon theme on gnome-look (I think that there's a KDE link there, if you don't use Gnome) I have the like to gnome-look in my signature. Then extract a good theme that is similar to what you want. (A theme is usually just a bz2 or something like that) A good one** WILL** have widget icons. Then rename the icon you want to use to the same name as the one you would like to change, and replace it. When You are done replacing, re-package it. I haven't done this, but I have done it to other types of themes. I don't have KDE (I have gnome) , but I *think* this will work!

---

### Post by acidPython on 2009-10-02
> **user333 said:**
> I think you should get a icon theme on gnome-look (I think that there's a KDE link there, if you don't use Gnome) I have the like to gnome-look in my signature. Then extract a good theme that is similar to what you want. (A theme is usually just a bz2 or something like that) A good one** WILL** have widget icons. Then rename the icon you want to use to the same name as the one you would like to change, and replace it. When You are done replacing, re-package it. I haven't done this, but I have done it to other types of themes. I don't have KDE (I have gnome) , but I *think* this will work!

That's actually a pretty good idea, thanks i'll get on it

EDIT: Awesome thanks, managed to change the icons. Turns out they were in ~./kde/share/icons OR if you run kdemod
~/.kdemod4/share/icons

I had to apply a theme then tweak it to get what i wanted at first

---

### Post by user333 on 2009-10-02
Just so you know, you can do this to any theme, as long as you don't violate rights!

---

