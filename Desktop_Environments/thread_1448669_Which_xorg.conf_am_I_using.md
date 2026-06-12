---
title: "Which xorg.conf am I using?"
date: 2010-04-06
forum: Desktop Environments
---

### Post by travisl_10 on 2010-04-06
Looking in the directory /etc/X11, I see the xorg backups and 'failsafe', I have a xorg.conf and xorg.conf.fglrx-0. The configurations inside are different. 

How do I know which one I am using? I have an ATI card using the fglrx driver.

---

### Post by me13221 on 2010-04-06
I believe X always loads /etc/X11/xorg.conf .  The only exceptions would be if a different file were specified on the commandline, or if you specifically selected something like 'failsafe mode' at the gdm login prompt.

---

