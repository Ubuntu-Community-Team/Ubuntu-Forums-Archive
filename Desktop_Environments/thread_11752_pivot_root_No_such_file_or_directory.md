---
title: "pivot_root: No such file or directory"
date: 2005-01-19
forum: Desktop Environments
---

### Post by Serengeti on 2005-01-19
Hi,
I've a new problem with my k6-2 550 machine (previous story [here](http://www.ubuntuforums.org/showthread.php?t=11343) ). The system have worked happily for a couple of days but totay it froze again. Neither mouse nor keyboard worked so I pressed the reset button and waited for ubuntu to reload. And well, it didn't reload. It just said:
> Starting Ubuntu...
pivot_root: No such file or directory
/sbin/init: 429: cannot open /dev/console: No such file
Kernel panic: attempted to kill init!
What can I do?

---

### Post by Serengeti on 2005-01-19
Running fsck on the /boot partition helped. Thanks go to Scoon from #ubuntu @ Freenode :)

---

