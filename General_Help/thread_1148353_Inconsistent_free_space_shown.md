---
title: "Inconsistent free space shown"
date: 2009-05-04
forum: General Help
---

### Post by ravi.xolve on 2009-05-04
Below is the output of "df -h" command on my system:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1                        10G  7.9G  1.7G  83% /
tmpfs                              751M     0  751M   0% /lib/init/rw
varrun                            751M   76K  750M   1% /var/run
varlock                           751M     0  751M   0% /var/lock
udev                              751M  152K  750M   1% /dev
tmpfs                             751M   96K  750M   1% /dev/shm
shmfs                             751M   12K  751M   1% /lib/init/rw/splashy
lrm                                751M  2.4M  748M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda2                       4.9G  4.4G  523M  90% /media/sda2
/dev/sda3                      10G  9.9G   91M 100% /media/sda3
/dev/sda5                       10G  8.8G  1.3G  88% /media/sda5
```

For /dev/sda1 it shows used + avail = 7.9 + 1.7 = 9.6G . Now where is the rest of ~400M? I am already low on disk space as you can see  #-o and it means a lot.

However this a question worth consideration.

---

