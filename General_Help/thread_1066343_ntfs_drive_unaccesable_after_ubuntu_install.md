---
title: "ntfs drive unaccesable after ubuntu install"
date: 2009-02-10
forum: General Help
---

### Post by Rhinop on 2009-02-10
I hate to ask this, but I'm not looking for someone to fix my problems, just point me in the right direction.

A few days ago I tried to install Ubuntu 8.10 server edition, however the cd I burned was corrupt and gave errors on trying to install. I did manage to get Ubuntu 8.04 server edition installed later. This is all in addition to the 8.04 desktop edition partition I have, and 2 ntfs partitions (a main and a data partition). Now I can't access the ntfs data partition. In XP it still shows up but says the drive isn't formatted. In fdisk and in the rescue mode on the live CD it shows up as formatted in ntfs, but doesn't show up at all in "system:/media/" (in KDE, which I am new to) even though the main ntfs partition does. In the rescue mode on the live cd when I try to access the options for the partition is gives an error.

I doubt I am the only one who has had the problem, but I'm not even sure what to google. Here is the fdisk output if you need it.

```
sudo fdisk -l -u

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbc90bc90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS
/dev/sda2       102398310   488392064   192996877+   f  W95 Ext'd (LBA)
/dev/sda5       102398373   307194929   102398278+   7  HPFS/NTFS
/dev/sda6       307194993   346265009    19535008+  83  Linux
/dev/sda7       346265073   352128734     2931831   82  Linux swap / Solaris
/dev/sda8       449322048   488392064    19535008+  83  Linux

```

---

### Post by lavinog on 2009-02-10
/etc/fstab is the file that determines what file systems are mounted at boot and where.
Usually when a user is having filesystem issues, it is usually the first place you want to look.

As for XP: have you looked at it with disk management in XP?

---

### Post by Rhinop on 2009-02-10
Ok. disk management says it is healthy and empty (and not formatted). I tried mounting it in ubunutu (which still says it is formatted) and I get this 
```
sudo mount /dev/sda5 /win -t ntfs
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

I assume this means the partition is dead? or is there something else I could try?

---

### Post by lavinog on 2009-02-11
> **Rhinop said:**
> Ok. disk management says it is healthy and empty (and not formatted). I tried mounting it in ubunutu (which still says it is formatted) and I get this 
```
sudo mount /dev/sda5 /win -t ntfs
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

I assume this means the partition is dead? or is there something else I could try?

What was on that partition? was it windows? if so did you shut it down correctly?

Chances are that the partition information got corrupted some how. It is likely your data is still intact though.

---

### Post by Rhinop on 2009-02-11
It was just data and a couple of programs. Not windows.

---

### Post by caljohnsmith on 2009-02-11
How about posting the output of:
```
sudo xxd -s128 -l2 -p /dev/sda5
```
Also, I would recommend using "testdisk" to see if the sda5 partition boot sector needs repairing. To do that, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the sda5 NTFS partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, try mounting it again and please post the results. We can work from there.

---

### Post by Rhinop on 2009-03-02
Thanks! I used testdisk and the partition is now mountable and accessible. Sorry for not responding sooner. One minor issue that I doubt anyone here can solve (seems like an application problem, but I guess someone here might have run into it before). I don't seem to be able to access some saved game files (Fallout 3). But otherwise I seem to be able to access all other files. Anyway, thanks again.

---

### Post by benmarvin on 2009-03-03
Thank you so much caljohnsmith. That test disk was exactly what I needed to fix the MBR on one of my data drives. That's what I get for screwing around in GRUB when I didn't know what I was doing.

---

