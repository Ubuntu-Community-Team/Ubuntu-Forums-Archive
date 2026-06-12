---
title: "Did it crashed or did it logged out?"
date: 2008-12-05
forum: General Help
---

### Post by velja27 on 2008-12-05
Well i leave my computer at 6:50 in the morning and go to school after i come back from school around 16 i see it on Log in screen so is there some log file to check if somebody restarted it or did it crashed or did it logged out on its self?

---

### Post by squaregoldfish on 2008-12-05
The simplest thing to check is the uptime. That will tell you how long the machine has been running since it booted, so you can work out from that.

What you do next depends on what you find. If the machine rebooted, /var/log/syslog may give you some clues. There's a number of archived syslogs, so you may need to go to a previous one to find something useful). If you were logged out, the X log (/var/log/Xorg.0.log) may tell you something.

Steve.

---

### Post by velja27 on 2008-12-05
Thanks Steve,it told me enough to know what happened,but i didn't see when did season got ended but i found out that my brother putted his flash drive surfed internet and pulled it out but that does not matter right now.

---

