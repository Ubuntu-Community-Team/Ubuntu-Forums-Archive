---
title: "Help with PartitionMagic 8.0"
date: 2005-12-29
forum: Desktop Environments
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

### Post by art on 2005-12-29
I think if you start installation of debian you will have an option to format whichever partition you want, so you don't need formatting them beforehand.

---

### Post by az on 2005-12-29
Partition magic does not seem to be able to handle linux filesystesma and partitions.  I think that the debian installer (and the ubuntu installer) uses the tools that are what is most widely used to resize and partition disks anyway - parted and the ntfs tools.

---

### Post by diffuser78 on 2005-12-29
You didnt like Ubuntu ....but why ? Its the best distro around and makes your much easier compared to other distros around. Well, thats your personal preference but give some time to yourself to like Ubuntu. Take it easy though.

Well, good luck for solving your problem.

---

