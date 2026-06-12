---
title: "Problem with partition permission"
date: 2009-04-20
forum: General Help
---

### Post by snorbens on 2009-04-20
Hi,
I created a new primary partition of 10.8 Gb formatted as ext3 using gparted, to be used mainly for backups and storing some important data.

I can backup to the partition using sbackup, but when I open the partition it will not allow me to do anything such as create new folders etc. 

When I right click on the space within the disk-file browser the create folder and create document is greyed out. It is the same when I try and cut and paste. The paste is greyed out.

Have I done something wrong? or not done something when I created the new partition?

Any help please

---

### Post by cariboo on 2009-04-20
When you created the new partition, you were running gparted as root, so root owns the partition. When you use sbackup, you are running it as root also, so it has permissions to write to the partition. If you need to create partitions, you can create them by running nautilus as root, press Alt-F2 and type:

```
gksu nautilus
```

or you can make the partition mount point read/writeable, in an Applications-->Accessories-->Terinal type:

```
sudo chmod -R 777 /media/<mountpoint>
```

where /media/<mountpoint> is where you mount your partition.

Jim

---

### Post by snorbens on 2009-04-20
Thanks Jim,

I will give that a go, Thanks very much.

---

### Post by snorbens on 2009-04-20
Hi,
I just tried Code: sudo chmod -R 777 /media/disk 

/media/disk being the mountpoint

And I was able to open the folders already there,but was still unable to create a folder and as sbackup created another folder immediatley afterwards was unable to open that one. Although the other folders were still readable.

Incidentally how do I get the code showing in a box in my threads?

As you can probably guess I am a complete newbie at this.

---

