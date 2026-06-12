---
title: "adding HD space to installed ubuntu system"
date: 2006-09-07
forum: Desktop Environments
---

### Post by linuxican on 2006-09-07
I'm using an installed ubuntu dapper system. the hard disk space i allocated to / is around 2.5 GB and all the other directories are also in that partition. now i'm facing a serious low disk space on my /. 
how can i add more disk space to my ubuntu system? is there any way to move some of the massive directories to another partition?
don't let me down:(

---

### Post by Ocxic on 2006-09-07
you could creat a new partiton for your /home directory, copy everything from the old /home to the new /home partition and add the partiton to your fstab. possibly you may have the choice of expanding your partition.

or/and doing the same thing that you did for your /home directory for the /usr, /bin, & /lib directories.

this depends on you situation.

---

### Post by linuxican on 2006-09-08
> **Ocxic said:**
> you could creat a new partiton for your /home directory, copy everything from the old /home to the new /home partition and add the partiton to your fstab. possibly you may have the choice of expanding your partition.

or/and doing the same thing that you did for your /home directory for the /usr, /bin, & /lib directories.

this depends on you situation.
Isn't that risky? i don't want to loose this installtion.the massive directories are the other ones not my /home.
How can i extend the partition? 
actually i'm looking for the safest way to do this.

---

### Post by Ocxic on 2006-09-08
ok scince extanding the partiton is risky you could try creating new partitons for other directories, you simply need the harddrive space, the easiest thing to do would be to iether creat new partitions on your current drive, if you have the space, or you could install a new drive, and use that. how do yu have the partitions on your system setup??

---

### Post by linuxican on 2006-09-08
here is my fdisk -l result: 

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         523     4200966    b  W95 FAT32
/dev/hda2             524        4998    35945437+   f  W95 Ext'd (LBA)
/dev/hda5             524        1696     9422091    b  W95 FAT32
/dev/hda6            1697        2869     9422091    b  W95 FAT32
/dev/hda7            2870        4042     9422091    b  W95 FAT32
/dev/hda8            4043        4577     4297356   83  Linux
/dev/hda9            4578        4641      514048+  82  Linux swap / Solaris
/dev/hda10           4642        4998     2867571   83  Linux
```

ubuntu is on /dev/hda10. i can remove my another distro on hda8 and add space to ubuntu installation.
i agree with you, i prefer to move some directories to another partition. but what would i do with moving for example /lib and /proc to another partition. should they be on separate partitions?

---

### Post by Ocxic on 2006-09-08
/usr and /proc would be the 2 best directories to put on the new partitions, check your folders for how much space they use,
then add the new partitons, by using fdisk (remember to leave extra for new stuff, more so for /usr then /proc). then all you have to do is copy/move everything to the new partition preserving the permissions and such, check man cp/mv for more info.
make the required changes to you fstab to add the new partions and there mount points wich would be /usr, /proc respectivly.

then delet eeverything in the origonal folders from a live cd and reboot with the modified fstab and the new partions and all your files will be there. with more space on /.

---

### Post by linuxican on 2006-09-20
Hey,
I did it. Thank you.
In my case there was no problem doing this. but i think there may appear problems in other cases. consider a change in partition table that may reorder the ids for each partition. for example you devide an existing partition into two or three smaller parts. doesn't that make problem in Linux system while trying to boot and load disks on its existing configurations?
I'm fine now but I'm just curious to know:)
:rolleyes:

---

