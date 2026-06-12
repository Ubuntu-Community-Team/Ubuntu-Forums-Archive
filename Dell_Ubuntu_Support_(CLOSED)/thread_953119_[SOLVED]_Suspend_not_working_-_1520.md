---
title: "[SOLVED] Suspend not working - 1520"
date: 2008-10-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ghost_ryder35 on 2008-10-19
Ok first off I know this has probably been brought up already but I have searched and have not found my solution..
Now the problem:
Ubuntu 8.10 (problem has been on 7.10 and 8.04 as well, so it is not version specific)
Dell Insprion 1520 2.2ghz Intel Core 2 Duo, 4gig ram and 4gig swap
I can not get my machine to resume from suspend.  Whenever I try, it un successfully does not come back leaving me with a black screen.  Hibernate works fine.  I am posting this right now and going to suspend the machine and try to come back... and when it does not work i am going to try too ssh to the machine from another one to see if it is just video or the whole machine... Wish me luck.  In the meantime, any ideas?

---

### Post by dizcrypt on 2008-10-20
Try [this]("http://ubuntuforums.org/showpost.php?p=5964814&postcount=3"). Maybe it is your case.

---

### Post by ghost_ryder35 on 2008-10-21
> **dizcrypt said:**
> Try to set DOUBLE_CONSOLE_SWITCH parameter of /etc/default/acpi-support file to true. For me it works perfectly.

That did the trick!

---

