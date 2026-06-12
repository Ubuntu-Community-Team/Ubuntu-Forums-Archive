---
title: "Gnome Startup Applications not running?"
date: 2012-04-12
forum: Desktop Environments
---

### Post by captaintrav on 2012-04-12
Ubuntu 10.04 LTS
In Gnome Startup Applications, I'm launching a couple of virtual box machines.
In the last couple of days, it stops launching them, but the rest of the applications in startup launch.
If I copy the commandline to a terminal, it launches.

VBoxManage startvm "Windows XP" --type headless

any ideas how to debug this?  I have no idea where a log might be stored.

---

### Post by souravc83 on 2012-04-13
The .desktop file for these applications might not be working properly. You can try checking the .desktop files, and see if everything is okay.

---

