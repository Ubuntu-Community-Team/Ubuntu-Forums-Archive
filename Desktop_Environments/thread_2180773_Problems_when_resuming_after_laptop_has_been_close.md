---
title: "Problems when resuming after laptop has been closed."
date: 2013-10-14
forum: Desktop Environments
---

### Post by Reuben_Williams on 2013-10-14
[FONT=verdana]I am running Xubuntu 13.04 on a Fujitsu AH530 Lifebook. I am running Xubuntu via Wubi.Whenever I open my laptop back up the following appears:

[ 7506.621015] legacy_resume(): acpi_device_resume+0x0/0x2b returns -19
[ 7506.621023] PM: Device PNP0C0D:00 failed to resume: error- 19
[17057.963605] BUG: soft lockup CPU#0 stuck for 22s! [kworker/0:1:7710]
[17057.963733] Stack:
[17057.963754] Call Trace:
[17057.963813] Code: 90 90 55 48 89 e5 f0 81 07 00 00 10 00 f3 90 81 3f 00 00 10 00

and it repeats.

What can I do to fix this?



[/FONT]

---

### Post by Toz on 2013-10-14
Hello and welcome to the forums.

These may be of interest to you:
- [Resume from standby error on Fujitsu Lifebook AH530]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/998884")
- [[Fujitsu LIFEBOOK AH530] BUG: soft lockup - CPU#0 stuck for 22s!]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1036456")

---

