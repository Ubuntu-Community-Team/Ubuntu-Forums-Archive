---
title: "Can I reconnect a disconnected bash shell?"
date: 2008-12-15
forum: General Help
---

### Post by GeekLove_JavaStyle on 2008-12-15
Hello All,
How can I reconnect to a bash session?  My session got disconnected.  When I reconnect, I can see my old session when I hit "ps".  

Is there a way to reconnect to that old session?

Thanks in Advance,
Steven
Harvard Children's Hospital

---

### Post by nielz on 2008-12-16
I don't know of a way to do that. There is a program that allows for this and much more terminal goodness though. The program is called [screen]("http://www.gnu.org/software/screen/") and it's a "virtual terminal multiplexer". It allows you to detach or attach the your terminal at will. It'll also stay running after you logout. 

Screen also has lots of other nice features among which is the option have multiple terminals in the same terminal, complete with split-screen and taskbar.

---

### Post by cpare on 2009-04-23
Bump - is there away to this wihtout this software?

---

### Post by HighFrictionZone on 2009-07-09
Also bump. I'm already well sold on the virtues of screen, however I was not running screen at the time my connection dropped, a shame because I was running upgrades. I'd rather not kill off the session and have to do repair work, especially if there's a way to reconnect to the existing session and finish the upgrade.

Is it at all possible to do this, or should I just cut my losses and manually repair things?

---

### Post by bab1 on 2009-07-09
> **HighFrictionZone said:**
> Also bump. I'm already well sold on the virtues of screen, however I was not running screen at the time my connection dropped, a shame because I was running upgrades. I'd rather not kill off the session and have to do repair work, especially if there's a way to reconnect to the existing session and finish the upgrade.

Is it at all possible to do this, or should I just cut my losses and manually repair things?

Try this at the terminal```
fg
```

if what your running is in the background (bg) then this will bring it to the foreground (fg)

---

