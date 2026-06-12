---
title: "Dindn't unmount external HDD caused no space to home"
date: 2009-01-24
forum: General Help
---

### Post by orduek on 2009-01-24
I'm running Mythbuntu 8.10 
I have about 12gb on the home directory and /var/lib partition of about 488gb

After connecting an external HDD (WD passport) I wasn't able to unmount it properly. 
Ofcourse i pulled it out (stupid me).
Now I found that my home directory has almost no free space, although I can't find out what causing it. I didn't installed or downloaded some big thing.

here is my fdisk -l:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f3ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460       60801   476664615    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sda6            1584       60801   475668553+  83  Linux
ormetal@HTPC:~$ 

```

any ideas?

---

### Post by caljohnsmith on 2009-01-24
How about from the Live CD do:
```
sudo fsck -yCM /dev/sdaX
```
And replace sdaX with your home partition. I would do it from the Live CD to make sure the home partition is not mounted. Then do:
```
sudo mount /dev/sdaX /mnt
df -h
```
Where sdaX is your home partition, and see if you have the free space back. Let me know how that goes.

---

### Post by orduek on 2009-01-24
SO, you mean I should do it from liveCD the go back to normal installation, right?

---

### Post by orduek on 2009-01-24
OK,
The problem was that mythtvfrontend.log took 8.2gb!!!
I deleted it and everything OK now.
thanks.

---

### Post by Yashiro on 2009-01-24
That's a spectacular log.

---

### Post by orduek on 2009-01-25
Indeed, I can't believe that was the problem.

---

