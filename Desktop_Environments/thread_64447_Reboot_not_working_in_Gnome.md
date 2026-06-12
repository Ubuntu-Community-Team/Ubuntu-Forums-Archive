---
title: "Reboot not working in Gnome"
date: 2005-09-11
forum: Desktop Environments
---

### Post by jakev383 on 2005-09-11
I have been making a lot of changes to Ubuntu to make it more my liking - installing new programs, recompiling new ipw2200 drivers, etc.
Anyway, now my reboot command no longer works.  The shutdown and hibernate work, but when I select reboot, Gnome goes away and I'm left at a root prompt in TTY1.  If I type reboot there, it reboots like it's supposed to.  In an effort to fix this, I thought that maybe the laptop-tools I installed changed something, so I chmod 755'ed /sbin/halt reboot poweroff and this did not fix it.  I added these commands in sudoers, and still no go. I normally do not use X (everything is console driven at work), so I'm not sure where to start with Gnome to fix this.
Anyone have any ideas, or a direction to point me to?
Thanks in advance.

---

### Post by jakev383 on 2005-10-12
Never did find a solution...  I installed Breezy, and the problem has not reappeared.

---

