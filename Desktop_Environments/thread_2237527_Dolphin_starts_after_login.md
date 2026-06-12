---
title: "Dolphin starts after login"
date: 2014-08-02
forum: Desktop Environments
---

### Post by AnotherKevin on 2014-08-02
Any one know how to stop Dolphin from starting after desktop starts?  After I log on to Kubuntu, Dolphin starts up and shows the home directory.  I've gone through the startup settings and everything else I can think of, but nothing shows Dolphin nor it's startup settings.

Thanks!  

Kevin

---

### Post by ajgreeny on 2014-08-02
I wonder if you have one or more saved sessions that cause dolphin to startup at the session start.

I have no idea where you can change any of those settings or delete saved sessions in KDE but this might give you a clue; in gtk DEs (gnome, xfce, lxde) they are in ~/.cache/sessions

---

### Post by PaulW2U on 2014-08-02
> **AnotherKevin said:**
> Any one know how to stop Dolphin from starting after desktop starts?  After I log on to Kubuntu, Dolphin starts up and shows the home directory.  I've gone through the startup settings and everything else I can think of, but nothing shows Dolphin nor it's startup settings.

I've seen problems like these before, I think I had one of my web browsers starting up for no apparent reason every time I logged in.

In "System Settings | Startup and Shutdown | Session Management | Default Leave Option", what do you have set?

I have "End current session". I'm guessing that you might have "Turn off computer" or "Restart computer" set. If so, please change to "End current session" and see if it make a difference.

It's only a guess but I hope it helps. ;)

---

