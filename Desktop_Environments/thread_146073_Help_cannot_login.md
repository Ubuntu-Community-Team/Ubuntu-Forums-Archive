---
title: "Help: cannot login ?"
date: 2006-03-17
forum: Desktop Environments
---

### Post by BigDeal on 2006-03-17
My system had utilization very high, almost 100%, and I found the process that caused it was: anacron>run-parts>backup-manager>backup-manager >tar>gzip. I tried to kill that process, but it said: 'no space left on device'. I tryied to login again but it says that system lost the user name and  'bla bla bla....contact the system administrator' ! Help: what has happened ??? :(

---

### Post by steve.horsley on 2006-03-17
The backup manager seems to be quite a normal thing to happen occasionally. No space left sounds kinda bad though. I wonder if your disk drive is full. Try booting the rescue mode and checking with **df**. If it is a disk space problem, I guess you will have to find something to delete. /var/log might contain some big logs that you don't need any more.

---

### Post by BigDeal on 2006-03-17
[QUOTE=steve.horsley]... Try booting the rescue mode and checking with **df**. If it is a disk space problem, I guess you will have to find something to delete. /var/log might contain some big logs that you don't need any more.[/QUOTE]

*- Rescue mode? how do I get into this mode?* I found it! OK 
- Can I use the Ubuntu live cd to mount the disk and delete some big files to free space?
- How do I mount the disk ? 
Thanks...

---

### Post by taurus on 2006-03-17
Assuming that you have Ubuntu on first harddrive and it has three partitions:  /dev/hda1 -> /boot, /dev/hda2 -> swap, and /dev/hda3 -> /, from the LiveCD, do
```

mkdir /mnt/ubuntu
mount -t ext3 /dev/hda3 /mnt/ubuntu
mount -t ext3 /dev/hda1 /mnt/ubuntu/boot
cd /mnt/ubuntu

```

---

### Post by BigDeal on 2006-03-18
More questions: 
- Is there a utility like windows chkdsk to check and correct disk errors ?
- How do I remove an unneeded directory in terminal mode ?
Thanks again...

---

### Post by BigDeal on 2006-03-18
I opened my big Linux book for Dummies (!) and all the answers were there. \\:D/  Thank you all for the info...

---

