---
title: "Restore option"
date: 2009-12-30
forum: Desktop Environments
---

### Post by jeevanrak on 2009-12-30
I am using ubuntu 8.0 version,we have any option to restore when it is corrupted,like windows.:confused:

---

### Post by x33a on 2009-12-30
no we don't have any system restore option for linux.

what problem are you facing?

---

### Post by premamotion on 2009-12-30
Two things are helping here... in my opinion... first is to have /home in another partition on the disk, and the second is to have a file with all the packeges installed on the system.
 (you can have it with the command **dpkg --get-selections > package_list.txt** and when you want to install everything from this list just use
 **dpkg --set-selections <package_list.txt apt-get dselect-upgrade**)

Hope that helps and answers your question.

---

