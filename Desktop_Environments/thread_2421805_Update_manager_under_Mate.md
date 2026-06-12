---
title: "Update manager under Mate"
date: 2019-06-27
forum: Desktop Environments
---

### Post by daniel-clement on 2019-06-27
Hello all,

My wife's brand new Dell XPS13 came with Ubuntu 18.04 preinstalled, and after some use she decided that she preferred the "old fashioned" Mate desktop. So I installed it (with the ubuntu-mate-desktop package).

It works like a charm, but we never see the update manager starting. Yet, we can start it manually, and it shows the available updates.

How could I properly set it up so that it will check for updates each time a session is opened?

TIA for any hint - best regards, Daniel

---

### Post by Dennis N on 2019-06-27
Both Gnome and Mate desktops have update settings in "Software and Updates" application, updates tab. The default settings look like the attachment. Set yours accordingly. Ubuntu (including Mate) checks daily, but by default you don't see notifications of security updates - these are handled by "unattended upgrades" system when they are detected and are installed in the background. Non-security upgrades are presented to you for installation authorization weekly.

To see the unattended upgrades, run **cat /var/log/apt/history.log** in the terminal. Unattended upgrades are identified from the Command Line shown.

From today's batch:
```
Start-Date: 2019-06-27  06:30:54
Commandline: /usr/bin/unattended-upgrade
Upgrade: libbz2-1.0:amd64 (1.0.6-8.1, 1.0.6-8.1ubuntu0.1), bzip2:amd64 (1.0.6-8.1, 1.0.6-8.1ubuntu0.1)
End-Date: 2019-06-27  06:30:55

```

---

