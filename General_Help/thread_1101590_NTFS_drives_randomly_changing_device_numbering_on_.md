---
title: "NTFS drives randomly changing device numbering on boot?"
date: 2009-03-20
forum: General Help
---

### Post by sodade on 2009-03-20
I have been trying to figure out a problem I have with one of my NTFS volumes not auto mounting and when I go to places and select the name it fails to mount. 

In struggling with this issue, I think I have found the root cause: sometimes when I boot, the drive shows up in gparted and fdisk as /dev/sda1 and sometimes as /dev/sdd1. The drive is one of four hard drives in this machine and is plugged into a SATA channel that requires a RAID driver in XP, even though I am not using RAID. 

Assuming that there is not an easy answer for this (and because I'd like to have a in-depth understanding of the end to end process), could someone please help me find the following information:

1. What is the "process" (or whatever it is called) that reads in the drives and assigns them to sda1, sdb1, etc ? 
2. Where do I find detailed info about this "process" 
3. I have a file called: fstab.pre-ntfs-config in my /etc, where can I find an explanation for how this works in conjunction with fstab?
4. As I indicated, the name of the volume is in my "places" menu - how did it get there and how can I edit its properties?


Much thanks in advance...

---

### Post by cariboo on 2009-03-20
You could try using uuid to mount the drive instead of the device label eg:

```
# Second internal drive mount as /home/stoage
UUID=7451e251-cb09-4cda-b433-a2768d81affe /home/storage	 ext4     relatime        0       2
```

I don't have Windows installed on a partition, I use Virtualbox, on this computer, so I can't show you a better example. to find the uuid of your hard drives open an Applications-->Accessories-->Terminal and type:

```
blkid
```

you should get a result that looks something like this:

```
blkid
/dev/sda1: UUID="7451e251-cb09-4cda-b433-a2768d81affe" TYPE="ext4" 
/dev/sdb1: UUID="b3e831ac-7f40-48e4-b65e-7f4700759208" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="e44c6e62-f018-4e73-926f-b8f51860f2c9" TYPE="ext4" 
/dev/sdb3: TYPE="swap" UUID="4626b456-e693-4be8-ab09-0f19f533d282" 
/dev/sdb4: UUID="16ba3cd0-406e-46ee-ba5e-d147f4bcb073" TYPE="ext4"
```

Look for your ntfs drives.

Jim

---

### Post by sodade on 2009-03-23
Worked perfectly - thanks cariboo907. :)

---

