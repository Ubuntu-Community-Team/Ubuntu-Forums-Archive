---
title: "Unable to avoid Insufficient disk space!!!"
date: 2009-07-11
forum: Desktop Environments
---

### Post by PrateekParekh on 2009-07-11
My df -h shows
[PHP]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              20G   19G     0 100% /
tmpfs                 996M     0  996M   0% /lib/init/rw
varrun                996M   88K  996M   1% /var/run
varlock               996M     0  996M   0% /var/lock
udev                  996M  2.8M  994M   1% /dev
tmpfs                 996M   12K  996M   1% /dev/shm
lrm                   996M  2.0M  994M   1% /lib/modules/2.6.27-7-generic/volatile
overflow              1.0M   32K  992K   4% /tmp
[/PHP]

Earlier, I removed about 3 GBs from my filesystem to make space. The "Available usage" went to about 90% from 100%. But, after some time I noticed that it again reached to 100% without me installing any additional software/packages. Also, I am not able to download any software, since I get the "Not enough space in /tmp" error message. The last action that I did which may have resulted into this error was removing the swap space. Could that really have caused this behavior? And, how should I go about fixing this?

---

### Post by merlinus on 2009-07-11
This may be useful info:

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

