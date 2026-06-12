---
title: "Will not mount new Hard drive"
date: 2009-04-05
forum: General Help
---

### Post by hufferd on 2009-04-05
I just bought a new 320gig internal hard drive it is a SATA drive. Ubuntu sees the drive  But when I try to open it I get an error


> Unable to mount location
Can not mount file 

then the only option I have is to hit ok 
I cant even look at properties of the drive or anything...

Anyone have any ideas?

):P

---

### Post by taurus on 2009-04-05
Have you created a partition and formatted it, filesystem?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by AllenGG on 2009-04-05
Your system does not mount a bare hard drive, it mounts the system installed.
see above post re fdisk

---

### Post by hufferd on 2009-04-05
> **taurus said:**
> Have you created a partition and formatted it, filesystem?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```


Ok well I didn't think it would read an empty drive but I am not sure how to go about changing the partition table or adding to it 

The output from fdisk is:

> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb6a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23570   189325993+  83  Linux
/dev/sda2           23571       24321     6032407+   5  Extended
/dev/sda5           23571       24321     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdb = The new drive
> Disk /dev/sdb doesn't contain a valid partition table

---

### Post by hufferd on 2009-04-05
I used Gparted and set up a partition table on this new drive ext3.... And unbunt see it now something is wrong with the permissions I can't write anything to it ?

---

### Post by taurus on 2009-04-05
Where did you mount /dev/sdb1, mount point?  You need to change the ownership of that mount point from root to your login name so you can write to it anytime you want without root privilege.

```
cat /etc/fstab
df -h
id
```

```
sudo chown -R *username*:*username* /mount_point_for_sdb1
```
Replace *username* with your login name and the actual mount point of /dev/sdb1.

---

### Post by hufferd on 2009-04-05
> **taurus said:**
> Where did you mount /dev/sdb1, mount point?  You need to change the ownership of that mount point from root to your login name so you can write to it anytime you want without root privilege.




[QUOTE]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
dan@oscar:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             178G  7.0G  162G   5% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M   96K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   92K 1007M   1% /dev
tmpfs                1007M  100K 1007M   1% /dev/shm
lrm                  1007M  2.0M 1005M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             294G  191M  279G   1% /media/disk

/media/disk ????

---

### Post by taurus on 2009-04-05
Did you add an entry in /etc/fstab for that new drive, /dev/sdb1, or did your system mount it automatically--automount?

```
sudo chown -R dan:dan /media/disk
ls -la /media
```

---

### Post by hufferd on 2009-04-05
> **taurus said:**
> Did you add an entry in /etc/fstab for that new drive, /dev/sdb1, or did your system mount it automatically--automount?

```
sudo chown -R dan:dan /media/disk
ls -la /media
```


Yep ok got it before you posted thanks ALL is working well now! :) 

Thank you for the help :)

---

### Post by hufferd on 2009-04-05
hmm it would seem that we don't mark threads as "solved" anymore --- ?

---

