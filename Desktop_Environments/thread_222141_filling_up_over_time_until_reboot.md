---
title: "/ filling up over time until reboot"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-07-24
If I leave my laptop on for a long time (i.e. about 8hours or so) I start to get messages telling me that / is filling up.  These messages stop when I reboot however, leading me to believe it's some kind of logging that is occuring that gets wiped when I reboot.

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             4.9G  4.5G  158M  97% /
varrun                505M  120K  505M   1% /var/run
varlock               505M  4.0K  505M   1% /var/lock
udev                  505M  120K  505M   1% /dev
devshm                505M   32K  505M   1% /dev/shm
lrm                   505M   18M  487M   4% /lib/modules/2.6.15-26-k7/volatile
/dev/hda4              28G   21G  5.5G  80% /home
/dev/fuse              40G   36G  4.1G  90% /media/hda1

```

I really cannot work out what is going on.  Any pointers?

---

### Post by Paerez on 2006-07-24
there is a handy command, "du" which will give you disk usage information. If you do:
```
du -sh /*
```
it will give you the usage in each folder. Then, see which folder fills up fast. If it is logs, then try:
```
du -sh /var/log
```
when you boot and when it fills. Then we can see where it's filling.
Also watch /tmp.

---

### Post by gray-squirrel on 2006-07-24
> **Paerez said:**
> 
Also watch /tmp.

I was wondering about /tmp.

Also. . . Lunar_Lamp. . . would it be possible to list what programs are running when this happens?  Sometimes a program have an open file which may end up getting deleted, but does not cause to the file to be freed up on the hard disk.  (I think I have that worded correctly).

---

