---
title: "I/O Errors"
date: 2005-05-24
forum: Desktop Environments
---

### Post by larry on 2005-05-24
Hi Everybody,
After upgrading my kernel, this morning, I rebooted my machine.
Since it had rebooted more than 30 times from the last check, while starting up it checked the partitions for mystakes and found several damaged I/O sectors.
Is this an hardware or a software problem, first of all? Does it have anything to do with upgrading the kernel? Should I worry or can I let it go?
Last but not least, can I fix those sectors?
I am a newbie, so I am not sure that all of my questions make sense.
Thanks anybody who gives a hand.
Larry

---

### Post by alastair on 2005-05-24
It is pretty standard to do a filesystem check after N mounts (i.e. an fsck). As long as you can continue normal operation, I wouldn't worry about problems found, as long as they are fixed (should be automatic). An abnormal shutdown (power outtage, hang etc.) can cause a check with errors but the fsck should automatically correct them.

If you do NOT keep getting filesystem errors on boot, then don't worry.

---

