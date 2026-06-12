---
title: "HDD mount problem in intrepid"
date: 2009-01-01
forum: General Help
---

### Post by morganGDFP on 2009-01-01
Hey all!
I have two HDDs inside my cabinet (SATA2 or whatever its called) and I want both of them to be mounted automatically when I start the computer.
Actually what I really want is that they are treated as one big HDD. I really have no need to know that there are two HDD units, but I don't know if that is possible.

Option number 2 is to just have them both to mount automatically. If I start the PC right now I have to open up nautilus and then I can see both my drives in the column on the left hand side, as soon as I can see that they are both mounted.

I have a shared folder on my second HDD and the windows machine that is on the same network cannot access the folder until it is mounted on my ubuntu machine.

I really need to learn more about mounting and how that works in ubuntu.. There must be a text file that you can edit and that will decide which things to mount what they are called..
Please point me in the right direction..

Oh by the way I am running intrepid on an AMD64 bit machine if that has anything to say..

Thanks and a happy new year!

---

### Post by prshah on 2009-01-01
> **morganGDFP said:**
> want both of them to be mounted automatically when I start the computer.

From 8.10 onwards, hdd partitions not mentioned in the fstab are handled dynamically (ie, loaded / mounted when required).

If you want them to be automatically (statically) mounted, you need to add the specific information to the /etc/fstab file. For example, you need to add an entry such as ```
# /dev/sda6
[color=red]UUID=AB707BCE707F8DE8[/color] [color=blue]/media/sda6[/color]     ntfs    [color=green]defaults,umask=007,gid=46[/color] 0       1
```

In the above example (your details will differ), you can find out the correct UUID for your partition (the part in red) using the command```
sudo blkid /dev/sda6
``` (Replace sda6 with the actual partition device ID in your case).

You should also create the mount point (the part in blue)```
sudo mkdir /media/sda6
sudo chown root:plugdev /media/sda6

```

If you're trying to mount an ext3 partition (linux partition) you should change the partition type to ext3 (instead of ntfs) and options (the part in green) to ```
defaults,relatime,auto
```

Post back if you need more details. A look at your current partition/hdd structure will be helpful; give the following commands from a terminal (Applications-Accessories-Terminal)```
sudo fdisk -l
mount
```

---

### Post by morganGDFP on 2009-01-04
Cheers, prshah that helped a lot.
I added my two HDDs to the /etc/fstab file like this:

```
# /dev/sdb1
UUID=9c2b6552-efc8-4962-ada7-7cee19385218 /media/sdb1     ext3    defaults,relatime,auto 0       1

# /dev/sdd1
UUID=e129d955-f740-4b62-8b9e-976f0758a4ce /media/sdd1     ext3    defaults,relatime,auto 0       1
```

And now they get mounted automatically when I start up the computer.

There might be a few problems left though..
/dev/sdd1 is an external USB HDD that I have named sdd1 in my fstabs file however, when I run fdisk -l it tells me it's called /dev/sdc1..
And Ubuntu seems to be doing a routine check of the drive everytime I start the computer up.
But other than that it seems to be working perfect. I could just remove that drive from the fstabs file and let it be handled automatically, the main thing is that I got my internal SATA2 drive mounted automatically at startup.

But just out of curiosity, is there something different that needs to be done just because this is an external USB drive or what am I missing here..?

Here is the output of sudo fdisk -l

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb52cb52c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18801   151019001   83  Linux
/dev/sda2           18802       19457     5269320    5  Extended
/dev/sda5           18802       19457     5269288+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00077ce0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   83  Linux
```

And mount

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /media/sdb1 type ext3 (rw,relatime)
/dev/sdc1 on /media/sdd1 type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/morgan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=morgan)

```

---

### Post by logos34 on 2009-01-04
> **morganGDFP said:**
>  I could just remove that drive from the fstabs file and let it be handled automatically, the main thing is that I got my internal SATA2 drive mounted automatically at startup.

But just out of curiosity, is there something different that needs to be done just because this is an external USB drive or what am I missing here..?


like you say, you can simply let the system automount usb:

[https://help.ubuntu.com/community/Mount/USB#Automounting](https://help.ubuntu.com/community/Mount/USB#Automounting)

It will do so at '/media/disk' with user access permissions

The system is actually seeing the disk according to it's UUID, but it would appear sdc is the correct drive letter (you only have 3 disks)

---

