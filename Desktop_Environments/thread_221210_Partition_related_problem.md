---
title: "Partition related problem"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Sinne on 2006-07-22
Yesterday I installed Ubuntu 5.10, and I upgraded to Dapper.
The problem is it can't open the non-Linux partitions. It says that I don't have a permission to view those partitions. How do I fix this? Please help me, I'm totally new in Linux.

Thanks,
Sinne

---

### Post by Jagot on 2006-07-22
Have a read through this:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html)

---

### Post by Sinne on 2006-07-22
Thanks a lot dude. I'll try this and I'll post here if it works.:)

EDIT: Anyway, before I do that, I must assure for something. Is there any chance to lose data or damage the partitions anyhow?

---

### Post by Jagot on 2006-07-22
No - no danger - don't think it's possible to mess up mounting a partition to the point that it is of any danger to the data - the worst that will happen is that you will simply not be able to read the partition from Ubuntu if you mount incorrectly.

---

### Post by Sinne on 2006-07-23
I think I have a problem. The partitions are not named hda1, but sda1 (or 3). Anyway, I changed that in the command lines from the link above, but it's says that they are already mounted. I still can't get a permission to view the files. :/

---

### Post by Omnios on 2006-07-23
I have been usinf this for over a year and works rather well.

```
/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0
```

---

### Post by Sinne on 2006-07-23
Yeah, but it says that it's already mounted. And why I can see it sda1, not as hda1? Also I have a NTFS partition which is only for files. There's no any OS there, and I can't see it too. Yeah, it's NTFS partition so the command lines that you guys wrote it should work, but they don't. :/

What should I do? 

Thanks anyway.

---

### Post by Sinne on 2006-07-23
Anyone?

---

### Post by VirtuAlex on 2006-07-23
> **Sinne said:**
> why I can see it sda1, not as hda1?
hda for IDE drives and sda for scasi or sata or usb

---

### Post by VirtuAlex on 2006-07-23
> **Sinne said:**
> Anyone?
and give output of mount command and content of fstab to start with

---

### Post by Sinne on 2006-07-24
What is the acctual command line?

---

### Post by Sinne on 2006-07-24
I'll check this thread from time to time, to see if there's an answer. :)

---

### Post by VirtuAlex on 2006-07-24
> **Sinne said:**
> What is the acctual command line?
```
mount
```
```
cat /etc/fstab
```

---

