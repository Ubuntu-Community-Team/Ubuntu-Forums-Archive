---
title: "mount a second hard drive"
date: 2009-03-17
forum: General Help
---

### Post by geo75 on 2009-03-17
I'd like to mount the partition from /dev/sdb and I am not sure how to do that let alone do it permanently

can you help - below is a list of all partitions

```

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8f06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18657   149862321   83  Linux
/dev/sda2           18658       19452     6385837+   5  Extended
/dev/sda5           18658       19452     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00084e3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19452   156248158+  83  Linux


```

running

```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

```

---

### Post by taurus on 2009-03-17
Open a terminal and edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   2
```
I assume it is ext3 filesystem.  Then save it.  Now, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

---

### Post by drs305 on 2009-03-17
Adding it to fstab is probably your best bet.

Backup fstab and open for editing:
```

sudo cp /etc/fstab /etc/fstab.old
gksudo gedit /etc/fstab

```

Add this entry:
```

/dev/sdb1 ext3 /mnt/[COLOR="DarkRed"]yourmountpoint[/COLOR] defaults 0 2

```

Create the mount point you entered above, and make yourself the owner:
```

sudo mkdir /mnt/[COLOR="DarkRed"]yourmountpoint[/COLOR]
sudo chown -R [COLOR="DarkRed"]yourusername:[/COLOR] /mnt/[COLOR="DarkRed"]yourmountpoint[/COLOR]

```

Run this command. If you get no output/error messages, everything is fine.
```

sudo mount -a

```

---

### Post by Nano_ext3 on 2009-03-17
In your case, lets say we are going to mount your drive to the typical "/mnt" folder.  The code would be as follows:

```
sudo mount /dev/sdb1 /mnt
```

Thats all there is to it!  You should not have permissions error when copying or adding files to this mount point, if you do, use the terminal and the "sudo cp" command with whatever will not copy.

Note, if you pulled the drive before safely removing it (always right click the drive an "unmount" or in windows "safely remove" in the lower right hand tray), you might have to "force" the drive.  This typically will NOT hurt the drive, but if you have lots of sensitive data on that drive, boot back into windows and safely remove it.  Here is the code:

```
sudo mount /dev/sdb1 /mnt -o force
```


Cheers!


-Nano

---

### Post by geo75 on 2009-03-17
thanks taurus - i can now access this drive
```

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             141G   58G   76G  44% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  248K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  104K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb1             147G  188M  140G   1% /media/sdb1
```

---

