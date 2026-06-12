---
title: "shutdown"
date: 2006-06-09
forum: Desktop Environments
---

### Post by kariopto on 2006-06-09
Hi.. I'm using Ubuntu dapper and Xfce, and I'd like to be able to shut down my computer by just pressing the power button, but when I press the button it goes back to the login screen.. I think its because of gnome-power-manager... and if it its, i wouldn't mind disabling it from running on startup (if its safe.. i don't know).. 
Any help would be appreciated
Thanks!

---

### Post by aysiu on 2006-06-09
Try ```
sudo aptitude update
sudo aptitude install gksu bum
gksudo bum
``` and then uncheck the box for the power manager.

---

### Post by kariopto on 2006-06-09
I did that... but the only option is to stop acpid, and then the button does nothing at all.. and if I start acpid and kill gnome-power-manager then when i push the button, the computer shuts down... but how do I stop gnome-power-manager from starting every time I turn on the computer?

---

### Post by aysiu on 2006-06-09
You're right--it's not in BUM. It's in Sessions.

---

### Post by kariopto on 2006-06-10
Nope... it's still there... I'm using xfce4.. I removed it from sessions.. I tried removing it with synaptic, but it says I have to remove ubuntu-desktop and gnome-session too.. and that's not right.. how can I stop it from loading every time xfce4 starts??
Thanks!

---

### Post by aysiu on 2006-06-10
Maybe you can create a new session besides the default session?

---

### Post by kariopto on 2006-06-10
I hadn't thought about that... how do I add a new session?

---

### Post by aysiu on 2006-06-10
Shoot. I just logged into XFCE. There doesn't seem to be an easy way to create a new session.

Maybe you can modify your existing one, though. It appears to live in the /home/kariopto/.cache/sessions folder. Mine is called *xfce4-session-ubuntu:0*.

---

### Post by kariopto on 2006-06-10
I couldn't stop it from loading at startup... i was starting to think it was impossible.. but.. ha!.. I made it non-readable.. and now it doesn't load... I know its a very sloppy way of fixing it but it was driving me crazy, and i dont use gnome-power-manager anyway
Thanks a lot for your help!.. it turned out to be a weirder problem than i thought..

---

