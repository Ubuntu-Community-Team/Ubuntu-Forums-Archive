---
title: "KDE messed up GNOME's GTK font rendering"
date: 2007-03-20
forum: Desktop Environments
---

### Post by y0ssarian on 2007-03-20
I recently gave KDE a try after using GNOME for a couple years and did not like it. After I uninstalled it, I noticed my GTK fonts in GNOME no longer rendered like they used to. Their size was too big and it did not have the OSX blurry text look like it did before. I fixed the font size by editing the ~/.gtkrc file and removing some text KDE had added, but my font still doesn't have that blurry OSX look it used to. It will still render correctly(blurry) in firefox and in my terminal; however, none of my menu's, nautilus, desktop icons, etc. do. They appear as if i had never ran 
```
sudo dpkg-reconfigure fontconfig-config
```
and changed ~/.fonts.conf. I tried reconfiguring that package again and it didn't change anything, nor did replacing ~/.fonts.conf again.

Any suggestions?

---

### Post by y0ssarian on 2007-03-25
If anyone has the same problem, try creating a new user account and logging into that. I did and saw that all of the fonts were rendered correctly so I just backed up my home directory, deleted my user and home directory, and then created a new one and restored my program preferences; however I made sure only to replace stuff that I knew had nothing to do with font rendering(.gaim, .mozilla, etc).

---

