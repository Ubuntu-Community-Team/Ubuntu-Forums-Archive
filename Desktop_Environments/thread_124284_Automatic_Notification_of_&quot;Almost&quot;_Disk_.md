---
title: "Automatic Notification of &quot;Almost&quot; Disk Full?"
date: 2006-02-01
forum: Desktop Environments
---

### Post by squidward on 2006-02-01
I recently had a server log file run amok.  It filled the disk, and I had had to log in with grub to fix.  A PITA for sure.

I fixed the underlying problem that was causing giant log files (two parts of Oracle agitating each other).

For the future... what can I run in the background to notify me by e-mail or screen message when the disk fill passes a certain level?

---

### Post by mark_g on 2006-02-01
You could use disk quotas. You just need to add them to your /etc/fstab file, it's really simple and I think there's a way to get a message when your disk is almost full by using them.

---

### Post by squidward on 2006-02-02
Thanks... that's a starting point.

---

### Post by az on 2006-02-02
[https://launchpad.net/distros/ubuntu/+source/gnome-session/+bug/4791](https://launchpad.net/distros/ubuntu/+source/gnome-session/+bug/4791)

---

