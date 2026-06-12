---
title: "Automatic Sudo"
date: 2005-09-11
forum: Desktop Environments
---

### Post by Christoff UK on 2005-09-11
Hi, 

Not sure if this is possible, but I run firestarter with the gksudo command at startup automatically, however I obviously have to enter my password, this becomes quite a annoynance when having to do it every time I boot, and was wondering if I could someone how get it to automatically negotiate my password? Thus elimating the need for me to enter it.

Cheers
Chris

---

### Post by Waqas on 2005-09-11
Perhaps you can find something over here:-

[http://ubuntuguide.org/#usersadministration](http://ubuntuguide.org/#usersadministration)

---

### Post by Christoff UK on 2005-09-11
It doesnt really help as i was looking for it to only have effect on firestarter, to which location does firestarter exist? i couldnt see it in the /usr/bin?

---

### Post by recce101 on 2005-09-12
My Firestarter launches automatically on each boot with no action required. If you launch it manually (thru the terminal) you should get a Firestarter dialog. In the preferences check the box "Start/restart firewall upon program startup".

---

### Post by JLTB on 2005-09-12
if you really want to try ... check out a command called "expect" (sudo apt-get install expect, then man expect).

It's neat, you can do crazy stuff with it.

---

### Post by wellery on 2005-09-12
There's a how to on this here. [http://www.ubuntuforums.org/showthread.php?t=26483&highlight=firestarter+startup](http://www.ubuntuforums.org/showthread.php?t=26483&highlight=firestarter+startup)

---

