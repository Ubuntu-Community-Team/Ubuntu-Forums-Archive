---
title: "Using more than one HDD with Ubuntu."
date: 2006-02-04
forum: Desktop Environments
---

### Post by Airjoe on 2006-02-04
Hi.
I really don't know much about the linux file-tree-system "whatever thingy" at all. What I'm wonderring is, how can I get Ubuntu to be able to save data to a secondary hard drive? 
I haven't installed it on the first yet. I'm not sure what steps I should take. Should I just install Ubuntu with both HDD's hooked up? 
I know on windows it's as simple as formatting it to FAT32 or NTFS, hopefully it's simple for this as well.

Thanks, 
Joe

---

### Post by ipp3l1 on 2006-02-04
> Hi.
I really don't know much about the linux file-tree-system "whatever thingy" at all. What I'm wonderring is, how can I get Ubuntu to be able to save data to a secondary hard drive? 

If you have the drive connected and running, you need to **mount** it. Good instructions about mounting windows partitions [here](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions)

> 
I haven't installed it on the first yet. I'm not sure what steps I should take. Should I just install Ubuntu with both HDD's hooked up? 
I know on windows it's as simple as formatting it to FAT32 or NTFS, hopefully it's simple for this as well.
**
Thanks, 
Joe

If your HDD's are formatted as FAT/FAT32, you dont nessecarily have to format them anyhow. Ubuntu supports them quite perfectly (though it would be better to format them as ext2/ext3 for example). Ubuntu supports ntfs disks quite poorly. You can only read/execute on them, but writing is not supported. And just "hooking up" is not enough, you also need to mount them and if you want them to mount automatically on boot-up, then you have to do this :

```
sudo cp /etc/fstab /etc/fstab_backup 
sudo gedit /etc/fstab
```

And then, Append the following line at the end of file
```
/dev/hda1 /media/hdd1 vfat umask=000 0 0
```

Assuming that /dev/hda1 is the location of the partition and the local mount folder is: /media/hdd1

\\:D/

e: And yeah, I know it might feel a bit complicated at first, but after a while you'll learn ** linux file-tree-system "whatever thingy"** quite soon :D

---

