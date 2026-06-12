---
title: "Huge Problem Please Help"
date: 2005-08-21
forum: Desktop Environments
---

### Post by carajean on 2005-08-21
ok for some reason i just loggied in to ubuntu and the screen is very dark actually extremely dark.  I dotn think its my vid card cause when i go turn on my comp everything up to ubuntu is crystal clear. when the nvidia splash screen comes on its a ll multicolored i can barely see what i am typing right now. please help me out i have no idea where to start.

---

### Post by adwait on 2005-08-21
If this were Windows, I would say the drivers must be corrupted and advise a reinstallaion of drivers..........but in Linux, I dunno if that happens!

Just a thought........but try this:
```
 sudo dpkg-reconfigure xserver-xorg
```

You'll have to do this outside GNOME, ie: in a terminal...

---

