---
title: "KDE application launcher cannot find applications"
date: 2016-09-28
forum: Desktop Environments
---

### Post by daniii10 on 2016-09-28
I started using KDE Neon lately and I'm having an issue with the search in the launcher and krunner (both have the problem).
When I'm searching for an app like Firefox or KWrite, I see only files in the result, the app is not shown. It's happen with all apps. The search is finding only files.
Is anyone know how to fix this? I tried to open a new user to see if the problem is local, but unfortunately it's global and it's happening in any user.
I think the problem started after I did an update (which mess up also the screen locker but I managed to fix it by reinstalling the package of the screen locker). I couldn't find a solution in Google.

I'm running the latest version of KDE Neon.

---

### Post by daniii10 on 2016-10-01
I did some research on the internet and I found out that in 'system settings' under 'plasma search' all the plugins (also known as runners) are there except 'applications', so I can't turn on applications search because it's not there.
I'm trying to figure out how to install the application runner for several days but no luck. It could be deleted by mistake with the update when I did autoremove after the update.
Is anyone know how can I get it back?

---

### Post by daniii10 on 2016-10-02
I found the solution!
If anyone have the same problem try to reinstall plasma-workspace.
Run this commands
```
sudo apt-get update
sudo apt-get install --reinstall plasma-workspace
```

That's what I did then reboot and problem fixed.

---

