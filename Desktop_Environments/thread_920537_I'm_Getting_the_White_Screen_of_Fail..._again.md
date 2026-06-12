---
title: "I'm Getting the White Screen of Fail... again"
date: 2008-09-15
forum: Desktop Environments
---

### Post by Jordanwb on 2008-09-15
So I got Ubuntu onto an LVM with XP on another partition. I installed ATI's video drivers for my videocard. I restarted, and almost after X started I got the White Screen of Fail.

I tried going into recovery to uninstall the fglrx driver but I noticed that the installer removed the VESA driver from xorg.conf How do I get rid of the fglrx driver without having to completely reinstall Ubuntu?

[Edit]I guess this should go under Desktop Effects & Customization.

[Edit #2]Boot into recovery mode and run "apt-get purge xorg-driver-fglrx", you can use "remove" instead of "purge". But it doesn't really solve the problem of why it happens.

---

