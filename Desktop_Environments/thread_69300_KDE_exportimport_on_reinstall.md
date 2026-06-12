---
title: "KDE export/import on reinstall"
date: 2005-09-26
forum: Desktop Environments
---

### Post by ManLord on 2005-09-26
Does KDE have a export/import wizard for personal files/settings? I know I can take a backup of /home/user, but what about settings? How well do KDE, and none KDE applications use /home/user/.app/ folder for settings? Because I know from windows that usally the document and settings folders usally gets awfully bloated and filled with non relevant files(files that I don't need on a computer change/reinstall)

Could someone please explain how this works in linux? Thanks!

---

### Post by mlomker on 2005-09-26
Yeah, there is a lot of bloat in there.  If you remove programs without using the *complete removal* option then even more so.  I haven't seen any cases where graphical apps didn't store their config in /home.

I have a little [write-up]("http://www.ubuntuforums.org/showpost.php?p=361622&postcount=4") on backing up from the command-line.  KDE does have a front-end applet for tar, but like most things in linux it just executes the same commands in the background.

---

