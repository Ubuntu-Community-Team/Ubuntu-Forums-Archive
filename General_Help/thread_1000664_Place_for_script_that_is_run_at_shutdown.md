---
title: "Place for script that is run at shutdown"
date: 2008-12-03
forum: General Help
---

### Post by maddis on 2008-12-03
I'm running Ubuntu on a bit unnormal hardware. Everything works fine except ACPI cannot turn the power off. I have my own program that does the trick, but I'm not sure what is the right place to call that program.

I saw that there has been discussion before about scripts that are called at startup and at shutdown, but it seems that the haven't gone in to actual distribution. 

Or is there a place that is executed when shutdown is executed? Of course it needs to separate reboot from shutdown so it won't power of the system when user just wants to reboot.

---

### Post by gTinker on 2008-12-03
I remembered seeing something about this recently so I did a forum search with the keywords, script and shutdown. The following thread has the information you are asking for.
[http://ubuntuforums.org/showthread.php?t=990796&highlight=script+shutdown](http://ubuntuforums.org/showthread.php?t=990796&highlight=script+shutdown)

---

### Post by maddis on 2008-12-03
This seems to be what I was looking for. Thanks. Some how I managed to forgot rest of the runlevels and looked only into default runlevel.

---

