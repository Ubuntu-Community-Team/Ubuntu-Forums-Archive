---
title: "Logging notifications"
date: 2010-10-09
forum: Desktop Environments
---

### Post by Darkade on 2010-10-09
Hello! Is there a way to log the notifications that show up in the desktop? For example:

a)When pidgin notifies you that you have a new message can you "save" that notification?
b)When transmission informs you that a torrent finished downloading can you log that notification?

Or if you can't log them can you make a script that "catches" those notifications? 

**What I want to do is that when a certain notification pops it triggers an app or a script.** So if I can log the notifications I can "watch" for changes in the log file and trigger something; or if can "catch" the notification I could also do that.

I think it can, somehow, be done with d-bus but I can't find my way around the documentation. Can someone point me in the right direction?

Thanks

---

### Post by Darkade on 2010-10-09
I found that the ***Notify-OSD*** (The ubuntu notifications daemon) logs the latest notifications in **$HOME/.cache/notify-osd.log** and that means I can do what I want to do in Ubuntu. But for the default daemon? "***notification-daemon***"

I use both arch and ubutu so I'd like to know if there are other logs.


[NotifyOSD Documentation]("https://wiki.ubuntu.com/NotifyOSD#Logging%20notifications")

---

