---
title: "Auto suspend not working with external monitor"
date: 2014-08-29
forum: Desktop Environments
---

### Post by mejrum on 2014-08-29
Hi
I am using a Lenovo T431s with SSD disk, Ubuntu 14.04
Suspend is working as it should, except for when I have an external monitor connected - the auto suspend does not trigger. 
I have to manually put the computer to suspend.
It might have something to do with that in tweak tool, I've unchecked "Power">"When laptop lid is closed">"Suspend even if an external monitor is used". But this imo should only affect the behaviour when closing the  lid - in my case the lid is always closed.

I have in gnome control center>power set the timeout to 20 mins, and 

$>gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 
1200

What could be the cause?

---

