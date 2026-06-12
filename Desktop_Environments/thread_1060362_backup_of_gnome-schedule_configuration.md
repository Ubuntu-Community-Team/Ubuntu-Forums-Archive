---
title: "backup of gnome-schedule configuration"
date: 2009-02-04
forum: Desktop Environments
---

### Post by nbr on 2009-02-04
Hi folks, does anybody know where gnome-schedule stores tasks to run?
I looked in /etc/cron* and found nothing there. Looked in .gnome2, nothing.
I'd like to backup my scheduled tasks.
I googled for an answered, but "schedule gnome backup" brings info about scheduled backup, not backing up schedule config.
Thanks!

---

### Post by nbr on 2009-04-30
Just found it:

/var/spool/cron/crontabs

---

