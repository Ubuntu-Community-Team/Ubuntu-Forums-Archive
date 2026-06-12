---
title: "Help with server going down"
date: 2009-03-11
forum: General Help
---

### Post by KayakJim on 2009-03-11
My server has been having problems lately that are causing high load and causing it to stop responding.

While I have high load the cpu utilization according to "top" is very low.

In addition, the output from "free" shows lots of available memory.

The only issue I can find is in the output of "df" where it appears I am out of space on my / partition, which is:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              4080064   3809416     63392  99% /
/dev                     10240       100     10140   1% /dev
udev                     10240       100     10140   1% /dev
/dev/sdb             433455904    248188 411189412   1% /mnt
none                   3936020         0   3936020   0% /dev/shm
/dev/sdf1            209610080 111282756  98327324  54% /vol

I'm not sure what else to check to determine why my server keeps going down so any further advice would be greatly appreciated.

---

### Post by skymera on 2009-03-11
Maybe you should free some space to at least 5-10%
This would increase performance and stop fragmentation.

---

### Post by KayakJim on 2009-03-11
That is what I thought so thank you for confirming that. Any suggestions for where to safely remove files to free up that kind of space without affecting the system?

---

### Post by skymera on 2009-03-11
Can you run 

```
 df -a 
```

That'll show us where all the space is being used up

---

### Post by KayakJim on 2009-03-12
Here are the results of :df -a":
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              4080064   3827756     45052  99% /
/dev                     10240       100     10140   1% /dev
/proc                        0         0         0   -  /proc
/sys                         0         0         0   -  /sys
udev                     10240       100     10140   1% /dev
devpts                       0         0         0   -  /dev/pts
/dev/sdb             433455904    248188 411189412   1% /mnt
none                   3936020         0   3936020   0% /dev/shm
/dev/sdf1            209610080 111359708  98250372  54% /vol
usbfs                        0         0         0   -  /proc/bus/usb
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc
securityfs                   0         0         0   -  /sys/kernel/security

```

---

### Post by KayakJim on 2009-03-13
Just a bump to hopefully get this resolved. The problem is driving me absolutely batty. :/

---

