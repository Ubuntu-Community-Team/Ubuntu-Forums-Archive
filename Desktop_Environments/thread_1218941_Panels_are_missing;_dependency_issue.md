---
title: "Panels are missing; dependency issue"
date: 2009-07-21
forum: Desktop Environments
---

### Post by mehta on 2009-07-21
Xubuntu 9.04 loaded ok but after the first update, I think, the top and bottom panels have disappeared.
I am able to run the panel using xfce4-panel and through that learnt that there is a problem with my installation.  When I close the terminal window the panels disappear again.
On running apt-get I got the following output:
mehta@mehta-laptop:~$ apt-get check
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
What should I do next?  Please help.

---

### Post by john.nicholls on 2009-07-22
After you get the panel back by running xfce4-panel you need to save the session so it'll come up again on reboot. You can do this by right-clicking a blank part of the panel and selecting Restart. Alternatively, go to Settings | Session and Startup and tick Automatically save session on logout.

---

