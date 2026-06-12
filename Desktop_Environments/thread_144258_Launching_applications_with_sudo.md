---
title: "Launching applications with sudo"
date: 2006-03-13
forum: Desktop Environments
---

### Post by John Jason Jordan on 2006-03-13
I use KDar for backups to my 60 Gb USB pocket drive. KDar will give constant error messages and refuse to back up a lot of files unless I launch it with sudo. I can do this fine from the command line, but it doesn't work in the application launcher in the panel. That is, I created a menu item in the panel and for the launch command, instead of just "kdar" I made it "sudo kdar." But when I click on it to launch KDar nothing happens. No error messages, no flickering screen, just absolutamente nada.

I assumed that doing this would pop up a box asking for my password before launching the app, as it does if I want to launch Synaptic or other such utilities. How do I mimic the command line "sudo kdar" in the applications drop-down list?

---

### Post by jasay on 2006-03-13
[QUOTE=John Jason Jordan]I use KDar for backups to my 60 Gb USB pocket drive. KDar will give constant error messages and refuse to back up a lot of files unless I launch it with sudo. I can do this fine from the command line, but it doesn't work in the application launcher in the panel. That is, I created a menu item in the panel and for the launch command, instead of just "kdar" I made it "sudo kdar." But when I click on it to launch KDar nothing happens. No error messages, no flickering screen, just absolutamente nada.

I assumed that doing this would pop up a box asking for my password before launching the app, as it does if I want to launch Synaptic or other such utilities. How do I mimic the command line "sudo kdar" in the applications drop-down list?[/QUOTE]
In gnome you use "gksudo" to get the password box.  Is KDar for KDE, or more importantly, are you running in KDE?  If so it's somehting different, ksudo maybe.  I don't use kde so I don't remember.

---

### Post by Sutekh on 2006-03-13
Use ```
gksudo kdar
```(GNOME)
or```
kdesu kdar
```(KDE)
instead.  This will get you the dialog box to enter your password.

---

### Post by jasay on 2006-03-13
[QUOTE=Sutekh]```
kdesu kdar
```[/QUOTE]Yeah, that one.  Thanks for the reminder.

---

