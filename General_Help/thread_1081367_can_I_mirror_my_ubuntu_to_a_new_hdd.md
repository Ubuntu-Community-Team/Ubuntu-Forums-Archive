---
title: "can I mirror my ubuntu to a new hdd"
date: 2009-02-26
forum: General Help
---

### Post by AxelBlade on 2009-02-26
Hello every body,

my question is the following:
I have an old HDD 80Gigs that is partitioned into two, one for Ubuntu and the other for windows ( yes windows, I use it for autocad and 3ds max), how can I transfer my OS's to a new hdd, the new hdd is 160 Gig? 
I don't want to loose my data that I have on Ubuntu:( for the windows part I can do a fresh install no problem, if there's no way to do it.

Thank you for your time.

---

### Post by OneShirtChris on 2009-02-26
it is possible to image your entire harddrive, however the issue is do you have a place to store a 80gig image of your drive? you could image one partition at a time as well. check out  [partimage]("http://www.partimage.org/Main_Page"). I believe you can even image only the used space in your HDD/partition.

If you go the partition route, you need to make sure you copy the MBR (the boot partition).

---

### Post by scouser73 on 2009-02-26
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by AxelBlade on 2009-02-26
10x guys for your help , I'll try and keep you inform

---

### Post by eldragon on 2009-02-26
i would boot from a live cd, with both hdds plugged.

then
```

# dd if=/dev/sda of=/dev/sdb

```

this would mirror your old hdd (assume its /dev/sda, replace it with whatever youve got) to your new hdd (asume its /dev/sdb, replace it with whatever youve got)

after doing this, you have yo mount the partition in the new hdd containing ubuntu, and modify its /etc/fstab in order to accomodate new UUID names.

maybe /boot/grub/menu.lst needs to be updated too (if it references to uuid names)

next, start gparted and resize partitions as you see fit.

---

### Post by celltransform on 2009-02-26
You can use Partition Saver or Ghost to copy an entire hard drive to another hard drive, that'd work :D 

dd would also get it done, in a more proactive way.

---

