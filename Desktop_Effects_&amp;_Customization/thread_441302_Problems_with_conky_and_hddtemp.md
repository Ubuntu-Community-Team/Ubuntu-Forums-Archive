---
title: "Problems with conky and hddtemp"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by kambrian on 2007-05-12
I am currently using conky 1.4.5 with hddtemp compiled in.  When using the hddtemp feature, it reports my SATA drives as always being asleep and my ATA drive as always being at 31C.
I thought maybe it was a problem with conky but when I look at nc localhost 7634, it also says both are asleep even though sudo hddtemp /dev/sdb reports it being 38C.

Any ideas?  I changed SYSLOG in /etc/default/hddtemp to 300 thinking 0 was causing it to only poll once on boot but that did not seem to fix my issue.

---

