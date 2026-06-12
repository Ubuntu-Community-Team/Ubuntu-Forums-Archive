---
title: "[SOLVED] Problem when starting up"
date: 2008-03-17
forum: Desktop Environments
---

### Post by brocky102 on 2008-03-17
Hi when i start Ubuntu (Gutsy) it is in 1280x1024 but after i login it defaults back to 640x480. I set it to default to 1280x1024 but after a restart it goes back to 640x480. This is only a new install with all the latest drivers and everything. I've tried finding someone else that is having a similar problem but it doesn't look like it. Anyone have any ideas?

---

### Post by Patb on 2008-03-17
Brocky, check the file /etc/X11/xorg.conf.  Under the "screen" section, there should be the line beginning "Modes".  Mine has the line:
```
Modes		"1024x768" "800x600" "640x480"
```If you need to edit it, in a terminal, type 
```
sudo gedit /etc/X11/xorg.conf
```Let us know if this solves the problem.

Cheers, Pat.

---

### Post by brocky102 on 2008-03-18
Nah it resets the xorg.conf file on reboot by the looks as i change it to just 1280x1024 and it still comes on at 640x480

---

### Post by NakedSnake on 2008-05-04
try saving the session when you reboot

---

