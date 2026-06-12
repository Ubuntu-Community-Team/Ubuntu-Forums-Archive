---
title: "How to make gnome setup defaut?"
date: 2009-12-31
forum: Desktop Environments
---

### Post by btiend on 2009-12-31
This may be a "stupid" question, but how do you make your gnome setup(how the panels are orginized, where the icons are, background, themes, etc.) default so that when you make another user it is same? I tried modifying the root... but it still comes up as the normal 2 panel setup with human as the theme.

---

### Post by 3Miro on 2009-12-31
This is actually a good question. I suppose you can try to copy/paste your .gnome_something folders into the /home/newuser folder. All the settings for all the apps are in the .something folders, but I am not sure which ones specifically.

---

### Post by btiend on 2009-12-31
That could work... but I was hoping to make it automnagically when I create an new user... are there defaults folders for gnome somewhere in the filesystem?

---

### Post by pritamps on 2009-12-31
Hey, 

The ~/.config directory and ~/.gconf and ~/.gnome have most of your settings. So just copying them over to your new user will give him those settings.

I'm not sure how to do it automatically though since these folders are specific to users.

You should try and copy the contents of .gnome to /usr/share/gnome and simlarly for the other directories (except config) and see what happens. That could work.

---

### Post by 3Miro on 2010-01-01
> **pritamps said:**
> Hey, 

The ~/.config directory and ~/.gconf and ~/.gnome have most of your settings. So just copying them over to your new user will give him those settings.

I'm not sure how to do it automatically though since these folders are specific to users.

You should try and copy the contents of .gnome to /usr/share/gnome and simlarly for the other directories (except config) and see what happens. That could work.

This may work, however, you should backup the old folders first before you overwrite anything.

---

### Post by pritamps on 2010-01-01
Oh yes...Backup Backup Backup! :)

---

