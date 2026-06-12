---
title: "RAID &quot;md: array md0 already has disks!&quot; results in total data loss?"
date: 2009-06-03
forum: General Help
---

### Post by StrangeWill on 2009-06-03
I was able to do a sudo mdadm --assemble --scan, now the drives appear empty!

What is going on? Why did the drives drop in the first place? Why are they NOW EMPTY?

Did they mount wrong? Is there a way to recover data? HELP!

---

### Post by StrangeWill on 2009-06-03
WHEW, pulling the hot swap drives + rebooting + doing it again and the data is there... had a heart attack.

Anyway, every time i reboot and the hot swap drives are not removed, I still get the "md: array md0 already has drives", I must pull the drives at reboot, boot, then manually add them, what gives?

---

