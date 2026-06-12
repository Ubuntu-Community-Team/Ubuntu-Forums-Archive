---
title: "Permissions with a FAT partition"
date: 2009-05-04
forum: General Help
---

### Post by Tootler on 2009-05-04
I have a dual boot Ubuntu/WinXP system. I keep my data on a separate partion formatted as FAT32 to make it accessible from both Windows and Ubuntu. 

This works fine most of the time but I have come across a couple of problems:

One relates to Audacity which is described in [this thread on the Audacity forum]("http://audacityteam.org/forum/viewtopic.php?f=18&t=2724") and is likely an Audacity issue.

The other problem, a relatively minor one, but irritating is that when I try to send a file to the Deleted Items folder, I get a message which says
"Cannot move file to the Deleted Items folder, do you want to delete permanently?". Like I say this is not a major issue, but annoying as I do not like to delete files completely immediately as I sometimes find I need to recover them.

All help resolving this appreciated

Geoff

---

### Post by DGortze380 on 2009-05-04
> **Tootler said:**
> I have a dual boot Ubuntu/WinXP system. I keep my data on a separate partion formatted as FAT32 to make it accessible from both Windows and Ubuntu. 

This works fine most of the time but I have come across a couple of problems:

One relates to Audacity which is described in [this thread on the Audacity forum]("http://audacityteam.org/forum/viewtopic.php?f=18&t=2724") and is likely an Audacity issue.

The other problem, a relatively minor one, but irritating is that when I try to send a file to the Deleted Items folder, I get a message which says
"Cannot move file to the Deleted Items folder, do you want to delete permanently?". Like I say this is not a major issue, but annoying as I do not like to delete files completely immediately as I sometimes find I need to recover them.

All help resolving this appreciated

Geoff

Not quite what you asked, but might I suggest ... NTFS Support has become quite good. I would recommend it over FAT.

---

### Post by Tootler on 2009-05-06
> **DGortze380 said:**
> Not quite what you asked, but might I suggest ... NTFS Support has become quite good. I would recommend it over FAT.

I'm not sure that will resolve the underlying problem which, I suspect has to do with ownership of the partition. I checked the permissions tab on file properties in the FAT partition and found that in both folders and files the owner and the group was given as a root with read and write access. In the Ubuntu partition it is given as "geoff" (my ubuntu userid) and I can change the partitions.

I tried changing ownership from the terminal using "chown" but that did not work. I cannot remember the exact message now but it meant that it was not possible.

WinXP is on a NTFS partition and that is mounted on startup as NTFS-3g so I checked the permissions there and like the FAT partition the owner and group was given as root with read/write access, so I am not sure that reformatting the FAT partition as NTFS will solve the problem.

I suspect it may be necessary to mount the partitions with "geoff" as the owner on startup, but I am not sure how to do that. I have tried modifying fstab in various ways but, so far none have worked.

I have only been using Linux for a few weeks so now I am stumped.

Geoff

---

### Post by Legace on 2009-05-06
Try this: [http://technet.microsoft.com/en-us/library/bb456984.aspx](http://technet.microsoft.com/en-us/library/bb456984.aspx)
Look at "Converting to NTFS Using Convert.exe".

---

### Post by LowSky on 2009-05-06
use this command in a terminal

```
gksu gedit /etc/fstab
```

and please post the results, maybe we can change the permissions.

---

### Post by Tootler on 2009-05-07
Here is the contents of /etc/fstab

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda3
UUID=ed332988-aaf5-4149-86d8-4e7c8ac7cf4b     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda2
UUID=DAD0B335D0B316AB       /media/drv0       ntfs-3g         defaults      0   0

# /dev/sda4
UUID=adfbcc7a-bff3-4142-891a-1b58e0286a67      none            swap        sw          0   0

# /dev/sda1
UUID=1C80-61A1  /media/DATA      vfat    user,fmask=0111,dmask=0000   0   0     
```

sda2 is my windows partition (formatted as NTFS) and sda1 the FAT partition with my data on it. I know it is not the usual way round, but has to do with the way the computer was set up when I bought it.

---

