---
title: "Startup programs"
date: 2012-03-29
forum: Desktop Environments
---

### Post by seastick on 2012-03-29
I've added cairo clock and gpe-clock into the startup applications (System - Preferences - Startup Applications) and although I've tried it with both the full path to the command and just with the command itself, neither start when I log in.  If I go to a terminal I can start them manually with the same command.  

What is a likely solution.

Ubuntu 10.04 LTS
Gnome 2.30.2

Any help most appreciated.

---

### Post by mikewhatever on 2012-03-29
You might want to try adding a little delay, for example:

```
X-GNOME-Autostart-Delay=10
```

The autostart entries should be in .config/autostart/, so edit them with nano or gedit and add that line.

---

