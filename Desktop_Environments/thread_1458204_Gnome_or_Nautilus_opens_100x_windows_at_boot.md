---
title: "Gnome or Nautilus opens 100x windows at boot"
date: 2010-04-19
forum: Desktop Environments
---

### Post by arrimapirate on 2010-04-19
I just started having this error with my Ubuntu 10.04 installation. Every time i turn my computer on and log in (as normal user, will try root in a few mins) hundreds of "starting home folder" warnings start in the bottom panel. No windows are opened, only the words saying they are opening. After this goes on for about 10 miniutes, they start to go away but my desktop is empty and i cannot open any folders from the places menu. All this time my CPU usage is at 100% and never goes down. I have tried reinstalling nautilus but that did not help. I will attempt to find the log file for it next. 

Can anyone help with this?

Edit:
This does not affect the root account

Edit:
This also does not happen if i unmount the drive i use as /home and log onto the /home on the root drive

---

### Post by arrimapirate on 2010-04-20
I have added a new user and now log in as that user. This is a temporary fix, and is very annoying. I could attempt to set Thunar as my file manager but i do not know how.

Ill call it solved. Deleted my user, created a new user with the same name and a chown -R to my old home folder.

---

