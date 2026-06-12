---
title: "I installed XGL, now X crashes and I can't disable!"
date: 2006-10-27
forum: Desktop Environments
---

### Post by rebelfallen on 2006-10-27
I am unsure how to disable XGL. I enabled it, then rebooted and X wouldn't start. Now I can't get into X to fix anything I am stuck at the terminal. If I try to let it boot normally it runs through this loop asking me if I want to let X try to fix the settings for me. 

Anyone know how I can disable XGL?

Thank you so much in advance.

---

### Post by magicfab on 2006-10-27
did you backup the /etc/X11/xorg.conf file ?

If yes, copy th eold file over the newer one.

If no, run "sudo dpkg-reconfigure xserver-xorg" to rebuild it, then restart X / reboot.

---

