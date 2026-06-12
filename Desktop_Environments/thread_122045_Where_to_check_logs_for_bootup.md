---
title: "Where to check logs for bootup?"
date: 2006-01-26
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2006-01-26
I've noticed that when starting up, there a lot of... no "ok"s next to the parts being initialized, including hotplug system. Is there a log to check what is going wrong on boot?

---

### Post by az on 2006-01-26
Look in the /var/log directory - use the log tool.


You can also type
dmesg
in a terminal.

---

### Post by TheIdiotThatIsMe on 2006-01-26
I found the log tool, but unfortunately I have no idea what I'm looking at or how to find what's going wrong on boot :confused:

---

### Post by dcstar on 2006-01-26
[QUOTE=TheIdiotThatIsMe]I found the log tool, but unfortunately I have no idea what I'm looking at or how to find what's going wrong on boot :confused:[/QUOTE]
Edit /etc/default/bootlogd to read:

BOOTLOGD_ENABLE=Yes

Edit /etc/default/rcS to read:

VERBOSE=yes

reboot, and you have to use the log viewer to look at the generated log files to find any problems.

---

### Post by mettallicat on 2006-01-26
and check /var/log/menssages ou dmesg

---

