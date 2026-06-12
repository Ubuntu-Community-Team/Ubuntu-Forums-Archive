---
title: "Any way to restart the Notification Area without logging out?"
date: 2009-11-19
forum: Desktop Environments
---

### Post by Donalb on 2009-11-19
Hey all,

Amongst the many issues I'm having with Karmic ( a lot, 14 at last count, maybe 10 are serious and me not an expert and getting few answers to my questions) is problems with the Notification Area Icons.

They are irregulary greyed out (grey boxes), not displayed, moved, outline only or  hovering over one show the actions or another. 
(Eg right now  where my Tracker Applet was is a grey box and hover shows Configure Displays actions). 
All the Notification Applets (except Shutdown) at the right (Network Man, Config Displays, Gnome-Do show the Appointments & Tasks info at Hover and call up the calender & clock when clicked
Since last reboot last night, most are grey boxes and the Clock Applet is hung on time & date. (Though the calender displays correct time & date when any applet icon is clicked.)  

So if there a way to restart the Notification area icons etc without logging out and back in?

Regards

---

### Post by VCoolio on 2009-11-19
Try "killall gnome-panel", the notification area is part of it. The panel will disappear and spawn right back. It would be better to solve the real problem of course, but I don't have a clue.

---

### Post by Donalb on 2009-11-19
I use an external VGA display (set as primary) connected to my laptop.
Turns out if I hit Fn+F8 to swap the displays and swap back to how I had it, all Applet icons started working. Although I lost my Clock customisation setup  and network manager icon is still screwed (as usual with Karmic).

---

### Post by jose_maria0 on 2009-11-20
When this happens to me I just remove the notification area applet from the panel and then add it again.

---

