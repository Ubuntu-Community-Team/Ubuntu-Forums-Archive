---
title: "space on hard disk"
date: 2012-01-26
forum: Desktop Environments
---

### Post by T S Rao on 2012-01-26
I am using Ubuntu 11.10 Oneiric Ocelot and it has been working alright and updating like charm.  Now it says there is not enough disc space when there are updates to be taken.  The updates require about 180Mb of space whereas the disc has actually more than 30 Gb.  It says to go to 'sudo apt-get clean' and emply thrash and remove any temporary packages used by earlier programs.  I do not know how to do this.  Please help me.

---

### Post by WthIteh on 2012-01-27
Free space is dependent on your partitioning too. Most the times, packages require enough free space in /usr (for example free space in /home does not help).
Post result of
```
df -h
```to see how much free space is available in different places.

The apt-get caches downloaded packages at /var/cache and that cache could be cleared (freeing some space) by
```
sudo apt-get clean
```

---

### Post by T S Rao on 2012-01-30
> **WthIteh said:**
> Free space is dependent on your partitioning too. Most the times, packages require enough free space in /usr (for example free space in /home does not help).
Post result of
```
df -h
```to see how much free space is available in different places.

The apt-get caches downloaded packages at /var/cache and that cache could be cleared (freeing some space) by
```
sudo apt-get clean
```
 
I could locate and read your message and I am sorry to say that it is not helpful to me.  In fact, there is actually 37Gb of space available on that particular drive when seen in the properties of that drive.  Please help me.

---

### Post by WthIteh on 2012-01-31
> **T S Rao said:**
> In fact, there is actually 37Gb of space available on that particular drive when seen in the properties of that drive.  Please help me.
Posting output of "df -h" could be more helpful for diagnosing the issue because it's possible that the drive properties do not reflect the real available sizes (e.g. in case of LVM drives or when /, /var, and /usr folders are in different partitions, etc.).
BTW, you could check these two cases too:

[LIST=1]
[*]According to size of updates, I can guess that it's updating kernel too (right?). The new kernel requires empty space in /boot partition. If this is the case and /boot is full, you could select an old kernel to be uninstalled for freeing disk space (old kernels do not get uninstalled automatically),
[*]You can also try "apt-get clean", "apt-get update", and then "apt-get upgrade".
[/LIST]

---

### Post by T S Rao on 2012-02-08
Thank you very much for the time you have spared to help me.
T S Rao

---

