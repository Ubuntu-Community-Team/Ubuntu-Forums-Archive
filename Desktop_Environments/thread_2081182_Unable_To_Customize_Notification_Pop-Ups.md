---
title: "Unable To Customize Notification Pop-Ups"
date: 2012-11-06
forum: Desktop Environments
---

### Post by brenttauro on 2012-11-06
Hi. I installed Xubuntu on my old HP Pavilion ze4900 a while ago. I then installed the Ubuntu and Ubuntu 2D sessions and uninstalled the Xubuntu session. So I'm running Ubuntu 12.04 LTS.

Anyway, I don't like the fact that the notification pop-ups which I loved, look like boring solid grey bubbles with a white outline and close button - barely visible *(see attached screenshot)*. The pop-ups close on click. I've already tried customizing it with a patched version of NotifyOSD as mentioned here:
[INDENT][http://www.webupd8.org/2012/06/closable-movable-notifyosd.html](http://www.webupd8.org/2012/06/closable-movable-notifyosd.html)
[/INDENT]...but to no avail. As a matter of fact, it doesn't affect the pop-ups at all!

[CENTER][B]How can I get the original Ubuntu/Unity notification pop-ups with bubble fade outs to work?
[/B][/CENTER]

---

### Post by zombifier25 on 2012-11-06
notify-osd was replaced by Xfce's own notifying system, xfce4-notifyd. Try uninstalling xfce4-notifyd completely.

---

### Post by WorLord on 2012-11-08
> **zombifier25 said:**
> notify-osd was replaced by Xfce's own notifying system, xfce4-notifyd. Try uninstalling xfce4-notifyd completely.

That was it.  Fixed the problem for me.

---

