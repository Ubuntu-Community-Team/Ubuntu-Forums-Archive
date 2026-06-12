---
title: "problem with session stuff..."
date: 2009-06-12
forum: General Help
---

### Post by gilang on 2009-06-12
[IMG]http://lh3.ggpht.com/_FsThl7_2zm0/SjH_Q1JejDI/AAAAAAAAAUc/g4QwnK6PlvA/s400/Screenshot-1.png[/IMG]


as you can see on the image above...my Meter Screenlet is already running. but, there is no Meter Screenlet in the current session on session preferences...

i dont know, maybe beacause of this..everytime when i try to login to my desktop the meter screenlet not automatically start up even though i set this screenlet to automatically start at login...

it also happen to another screenlet except clock, calendar, slideshow and sidebar. 

how do i fix this? i want all my screenlet to automatically start when i set them...is session the problem? because, when i try to login using filesafe gnome i dont have problem with this...

it would be nice if you can help me...thank u.

---

### Post by gilang on 2009-06-28
problem solved...by myself :P...

i knew the problem is with my session stuff.

i found this file, "session" file on folder: /home/"your account name"/.gnome2

when i open it, there is some missing startup of my screenlet...so i add it manually...


i also found some screenlet got wrong startup script in it, such us:
RestartCommand=python -u /usr/share/screenlets/Pager/PagerScreenlet.py

it should like this to work:
RestartCommand=python /usr/share/screenlets/Pager/PagerScreenlet.py > /dev/null

dont forget to change both of the "num_clients", on filesafe and default session.

then i did edit the startup programs script on session preferences to get it work well, uncheck the "automatically remember running applications when logging out", and click "remember currently running application"

---

