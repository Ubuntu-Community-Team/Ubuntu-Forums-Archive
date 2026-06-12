---
title: "Ubuntu doesn't recognize my new Ext2 partition"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Wormsie on 2006-07-20
I've been using ubuntu for a few months now, and I really like it in general. I like it more than Windows XP anyway. I'd like to move almost completely from Windows to Linux.

The biggest problem is this: I've been running out of space on my Ubuntu partition, so I decided to repartition my F: drive with Partition Magic 7, which contains most of my data files. Now I have two partitions there, a Windows NTFS -partition sda1, and a Ext2 partition sda5. But when I browse the files with Disks Manager on Gnome, it says:

Access path: none
Size: 48,81 GiB (Free space not available)
Status: Inaccessible

What to do? Clicking "Enable" doesn't help. Or changing the access path to something and then clicking Enable.

---

### Post by halfvolle melk on 2006-07-20
You could try to use gParted instead (of Partition magic).

---

### Post by Wormsie on 2006-07-20
Tried that too, wasn't of much help yet. Do you suggest merging back the two partitions (sda1 and sda5) and then creating a new partition with gParted?

Also, should I do something to /etc/fstab ?

---

### Post by halfvolle melk on 2006-07-20
> **Wormsie said:**
> Tried that too, wasn't of much help yet. Do you suggest merging back the two partitions (sda1 and sda5) and then creating a new partition with gParted?
I suggest you remove and recreate the partition that is not recognised correctly, using gParted.

> Also, should I do something to /etc/fstab ?
You'll need to add a line if you want it to mount at boot.
Something like
```
/dev/sda5       /mnt/extra-partition           ext2    defaults        0       2
```

---

### Post by adam.tropics on 2006-07-20
curious...why ext2?

---

### Post by Wormsie on 2006-07-20
Because that's the only Linux file system Partition Magic recognizes. :) I thought I could reformat it as ext3 in Linux.

Thanks for the tips, I'll try that.

---

### Post by Wormsie on 2006-07-20
Otherwise OK, but I seem to be unable to write to the partition. Any tips?

---

### Post by halfvolle melk on 2006-07-20
This is likely to be because you are not the owner or otherwise don't have the right permissions. You can verify this by browsing to the place where you have mounted [extra-partition]. For now lets assume it's mounted in /mnt/extra-partition. Right-click it and click properties. It will probably say that root is the owner. You can fix this by issuing
```
sudo chown -R Wormsie /mnt/extra-partition
```
Or I'm alltogether incorrect :)

---

### Post by adam.tropics on 2006-07-20
You will not be able to change anything (partition related) on any partition, if that partition is mounted. Makes sense if you think about it!

---

### Post by Wormsie on 2006-07-21
Thank you so much, it worked! I tried to do that from the graphical interface but didn't succeed. :D

---

