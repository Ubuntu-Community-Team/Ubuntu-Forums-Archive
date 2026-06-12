---
title: "cannot mount harddisk"
date: 2009-04-18
forum: General Help
---

### Post by SkippoGuangiacomo on 2009-04-18
Hi, I recently 'transformed' an internal harddisk (was initially working in windows as an NTFS drive) in a external harddisk (I bought a box, put the harddisk inside and make some connections, and now it looks pretty much like a removable harddisk). The harddisk in this new configuration was working perfectly properly in kubuntu. Recently I had to use the harddisk in Windows again (the harddisk contains some data that I recently needed to analyze again, and in my university linux is not supported, therefore windows is the only OS). In Windows I had to 'reactivate' the drive before being able to use it again. But now, that I would like to reopen the drive at home, I cannot access the drive in anymore. I'm going to post the result of 'sudo fdisk -l':
--- begin report
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ac6ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       57142       58978    14755702+  83  Linux
/dev/sda2           58979       60801    14643247+  82  Linux swap / Solaris
/dev/sda3               1       57141   458985051   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002e534

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15801   126921501   83  Linux
/dev/sdb2           15802       30801   120487500   83  Linux
/dev/sdb3           30802       45801   120487500   83  Linux
/dev/sdb4           45802       60801   120487500   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b278456

   Device Boot      Start         End      Blocks   Id  System
 ----- end report
Now, sda and sdb are the internal hdd installed in the desktop, whereas sdc (I suppose) is the external hdd (I say this because there is nothing else attached to the machine). First thing I've noticed is that the fdisk does not report anything under the line 
'   Device Boot      Start         End      Blocks   Id  System' 
for the sdc device, whereas it did so for the other two hdd. Isn't that strange? Can anybody tell me if the HDD is not working properly anymore?
If I try to mount manually, through:
'sudo mount -t ntfs /dev/sdc /media/sdc1 -o umask=000'
I get:
'NTFS signature is missing.
Failed to mount '/dev/sdc': Invalid argument
The device '/dev/sdc' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?'

I also tried tried to fix it through 'ntfsprogs' using: 
'sudo ntfsfix /dev/sdc'
and i got:
'Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.'
When I run 'chkdsk' I got: 
'sudo: chkdsk: command not found'

I tried to install it but got nothing.. 
I'm not really sure what to do after this.. Any help would be greatly appreciate!

---

### Post by danwood76 on 2009-04-18
Theres a piece of software in the repos that might be able to help you.
Its called testdisk, if you run this from the terminal:
```

sudo testdisk /dev/sdc

```
you will be able to search for lost partitions and recover them, its odd that the partition table is gone though, wither way this sw should recover it.

It normally moans that the default window isnt large enough, just drag the bottom of the terminal window down one line and it should work fine!

---

### Post by SkippoGuangiacomo on 2009-04-18
Thanks for the suggestions. I installed and checked the partitions. Testdisk finds the partition and it's able to check the content of the harddisk. I do not really know what I should do to recover it though. Should I remake the partition and write it to the disk? I'm not sure about this because I thought that if I write a partition the content will be erased, or is it only referring to the partition table? 
Thank you very much for you help!

---

### Post by danwood76 on 2009-04-18
You need to re write the partition table.
Re writing this table wont effect the data on the disk just the table that gives info about the partitions.

Testdisk should offer to do this for you (I think).

---

### Post by SkippoGuangiacomo on 2009-04-18
Yes, it does. It's only that rewriting was something I used to do years ago with debian, when I wasn't using a desktop... But I thought then I would have formatted the disk. However, if you say that is not a problem I'll do it and hope for the best. Thank you very much!

---

### Post by danwood76 on 2009-04-18
It will just re qrite the table according to what partitions it has found.
So it will simply make the partitions active again.

Good luck!

---

### Post by SkippoGuangiacomo on 2009-04-18
True! I did it, rebooted and it works again! Thank you for the help! Very appreciated!

---

### Post by danwood76 on 2009-04-18
:) No problem.

---

