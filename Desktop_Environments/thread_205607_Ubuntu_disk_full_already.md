---
title: "Ubuntu disk full already?"
date: 2006-06-28
forum: Desktop Environments
---

### Post by crag2804 on 2006-06-28
Hi all, I'm hoping someone can shed a little light on a problem I'm having. I'm new to Ubuntu and I'm having trouble with a disk that's full, the problem being that it shouldn't be. 
The machine has two physical disks. The first is an OS disk and has a 7.5Gb partition (Ext3) and a 360Mb swap file on the same disk. The other disk is a much larger backup disk that I keep all my files on. 
My problem is the 7.5 Gb drive (\dev\hdb1) is totally full and it's only got ubuntu installed on it. I haven't put anything on this drive apart from installing the OS and I can't for the life of me find out what's taking up all this room. 
This is stopping me from logging on as all but root and plenty of other things I've tried to do wont let me due to lack of space. 
Does anyone have any sugguestions as to what could be taking up this space and how to stop it. 
Thanks in advance

---

### Post by taurus on 2006-06-28
Okay, what is the output of this command from a terminal, Applications -> Accessories -> Terminal?
```

df -h

```
Will take it one step at a time...  ;)

---

### Post by crag2804 on 2006-06-28
It tells me that hdb1 is 7.4g, i've used 7.1 and it's usage is 100%. Obviously it's mounted on /

---

### Post by taurus on 2006-06-28
Can I at least see the output of that command?

---

### Post by crag2804 on 2006-06-28
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1             7.4G  7.1G     0 100% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-9-386/volatile
/dev/hdc1              76G   44G   29G  61% /crag
root@ubuntu:~#

Edit: Apols, I was posting from my windows machine previously.

---

### Post by taurus on 2006-06-28
How about the content of /etc/fstab?
```

more /etc/fstab

```

---

### Post by crag2804 on 2006-06-28
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /crag           ext3    defaults        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
root@ubuntu:~#

EDIT: thanks for the help but bedtime now. I'll check back again tommorow after work. Obviously I can't (yet) access this machine from the net.

---

### Post by yage on 2006-06-28
Well your /home partition is under /dev/hdb1, so whats on your /home?... might the problem be there? maybe a stupid question but...

---

### Post by crag2804 on 2006-06-29
Thanks but my home is practically empty, only 2 items of 200 or so kbs

---

### Post by jgcamp99 on 2006-06-29
Trying to run a modern day OS on a 7.5 GB hdd partition ? That's not enough space, I set mine to 20 GB minimum. at least you haven't done anything on it, so delete the partition make more empty space if it's available and start over with a clean install. The live cd is a minimalist temporary approach to Linux, but to do a hdd install implies permanence, give it the storage space it deserves.

---

### Post by Dubbayoo on 2006-06-29
This is true but it shouldn't be full already. Find out what is actually taking up the space with this.

sudo du -sh /*

---

### Post by crag2804 on 2006-06-29
It isn't a partition, it's a physical disk with only 7.*Gb on it. That should be plenty to run an OS on. My big bloaty windows installation complete with a good few months of programs is only slightly over 7Gb (Takes up a nice chunk of my raptor but not too much). 
That's exactly what I needed thanks dubba. It's let me see that my brother (who says he doesn't use this machine) has accidentaly put 5.5Gb of backup on this drive by mistake. It should be on the backup drive. Cheers very much!

---

