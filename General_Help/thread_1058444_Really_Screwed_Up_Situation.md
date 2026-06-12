---
title: "Really Screwed Up Situation"
date: 2009-02-02
forum: General Help
---

### Post by mike_302 on 2009-02-02
Okay so I'll explain the whole thing.

I wanted to get rid of my linux partition, so I used Norton Parition magic in windows to format the 3 linux partitions. Then on reboot, the Grub says ERROR 17.

I google this and find that I basically need to redo the MBR . Someone else did hte EXACT same thing as myself and they fixed the problem simply by putting in the windows disk, doing the recovery console and "fixmbr"   so I try this. Forgot my Administrator password! And I've tried everything I can think of. So my next thing is to try to get linux to do the mbr fix. Well, that didn't seem to work out. So I try to reset my admin password for windows, but I can't seem to do that because the Linux LiveCD doesn't recognize my XP Partition (it sees that there is a partition there: sure. But it doesn't see it for me to mount I guess)

So I need to get this MBR fixed. I can't format the XP partition. not for somethign this small. IT's just complicated an I have little linux knowledge... I just have a Ubuntu LiveCD, an XP disk, and a NEED to get this done.

SOMEONE PLEASE HELP! :(

---

### Post by sedawk on 2009-02-02
Is the dialog for "fixmbr" only asking for the password or also for
the name of the Administrator - on none of my XP machines the
"primary" user is called "Administrator", but something else!

You should not have problems mounting the XP partition. Use
"sudo fdisk -l" to list the disk(s) and find the active boot partition
for xp. It is something like /dev/sda1.
Mount it using something like "sudo /dev/sda1 /media/manually".

If you still have a way of downloading and burning an iso-File you
might try a Live-Distro like Knoppix.

Be patient, your problem is not hard to fix, e.g. post the output
of "sudo fdisk -l" and "mount" here.

---

### Post by mike_302 on 2009-02-02
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8924    71681998+   7  HPFS/NTFS




ubuntu@ubuntu:~$ sudo mkdir /media/hda1
ubuntu@ubuntu:~$ sudo mount -t NTFS /dev/hda1 /media/hda1
mount: unknown filesystem type 'NTFS'

---

### Post by mike_302 on 2009-02-02
when in Recovery, it asks me to select which drive I want to boot, gives me only one option... the one with windows on it, and then I slect it, then it asks for the Admin password for it.

---

### Post by mike_302 on 2009-02-02
Okay, long story short, I was following another guys thread that had a similar problem and got to the point where Grub loading doesn't even appear: Just "Invalid Partition Table" (something about forcing a MBR fix from terminal actually messes the Partition table) . So now my partition table is messed, but on the bright side: I loaded hte XP disk again and went into recovery console, NO MORE PASSWORD PROMPT! YAY!

but if I do fixmbr, it says that with invalid partition table, I could lose my data... make it unreadable.

How do I fix the partition table is my next question?

---

### Post by sedawk on 2009-02-04
There is a tool "testdisk" even available for Linux.
Some people here have reported it worked (recovering the
partition table from backups that are stored on the disk too).

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

---

