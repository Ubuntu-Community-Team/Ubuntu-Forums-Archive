---
title: "Won't log into X after automatic upgrade to 9.10"
date: 2010-01-22
forum: Desktop Environments
---

### Post by erinspice on 2010-01-22
I used my package update manager to upgrade to 9.10 this morning, and now I can't get X to start or login. I type my password into the GDM login box, and it looks like it's going to log in for about 3 seconds. Then it just goes right back to GDM with no errors or messages.  What can I do?

ETA: Oops. Mod, feel free to move this to Installations and Upgrades if you want.

ETA again: dmesg says seahorse-agent is segfaulting.

---

### Post by erinspice on 2010-01-22
[https://bugs.launchpad.net/ubuntu/+source/seahorse-plugins/+bug/429322](https://bugs.launchpad.net/ubuntu/+source/seahorse-plugins/+bug/429322)

I found this [fixed] bug that may be related, but apt says my seahorse-plugins packages is already the latest version.  However, dpkg says I have 2.28.1-0ubuntu3 when the bug report says this was fixed in 2.28.1-0ubuntu4. Where do I get that version if apt-get can't find it?

ETA: Doesn't matter. I found and installed it and it didn't change a thing. So what else can I look for to be able to log into X?

---

### Post by erinspice on 2010-01-22
I can log in as root. I get a desktop, but no window manager, bars, or application menus.

ETA: Wow, I'm just talking to myself here! I got my window manager and desktop to start by running "sudo dpkg-reconfigure ubuntu-desktop."  Still can't log in as non-root.

---

