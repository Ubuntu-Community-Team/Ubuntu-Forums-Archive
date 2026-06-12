---
title: "Clearing temp data?"
date: 2009-03-09
forum: General Help
---

### Post by MTeVil on 2009-03-09
I've just recently made the switch to ubuntu and was wondering if there was an easy way to clear temp data. Whilst i was an XP user i had an app installed that i configured too automate the process for me; is there any such equivalent?  

I've been told that hardy defrags after 30 days/boots so i assume that the same may be true of temp files, but i want to configure it so they clear upon shut down. Thanks in advance.

---

### Post by Tibuda on 2009-03-09
The /tmp directory is cleaned everytime you reboot, so no need to worry about that. You can find "orphan" packages if you install the package [deborphan]("apt:deborphan"), and execute deborphan in a terminal. There are yet some terminal commands you can run to clean up unneeded stuff downloaded to install packages:
```
sudo aptitude autoclean
sudo aptitude purge -y `dpkg -l|grep "^rc"|awk '{print $2}'`
```

There's a Linux application called crontab, that executes recurring tasks. You can manage it with a graphical interface, by installing the package [gnome-schedule]("apt:gnome-schedule").

Next Ubuntu release (Jaunty) will have a Janitor application so these tasks will become easier.

---

### Post by MTeVil on 2009-03-09
Ok, thank you very much for the information.

---

### Post by snova on 2009-03-09
> **MTeVil said:**
> I've just recently made the switch to ubuntu and was wondering if there was an easy way to clear temp data. Whilst i was an XP user i had an app installed that i configured too automate the process for me; is there any such equivalent?

As far as temp files go, most of them (in /tmp) will be removed when you turn off your computer.

> I've been told that hardy defrags after 30 days/boots so i assume that the same may be true of temp files, but i want to configure it so they clear upon shut down. Thanks in advance.

Kinda. Ext3 filesystems don't need to be defragmented, what it does is run a filesystem check.

---

