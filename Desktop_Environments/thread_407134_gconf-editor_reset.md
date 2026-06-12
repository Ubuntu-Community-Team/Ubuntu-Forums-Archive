---
title: "gconf-editor reset"
date: 2007-04-11
forum: Desktop Environments
---

### Post by naseem on 2007-04-11
hi
 is there a way to go back to default settings of gconf-editor in case I mess it up badly?

---

### Post by ComplexNumber on 2007-04-11
> **naseem said:**
> hi
 is there a way to go back to default settings of gconf-editor in case I mess it up badly?
make a backup of the .goconf and gconfd folders in your home directory. files and folders preceded by a doty are hidden. to make them visible, (and if you haven't already go to the Edit menu in nautilus and select preferences. there you will see an option for show hidden and backup files. tick the box.
i make regular backups of my 'system' files and directories regularly. i've automated mine so that they are all backup in a directory that shows the date and time of backup. call it something like 'backup_120407_1221'(this shows the date and time of backup)

---

### Post by naseem on 2007-04-11
ok thanks that's what I'm going to do,
I have another question, if I make a backup of the directorys (to be safe) and then delate the .gconf and gconfd, at reboot do I have something like a reset of gconf-editor? like it goes back to as just installed?

---

### Post by ComplexNumber on 2007-04-11
personally, i wouldn't delete them whilst you're logged in using gnome. it may cause some strange results. at the login screen, choose .failsafe terminal' as your session. then delete them that way by using 'rm -R .gconf .gconfd'. then exit to get back to the login screen. choose .gnome. as your session. you will then find that your gconf and gconfd has completely reset to the same state as when you first installed ubuntu.

---

