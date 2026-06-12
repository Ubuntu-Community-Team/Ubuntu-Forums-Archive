---
title: "[SOLVED] How to get liferea to start in notification area on startup?"
date: 2008-12-24
forum: General Help
---

### Post by josephellengar on 2008-12-24
Gnome, intrepid.  Thanks!

---

### Post by Piratini on 2008-12-25
1. In Liferea: Tools -> Preferences -> GUI tab, tick "Show icon in system tray".
2. In Gnome panel: choose System -> Preferences -> Sessions, then add a new item to the "Startup Programs" tab.

Name: Liferea
Command: liferea
Comment: RSS feed reader

That should do the job ;)

---

### Post by josephellengar on 2008-12-25
> **Piratini said:**
> 1. In Liferea: Tools -> Preferences -> GUI tab, tick "Show icon in system tray".
2. In Gnome panel: choose System -> Preferences -> Sessions, then add a new item to the "Startup Programs" tab.

Name: Liferea
Command: liferea
Comment: RSS feed reader

That should do the job ;)

That starts it maximized.

---

### Post by Piratini on 2008-12-26
Oh. Then you need to run "liferea --mainwindow-state=hidden" instead of just "liferea".

---

### Post by pirattrev on 2008-12-28
> **Piratini said:**
> Oh. Then you need to run "liferea --mainwindow-state=hidden" instead of just "liferea".

thanks a bundle dude

---

### Post by clem11388 on 2011-07-27
> **Piratini said:**
> Oh. Then you need to run "liferea --mainwindow-state=hidden" instead of just "liferea".
Thank you kindly :-) exactly what I was looking for.

Do you or someone else know if this command can also be used for Pidgin or other apps that allow notification area hidding? Granted replacing the appropriate app name of course.

   Thank you again and God bless!!
      Clem

---

### Post by xx58 on 2011-07-29
:rolleyes: Difficult to help if used Operating system are hidden.
1. Do you have Natty Narwal - Ubuntu 11.04
a) Classic
b) Uniti
c) or other operating system

---

