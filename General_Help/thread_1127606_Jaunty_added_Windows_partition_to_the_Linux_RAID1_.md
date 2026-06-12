---
title: "Jaunty added Windows partition to the Linux RAID1: don't know how to remove it!"
date: 2009-04-16
forum: General Help
---

### Post by andy80 on 2009-04-16
In my PC I've the following disks:

/dev/sda1 --> Windows XP
/dev/sda2 --> Ubuntu Jaunty

/dev/sdb1 + /dev/sdc1 --> / of Ubuntu Intrepid in RAID1
/dev/sdb2 + /dev/sdc2 --> /home of Ubuntu Intrepid

After I've installed Jaunty, to test it, I've installed mdadm, copyed the mdadm.conf from Intrepid and after a reboot I was able to use my /home/ from Intrepid in Jaunty too.

Until this point, all is ok!

The problem is that Jaunty thinks that /dev/sda1 (Windows XP - NTFS partition) is part of the RAID. I cannot neither mount /dev/sda1 partition from Jaunty because system says it's in use.

Look into /proc/mdstat:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdb2[0] sdc2[1]
      260839296 blocks [2/2] [UU]
      
md0 : active raid1 sdb1[0] sdc1[1] sda1[2](S)
      48829440 blocks [2/2] [UU]
      
unused devices: <none>
```

and look this:

```
andy80@andy80-jaunty:~$ sudo vol_id /dev/sda1
[sudo] password for andy80: 
ID_FS_USAGE=raid
ID_FS_TYPE=linux_raid_member
ID_FS_VERSION=0.90.0
ID_FS_UUID=5c7c967b:58c2a816:7ff42eed:7c82eb40
ID_FS_UUID_ENC=5c7c967b:58c2a816:7ff42eed:7c82eb40
ID_FS_LABEL=
ID_FS_LABEL_ENC=
```

Linux thinks is a RAID partition, but it contains NTFS file system and Windows inside it can boot and work properly.

Luckly the data contained in /dev/sda1 is still there and Windows is working but I think it could be damaged by the Linux RAID1.

How can I exclude /dev/sda1 from the RAID?

This is my mdadm.conf:

```
andy80@andy80-jaunty:~$ cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=5c7c967b:58c2a816:7ff42eed:7c82eb40
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=594efe5c:7ee2560b:86bd34d3:2fc2d4bd

# This file was auto-generated on Tue, 07 Apr 2009 12:00:21 +0200
# by mkconf $Id$

```

I hope someone can help me, I don't want to loose my data on /dev/sda1

---

### Post by fjgaude on 2009-04-19
Well, it looks like /dev/sda1 is thought to be a space for /dev/md0.

Since likely you have no backup for your Windows stuff anything you do could be a downer.

If you are brave you could use this command:

```
sudo mdadm /dev/md0 --fault --remove /dev/sda1
```

That should do it.

Can you think of what you did to make **mdadm** assemble /dev/sda1 into the array?

---

### Post by andy80 on 2009-04-19
If you are brave you could use this command:

```
sudo mdadm /dev/md0 --fault --remove /dev/sda1
```

I removed it with this one (similar):

```
sudo mdadm --remove /dev/md0 /dev/sda1
```

No data lost :)

Can you think of what you did to make **mdadm** assemble /dev/sda1 into the array?[/QUOTE]

I simply installed mdadm using apt-get and then I copyed mdadm.conf from my Intrepid installation to Jaunty, I added a line to fstab to mount my /home/ and then I did a reboot. That's all.

Now I've modified this line in mdadm.conf so mdadm doesn't add /dev/sda1 to the raid each time I reboot:

```
DEVICE /dev/sdb* /dev/sdc*
```

so it only uses the two disks.

---

### Post by fjgaude on 2009-04-20
Okay, all makes sense. The next time you move to a new OS or motherboard simply don't bring your old mdadm.conf over. So a --scan to assemble like so:

```
sudo mdadm --assemble --scan
```

That will create a new mdadm.conf that is fully valid. If this doesn't work, remove mdadm, re-boot, re-install and then do the above command.

It's great you got everything up without loss of data.

---

### Post by andy80 on 2009-04-20
I'll do it next time. The only problem now is that /dev/sda1 is marked as "linux raid member" as you can see from these information:

```
andy80@andy80-jaunty:~$ sudo vol_id /dev/sda1
[sudo] password for andy80: 
ID_FS_USAGE=raid
ID_FS_TYPE=linux_raid_member
ID_FS_VERSION=0.90.0
ID_FS_UUID=5c7c967b:58c2a816:7ff42eed:7c82eb40
ID_FS_UUID_ENC=5c7c967b:58c2a816:7ff42eed:7c82eb40
ID_FS_LABEL=
ID_FS_LABEL_ENC=
```

Is it possible to change ID_FS_USAGE and ID_FS_TYPE values?

---

### Post by fjgaude on 2009-04-21
Yes, use **gparted** to change the flag for the partition, with the Manage Flags menu.

---

### Post by andy80 on 2009-04-21
> **fjgaude said:**
> Yes, use **gparted** to change the flag for the partition, with the Manage Flags menu.

If I use gparted on that partition it says me it's a boot partition, but not a raid one.

---

### Post by fjgaude on 2009-04-21
Did you select the drive then clicl Partition, and then Manage Flags?

---

### Post by andy80 on 2009-04-21
> **fjgaude said:**
> Did you select the drive then clicl Partition, and then Manage Flags?

Yes I did, look at the screenshot: [http://img218.imageshack.us/img218/618/gparted.jpg](http://img218.imageshack.us/img218/618/gparted.jpg)

---

### Post by fjgaude on 2009-04-21
Interesting... the raid box is unchecked. Was it ever checked? You might re-boot if it was and then unchecked.

I don't use **fdisk** much but do use **cfdisk** which can do a flag set. If you read the **man** pages for fdisk I'm sure it tells how to set the flags.

---

