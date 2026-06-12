---
title: "Help with PartitionMagic 8.0"
date: 2005-12-29
forum: General Help
---

### Post by skillzdatkillzholmes on 2005-12-29
I had a Dual Boot system with Windows XP Pro and Ubuntu 5.10. I didn't like Ubuntu too much so I decided I wanted to install Debian instead. Now, I did the Windows Recovery Console fixmbr (Fix Master Boot Record) command and it of course, over-wrote the GRUB Boot thing with a direct Windows XP Pro Boot. Now my problem is that I want to format my Linux Partitions (Swap and EXT3) so I can install Debian but whenever I start Partition Magic 8.0 it says Init Failed: Error 117 Partition's Letter Cannot be Identified. In the help file it says "#117 Partition’s drive letter cannot be identified
Under OS/2, PartitionMagic must be able to find the drive letter for each partition
before modifications can be made. There are various reasons why OS/2 might not
be able to find a drive letter for each partition. For example, a driver on your
system may change the drive letters from their defaults, or your partitions may
not have serial numbers.
You may also see this error when running PartitionMagic under Windows.
The solution is to run PartitionMagic from DOS or from MS-DOS mode (in
Windows 95 or Windows 98). When PartitionMagic runs from DOS or from
MS-DOS mode, it does not need to be able to find the drive letter for each
partition. Thus, if the problem indicated by this error message is the only
problem, PartitionMagic can run successfully."

---

### Post by hw-tph on 2005-12-29
For the problem with Partition Magic, contact their support. From my experience they are very quick and competent, unlike most other helpdesks.

As for your problem, you can just boot the Debian installer and take care of the partitioning from there. No need to involve any other software like Partition Magic.


H&#229;kan

---

### Post by shin on 2005-12-29
I got the same problem. PartitionMagic is not the greatest partition tool. I heard of many issues about it. You might be able to fix the problem with somekind of another partition tool. Yet, it's better to backup your files first.

Anyway, format will fix the problem. Which is not real solution.. Rather a Microsoft-like solution.

---

### Post by rcerreto on 2005-12-29
Partition Magic is a great tool as long as you stick with windows.
I had tons of problem running it after using any kind of linux partitioning tool.
(that's to say on mixed windows/linux system).
I never succeded in recovering if not through: backup, delete partitions, re-create partitions, format, restore.
Awkward.

If anyone did better I'm interested though.

---

