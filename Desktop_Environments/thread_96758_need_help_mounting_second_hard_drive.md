---
title: "need help mounting second hard drive"
date: 2005-11-29
forum: Desktop Environments
---

### Post by tagg3rx on 2005-11-29
Hi - I have installed a new Hard drive 
It shows up in system-admin-disks as dev/hdb but it will not let me format or add partitions.

When I try and mount it I get :
helpdesk@95-ubuntu:~$ sudo mount /dev/hdb /mnt/80gigs
Password:
mount: you must specify the filesystem type
helpdesk@95-ubuntu:~$


My fstab reads as follows
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



Its formatted ntfs at the moment but i want to reformat it to linux FS


Help plz

---

### Post by Murgle on 2005-11-29
You cannot mount a whole drive you need to mount the specific partition on the drive.  I am going to guess that the partition you want is the first one.  to do this type :
sudo mount /dev/hdb1 /mount/point

if this isn't the right partition then type "ls /dev |grep hdb" and this will list all entries in /dev that have hdb in them.

---

### Post by tagg3rx on 2005-11-29
what if there are no partitions?

helpdesk@95-ubuntu:~$ ls /dev |grep hdb
hdb
helpdesk@95-ubuntu:~$

---

### Post by tagg3rx on 2005-11-29
And shouldent I manualy add a line to my fstab refrencing it?

I would do that I just dont know what to put as type, options, dump & pass

Thanks

---

### Post by Brent Dax on 2005-11-29
[QUOTE=tagg3rx]what if there are no partitions?

helpdesk@95-ubuntu:~$ ls /dev |grep hdb
hdb
helpdesk@95-ubuntu:~$[/QUOTE]
Then it needs to be partitioned and formatted.  A good tool for this is GParted, which you can install through Synaptic or apt-get.

[edit] I believe the Disks tool will help you add the drive to fstab once everything else is properly configured, but I could be wrong.

---

### Post by tagg3rx on 2005-11-29
Parted didnt do me good but fdisk did the trick 

for future refrence of those searching for answers here was my fix


sudo fdisk /dev/hdb
    chose option N from the menu and fully partotned the drive  (defaults)
    chose option W to write the changes

sudo mount /dev/hdb1 /mnt/80gig
And now its there

Oddly enough it did have a partition on it because it's full of an old windows install

---

### Post by aysiu on 2005-11-29
Can you post the output of these three commands ```
sudo fdisk -l
df -h
cat /etc/fstab
```?

---

### Post by tagg3rx on 2005-11-29
It wasent quite working right so
I went back and did fdisk a second time and deleted the partiton and recreated it
Then i added it back -- then i mounted it agian.

After doing that i was able to use system -> admin -> disks to format the new partiton in reiserfs.

It still didnt add the line to the fstab so i added one my self just trying to mimic the ones i found in there.

The only issue I am having still is that i have to chmod 777 /mnt/80gig after each reboot.  

So still trying to figure it out a bit

Here is the info you requested::


helpdesk@95-ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        1244     9743422+   5  Extended
/dev/hda5              32        1244     9743391   8e  Linux LVM

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1      158816    80043232+  83  Linux
helpdesk@95-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                      8.8G  2.8G  5.5G  34% /
tmpfs                 189M     0  189M   0% /dev/shm
tmpfs                 189M   13M  177M   7% /lib/modules/2.6.12-9-386/volatile
/dev/hda1             228M   12M  205M   6% /boot
/dev/hdb1              77G  1.7G   75G   3% /mnt/80gig
helpdesk@95-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0    1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hdb1       /mnt/80gig      reiserfs  defaults        0       0
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
helpdesk@95-ubuntu:~$

---

