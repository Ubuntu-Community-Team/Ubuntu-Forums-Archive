---
title: "GNOME most metacity themes not working"
date: 2013-01-26
forum: Desktop Environments
---

### Post by Deucalion29710 on 2013-01-26
I am using Ubuntu 12.10 GNOME Remix.  My problem is when I open my Tweak Tool and then go to Themes and I attempt to change my "Current Theme" at top (from what I understand this is the metacity theme) most of the themes do not work.  Any help is much appreciated.  :D

---

### Post by Deucalion29710 on 2013-01-28
For future users I found the solution.  Gnome 3.6 does not look in ~.themes for the metacity/mutter theme.  It looks in usr/share/themes

Because so many theme packages come with multiple theme types packaged I have opted to store them in both.

):P

---

### Post by Frogs Hair on 2013-01-28
You should be able to apply themes stored in .themes or usr/share/themes but in Gnome 3 and up the .themes folder has to be created manually in home hidden folders. Use only themes for your version of Gnome or they may not appear in the selections . If you have Gnome 3.6 use only themes for 3.6.

---

