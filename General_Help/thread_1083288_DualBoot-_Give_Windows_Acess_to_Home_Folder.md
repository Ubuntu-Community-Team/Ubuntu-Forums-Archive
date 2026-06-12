---
title: "DualBoot- Give Windows Acess to Home Folder"
date: 2009-02-28
forum: General Help
---

### Post by Amerinidiot1231 on 2009-02-28
I have my system set up as a Dual-Boot between Windows Vista and Ubuntu 8.10.  Is there a way I can make my Home Folder, or more preferably my 'Music' folder, visible and editable to Windows Vista?

---

### Post by taurus on 2009-02-28
Windows as a default cannot access ext3 filesystem.  In fact, it doesn't even see or detect it.  However, fs-driver would allow you to access your ext3 partitions while in windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

