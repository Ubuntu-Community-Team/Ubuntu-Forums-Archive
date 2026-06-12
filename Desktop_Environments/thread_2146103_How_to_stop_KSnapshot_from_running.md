---
title: "How to stop KSnapshot from running"
date: 2013-05-17
forum: Desktop Environments
---

### Post by mbnoimi on 2013-05-17
I want to disable KSnapshot from running at startup so I went to System Settings -> Startup & Shutdown -> Service Manager but I didn't find KSnapshot name!!!

How can I disable KSnapshot at startup?

---

### Post by oldos2er on 2013-05-18
Look in System Settings, Startup & Shutdown, Autostart, is it listed there? If not, look in Session Management, tick 'Start with an empty session'.

---

### Post by mbnoimi on 2013-05-18
> **oldos2er said:**
> Look in System Settings, Startup & Shutdown, Autostart, is it listed there?
No

>  If not, look in Session Management, tick 'Start with an empty session'.
Did it... nothing changed:confused:

---

### Post by mbnoimi on 2013-05-22
I got... Voila

KSnapshot doesn’t run as daemon, KDE call it whenever the user pressed "PrtScr" keyboard button. So I simple disabled it from:

[[IMG]https://imageshack.us/a/img19/2497/customshortcutskdecontr.th.png[/IMG]]("http://img19.imageshack.us/i/customshortcutskdecontr.png/")

---

