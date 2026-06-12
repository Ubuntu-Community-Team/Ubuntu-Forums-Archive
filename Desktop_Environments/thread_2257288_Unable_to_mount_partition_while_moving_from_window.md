---
title: "Unable to mount partition while moving from windows 7"
date: 2014-12-18
forum: Desktop Environments
---

### Post by classify on 2014-12-18
I moved from win7 to ubuntu with 2 drives:
1. SSD - 128gb 
2. HDD - 500gb - partitioned to 2 parts (lets call them 'a' and 'b')

After installing Ubuntu on the SSD I logged in and found out the 'b' were automatically mounted but 'a' wasn't.
With fdisk I can see:

**Device Boot      Start         End      Blocks   Id  System****/dev/sdb1              63   976771119   488385528+  42  SFS**
**Partition 1 does not start on physical sector boundary.**
I read a little on the forums and saw that there were no way to mount those SFS partitions but that was about a year ago, is there something I can do now ?

---

### Post by TheFu on 2014-12-18
Google found this: [http://askubuntu.com/questions/412248/mounting-an-sfs-partition-drive](http://askubuntu.com/questions/412248/mounting-an-sfs-partition-drive)  from last January. Looks easy.

Depending on the version of Ubuntu you are running, using **parted**, not fdisk, might be smarter. Old versions of fdisk don't support GPT and not using a GPT-ready tool might be bad if changes are made to the drive.

---

### Post by oldfred on 2014-12-18
SFS is Windows dynamic partitioning. It is proprietary to Windows and somewhat like the LVM or logical volume management type systems.

Whatever you do be sure to have good backups.

You can unusually use third party Windows tools to remove the dynamic partitions as long as you have less than 4 so you can map back to 4 primary partitions. Not sure if more then it can use logical or not.

       Microsofts official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

    Never used these, I think one only runs in Windows, and the other has a live CD version.
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

One user posted he was able to undo dynamic partitions with testdisk? 
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

---

