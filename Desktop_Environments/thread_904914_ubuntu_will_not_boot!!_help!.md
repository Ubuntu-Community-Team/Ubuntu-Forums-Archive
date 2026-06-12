---
title: "ubuntu will not boot!! help!"
date: 2008-08-29
forum: Desktop Environments
---

### Post by banned bandit on 2008-08-29
When I boot ubuntu i get the following error:

An automatic file system check fsck of the root filesystem failed.  A manual fsk must be performed, then the system restared.  The fsck should be performed in maintenace mode wuth the root filesystem mounted in read-only.

The root filesystem is currently mounted in read-only mode.  A maintenance shell will now be started.  Afer performing the system maintenance, press control-d to terminate the maintenace shell and restart the system.



How do I go about fixing this?

Cheers,

Roy

---

### Post by falcon61102 on 2008-08-29
Have you attempted to boot up in the Recovery Mode of your kernal?  It's normally the second option on the GRUB boot list.

---

### Post by sidewinder46 on 2008-08-29
If you can not enter in Recovery mode, boot up the live cd.  then run:
```

fsck

```
This will take care of the mounting problem.

---

### Post by banned bandit on 2008-08-30
I managed to fix it. followed this thread to fix it:

[http://ubuntuforums.org/showthread.php?t=789454&highlight=%2Fdev%2Fsda3%3A+UNEXPECTED+INCONSISTENCY%3B+RUN+fsck+MANUALLY](http://ubuntuforums.org/showthread.php?t=789454&highlight=%2Fdev%2Fsda3%3A+UNEXPECTED+INCONSISTENCY%3B+RUN+fsck+MANUALLY)

---

### Post by sayakb on 2008-08-30
Please mark the thread as solved.

---

