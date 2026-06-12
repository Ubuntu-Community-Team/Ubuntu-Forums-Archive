---
title: "Rename grayed out in nautilius"
date: 2012-11-11
forum: Desktop Environments
---

### Post by kerryhall on 2012-11-11
Hello,

I have this weird problem when I right click on a folder in nautilus. Ubuntu 12.04. GNOME nautilus 3.4.2. The "rename" option is grayed out, yet I can still click it and renamed folders...

I have permissions to write to the folder.

---

### Post by papibe on 2012-11-11
Hi kerryhall.

Make sure you do. Go to the parent directory and right click on the directory in which the file you want to rename resides. Click 'Properties' and select the 'Permissions' tab.

There, make sure the 'Folder access' under 'Owner' says 'Create and delete files'.

Let us know how it goes.
Regards.

---

### Post by mc4man on 2012-11-12
longstanding bug that I  guess is still active in 12.04
(though usually was a sometimes thing rather than all the time & no longer a problem in 12.10/13.04
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/973491](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/973491)

---

### Post by kerryhall on 2012-11-12
Absolutely I have perms to rename the folder.

Ahh I can see that bug report now. This was a hard bug to google for, but perhaps I should hunt around bugs.launchpad.net before posting on here though.

---

