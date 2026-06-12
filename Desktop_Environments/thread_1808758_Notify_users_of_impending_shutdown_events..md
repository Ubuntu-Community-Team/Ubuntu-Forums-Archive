---
title: "Notify users of impending shutdown events."
date: 2011-07-20
forum: Desktop Environments
---

### Post by Benton Macdonald on 2011-07-20
I have used Ubuntu 11.04 and am now using 10.04, both with Gnome as the desktop environment.
This problem may also occur in Ubuntu 11.04 with Unity as the desktop environment.

I would prefer when I issue a notify-send command from /etc/crontab or any user's crontab that the notification appear on my desktop.  This does not happen.  
Neither does an echo command issued from these two crontab sources display to the terminal.

As a workaround, I have used crontab to write a message to a file.  I have then used Specto to detect when that file has changed in order to notify the desktop.

An example of the command I issue from Specto is:
notify-send Shutdown "`tail -n5 /home/var/shutdown.spc`"

---

