---
title: "No automatic updates"
date: 2009-05-07
forum: General Help
---

### Post by shadwstalkr on 2009-05-07
Sometime after I upgraded to 8.10, automatic updates stopped working. When I run apt-get update the updater icon appears in the tray, so it seems like everything after that is working. It's just that apt is not updating regularly on it's own. Upgrading to Jaunty didn't fix it.

I don't know where the auto update is being run, so I don't know what to check (cron?). Can anyone help? I'm using Kubuntu if that makes a difference.

---

### Post by sgosnell on 2009-05-07
"sudo apt-get update" just updates the sources.list packages, it has nothing to do with OS updates or upgrades.  Run the update manager to actually get updates to the OS.

---

### Post by shadwstalkr on 2009-05-07
apt-get update refreshes my local list of what packages are available from the repositories in sources.list, then apt-get upgrade actually upgrades the packages. The update manager is a GUI for apt-get upgrade, but there should be something in the background running apt-get update (or equivalent) every day. There used to be.

Are you saying that Ubuntu has changed the behavior so that you have to manually run the update manager to see if there are any updates?  The base problem here is that I used to be automatically notified when updates were available, and now I have to remember to run apt-get update every few days or else I get no update notifications.

My guess is that a cron job somewhere was deleted, but I don't know if it was installed with the update manager package or what.

---

### Post by jflaker on 2009-05-08
to do a full upgrade as the packages become available
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by sgosnell on 2009-05-08
The update notifier can actually be run at startup, and probably was being run but now isn't.  You can run it at startup through System/Preferences/Startup Programs.  It is also accessible through System/Control Center.  This is on 9.04, and I can't remember if 8.10 is exactly the same.  The result is the same, but the exact names in the menus may have changed slightly.

---

### Post by MaxVK on 2009-05-14
Hi, I'm having the same problem, but update manager is already in my startup applications (Jaunty)

The updates work fine, but I have to remember to check or Ill never know about them. What could be wrong?

cheers

Max

---

