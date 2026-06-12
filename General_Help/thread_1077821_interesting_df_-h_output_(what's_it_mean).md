---
title: "interesting df -h output (what's it mean?)"
date: 2009-02-22
forum: General Help
---

### Post by mandarb777 on 2009-02-22
Hi I wasn't sure where to put this.
I am getting a funny df output.  It is showing a certain amount "used" but a lesser amount "avail"  what could account for this?

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             224G  209G  3.9G  99% /
tmpfs                1010M     0 1010M   0% /lib/init/rw
varrun               1010M  120K 1010M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M  2.8M 1008M   1% /dev
tmpfs                1010M  312K 1010M   1% /dev/shm
lrm                  1010M  2.0M 1008M   1% /lib/modules/2.6.27-11-generic/volatile

Thanks,
Dave

---

### Post by mcduck on 2009-02-22
5% of disk space is reserved for root user only on Ext3 partitions. If you run "df" as normal user that part of the disk space doesn't count as available.

edit:
The amount of reserved space can be changed, but on the root partition I would leave it as it is. The reason behind this is that the system needs some available disk space to be able to boot at all. When part of the disk space is available for rot only, normal user's can't fill the disk to the point where the machine wouldn't be able to boot any more.

---

### Post by mandarb777 on 2009-02-22
Okay, thanks.

Um, how do I get the nice formatting to copy over from terminal commands?
Thanks,
Dave

---

### Post by mcduck on 2009-02-22
Paste the text inside code tags (the "#" button when typing messages).

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              20G  8.9G  9.4G  49% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  132K 1012M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.9M 1010M   1% /dev
tmpfs                1013M   12K 1013M   1% /dev/shm
lrm                  1013M  2.0M 1011M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6              27G   17G  9.5G  63% /mnt/storage
/dev/sdb1              74G   51G   19G  73% /media/Helios
/dev/sdb2              20G  3.4G   17G  17% /media/EOS
```

they are also useful when pasting long pieces of code or other text.

---

### Post by plucky on 2009-02-22
```
Filesystem Size Used Avail Use% Mounted on
[color=red]/dev/sda1 224G 209G 3.9G 99% /[/color]
tmpfs 1010M 0 1010M 0% /lib/init/rw
varrun 1010M 120K 1010M 1% /var/run
varlock 1010M 0 1010M 0% /var/lock
udev 1010M 2.8M 1008M 1% /dev
tmpfs 1010M 312K 1010M 1% /dev/shm
lrm 1010M 2.0M 1008M 1% /lib/modules/2.6.27-11-generic/volatile

```


and your root partition is nearly full,so you should really think about creating some space before you have problems.

Good Luck

---

