---
title: "&quot;Cannot Remove Directory&quot; when unmounting an external  USB Hard Disk"
date: 2007-10-11
forum: Desktop Environments
---

### Post by OscarWabbit on 2007-10-11
hi

i often get an error message "Error Removing Directory" when unmounting a USB Hard Disk on the desktop using Unmount under Feisty.

sometimes when the disk is switched back on and auto-remounts, it gets mounted as /media/DISK2_ instead of /media/DISK2 and that stops another application from working because it is on the wrong mount point.

has anyone else seen this problem and what can i do about it?

thanks

---

### Post by safaricity on 2007-10-11
user-rights?
and do you have gnome-user-mount installed?

---

### Post by FuturePilot on 2007-10-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95368](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95368) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had a similar problem.
The solution for me was to open a root Nautilus
```
gksudo nautilus
```
and navigate to /media/ and press Ctrl+H to show hidden files.
Then I deleted .hal-mtab
You might want to give that a try.

---

