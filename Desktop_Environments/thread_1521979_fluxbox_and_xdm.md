---
title: "fluxbox and xdm"
date: 2010-07-01
forum: Desktop Environments
---

### Post by 19bab79 on 2010-07-01
i am having problems getting my pc to shut down after installing xdm. before i install xdm and starting fluxbox using startx, the shutdown and reboot options that i have put in my menu work fine. after installing xdm they don't work anymore. does anyone have any ideas.

here are the entries for shutdown in my menu:
[exec] (Reboot) {sudo /sbin/shutdown –r now}
[exec] (Shutdown) {sudo /sbin/shutdown –h now}

here is what i added to the sudoers file:
<user>  ALL=NOPASSWD: /sbin/shutdown,/sbin/reboot

---

