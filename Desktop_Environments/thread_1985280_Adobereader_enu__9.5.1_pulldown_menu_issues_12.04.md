---
title: "Adobereader enu  9.5.1 pulldown menu issues 12.04"
date: 2012-05-23
forum: Desktop Environments
---

### Post by dreamquartz on 2012-05-23
I don't understand this one.
I installed the deb-version of adobereader 9.5.1 from the Adobe web-site on one computer, and all the pull-down menus are working fine in both the following situations:

[LIST=1]
[*]open reader and then open a file
[*]open a file by double clicking it
[/LIST]

Situation on other computer:
However reader was opened, the pull-down menus were empty, meaning they were there, but no text.
I found a solution, but only for 1. as mentioned above, being: *env UBUNTU_MENUPROXY= acroread *entered in as command of the Adobe Properties.
When opening a file by double clicking it, the pull-down menus are there, but no text.

Anyone?

---

### Post by MadmanRB on 2012-05-23
dont use trhe adobe reader plugin, its old and obsolete and you should just open .pdf's with the built in PDF reader in ubuntu

---

### Post by dreamquartz on 2012-05-23
We have to use it, because of the forms that we create form Adobe Acrobat and receive form others.

So we have no choice in the matter.

Dream

---

### Post by dreamquartz on 2012-05-23
> **dreamquartz said:**
> I don't understand this one.
I installed the deb-version of adobereader 9.5.1 from the Adobe web-site on one computer, and all the pull-down menus are working fine in both the following situations:

[LIST=1]
[*]open reader and then open a file
[*]open a file by double clicking it
[/LIST]

Situation on other computer:
However reader was opened, the pull-down menus were empty, meaning they were there, but no text.
I found a solution, but only for 1. as mentioned above, being: *env UBUNTU_MENUPROXY= acroread *entered in as command of the Adobe Properties.
When opening a file by double clicking it, the pull-down menus are there, but no text.

Anyone?

**Solution found**
[http://askubuntu.com/questions/73272/how-do-i-disable-the-global-application-menu-in-adobe-reader-9](http://askubuntu.com/questions/73272/how-do-i-disable-the-global-application-menu-in-adobe-reader-9)
The only difference with 12.04 is, that the the launcher is located @ :  /opt/Abobe/Reader9/bin/.
Therefore: *gksudo gedit /opt/Abobe/Reader9/bin/acroread*, and follow the rest

---

