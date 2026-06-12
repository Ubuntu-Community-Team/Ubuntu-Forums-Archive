---
title: "Turn off passwd promt when accessing internal HD"
date: 2008-04-04
forum: Desktop Environments
---

### Post by steffinb on 2008-04-04
Hey guys, I just installed Xubuntu and it rocks but there's one major annoyance.

I've got 2 internal drives. One 40 gig with the OS installed on it and one 320 gig with my personal files.

Every time I try to open my 320 gig HD (is mount the correct terminology?) it prompts me for the password. 

Does anybody know how to turn this feature off?

---

### Post by warp99 on 2008-04-04
The drive is not mounting in your fstab. When you click on the drive it's asking for you sudo password because it's not mounted. Type the following command:

```
cat /etc/fstab
```

and post the results to this thread.

---

### Post by hellomoto on 2008-04-04
I am also having the same problem.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=02eea92b-1a10-4d4a-81c5-09b7d7f55447 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=40bbaa97-5afc-45c3-9310-59897280f465 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
mark@mark-desktop:~$ 
```

---

### Post by warp99 on 2008-04-04
> **hellomoto said:**
> I am also having the same problem. 

I'll use your fstab as the example. The first thing is we need to determine where the partitions are and we do this with the following command:

```
cat /proc/partitions
```

The output should look similar to this:

```
cat /proc/partitions
major minor  #blocks  name

   8     0  195360984 sda
   8     1   78124063 sda1
   8     5  113282284 sda4
   8     6    3951958 sda5

```

Now the drive is listed as /dev/sda, see the total sectors. We also have the root partition as sda1 according to the fstab (/dev/sda1) and the swap position (dev/sda5), but were missing /dev/sda4. That's the partition we want to mount at boot time. So lets mount that drive partition to an empty directory. Since we need an empty directory to mount we should just create a new one:

```
sudo mkdir /media/sda4
```

then mount the directory:

```
sudo mount /dev/sda4 /media/sda4
```

if everything goes to plan you should be able to see the files on that partition. Next we need to determine the file format. If you know what the file format is you can skip this part. Issue the following command:

```
sudo mount |grep /dev/sda4
```

and the ouput:

```
/dev/sda4 on /media/sda4 type ext3 (rw)
```

the file format is the one after type, which is 'ext3'. Now we need one more piece of information, the uuid of the partition. You can mount the drive partition using the /dev/sda4 convention, but it's better to use the uuid. Issue the following command:

```
sudo vol_id -u /dev/sda4
```

and the output:

```
8666449e-04fe-4963-8d8a-db0fb88b9e91
```

Your drive partition of course will have a different uuid. Now that we have all of the neccesary information we can add this line to our fstab. First back up the fstab:

```
sudo cp /etc/fstab /etc/fstab.backup
```

then open the fstab for editing:

```
sudo gedit /etc/fstab
```

If you don't have Ubuntu, but Kubuntu or Xubuntu, then use 'kate' or 'nano' instead of 'gedit'. We need to add the following lines to the fstab:

```
#/dev/sda4
UUID=8666449e-04fe-4963-8d8a-db0fb88b9e91 /media/sda4     ext3    defaults    0    2 
```

so the fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=02eea92b-1a10-4d4a-81c5-09b7d7f55447 /               ext3    defaults,errors=remount-ro 0       1
#/dev/sda4
UUID=8666449e-04fe-4963-8d8a-db0fb88b9e91 /media/sda4     ext3    defaults    0    2
# /dev/sda5
UUID=40bbaa97-5afc-45c3-9310-59897280f465 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Save the file, then unmount the /dev/sda4 partition we mounted earlier:

```
sudo umount /dev/sda4
```

then issue mount all drives command:

```
sudo mount -a
```

and all of your partitions are mounted and will be mounted when your reboot. If you need to add more partitions repeat the same steps, but increase the <pass> number in the fstab by 1. Hope this helps.

---

### Post by Dzoni^mne on 2008-04-06
Hi, i think i have same problem,i cant open my sda1 and sda5 i was looking around forum and trying but i didn't do anything.This is the error  :You do not have the permissions necessary to view the contents of "sda5"  (same for sda1)

---

