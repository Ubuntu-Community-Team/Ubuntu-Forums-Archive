---
title: "Dynamic disk drives"
date: 2011-10-01
forum: Desktop Environments
---

### Post by srimadhann on 2011-10-01
My computer has been partitioned as 6 disk drives under dynamic type. My computer's operating system is Windows 7 Home Premium. I wish to change one of my disk drive from dynamic type to basic type. Please explain step by step method to proceed the same.

---

### Post by westie457 on 2011-10-01
Hello that is a not very easy task you are asking about. It is possible however there are no guarantees that your files will be saved as they are. 

**Before doing anything else have full back ups of your Windows system and your Ubuntu system and all of your personal files.**

Microsoft say the only way to convert a dynamic disk back to a normal one is to wipe and format the drive then reinstall everything. As in this link. [http://technet.microsoft.com/en-us/library/cc755238.aspx](http://technet.microsoft.com/en-us/library/cc755238.aspx)

However there is a process detailed in this link [http://strangelyperfect.tv/6415/how-to-convert-a-dynamic-disk-to-basic-disk-in-windows-7/](http://strangelyperfect.tv/6415/how-to-convert-a-dynamic-disk-to-basic-disk-in-windows-7/) that is supposed to work on the fly. Cannot vouch for the accuracy of the claim as I have never tried it.

Even if it does work you will in all probability have to lose at least 2 partitions to make it work.

There is no way to do this with Ubuntu as far as I am aware.


Good luck.

---

### Post by oldfred on 2011-10-01
If you have created that many dynamic partitions and used them, conversion may not work depending on how the data is written to the drive. Conversion back works best when you have only created and then want to reverse where the physical and logical have a one to one correspondence. 

Some more possibilities but you must have good backups.

Several users have used this, it has a liveCD download to use:

MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)

---

