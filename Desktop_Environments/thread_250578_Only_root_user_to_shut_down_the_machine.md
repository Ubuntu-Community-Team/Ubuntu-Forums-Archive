---
title: "Only root user to shut down the machine"
date: 2006-09-04
forum: Desktop Environments
---

### Post by savimonty on 2006-09-04
Hi,

My distro dapper, shows the shut down button to all users....!

I do not want non-root users to shut the machine down ...

I want only sudoers to have the "Shut Down" button!

HOW do I do this?

Thanks a million.
Savio.

---

### Post by hexion on 2006-09-04
> **savimonty said:**
> Hi,

My distro dapper, shows the shut down button to all users....!

I do not want non-root users to shut the machine down ...

I want only sudoers to have the "Shut Down" button!

HOW do I do this?

Thanks a million.
Savio.

You have to add to /etc/sudoers these lines:
> your_user_name ALL= NOPASSWD: /sbin/reboot
your_user_name ALL= NOPASSWD: /sbin/shutdown
 
To edit that file, do not use nano, or gedit, just type this command:
> sudo visudo 
Bye

---

### Post by hexion on 2006-09-04
Mmm, I didn't understand you...
What I wrote above let your user shutdown or reboot from console...

But I don't know how to avoid users shutdown with gnome GUI...

---

