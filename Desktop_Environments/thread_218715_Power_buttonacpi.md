---
title: "Power button/acpi"
date: 2006-07-18
forum: Desktop Environments
---

### Post by complexgeek on 2006-07-18
I'm quite new to Ubuntu and Linux in general, so I may have missed something obvious here.
I've just installed Xubuntu on a simple HTPC (just uses VLC to play videos), and I would like the system to shutdown cleanly when I press the power button. However the system goes to sleep, instead of shutting down. I've edited /etc/acpi/powerbtn.sh to do nothing besides /sbin/shutdown -h now , and the system still just goes to sleep. Does anyone have any suggestions?

Update: I've done some more investigation and it seems that the power button event is being handled by apm, not by acpi, but I can't find anywhere to change the option to shutdown instead of standby.

Furthur update: I found out that in the BIOS the power button was set to standby. I didn't think to look there because it always worked how I wanted in Windows. So I changed the setting but now the computer instantly turns off when the button is pressed, not doing a proper shutdown. Which really isn't an acceptable solution. Any ideas?

---

