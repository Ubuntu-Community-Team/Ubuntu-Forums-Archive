---
title: "Vista won't let me make a new partition"
date: 2009-01-07
forum: General Help
---

### Post by SirSigma on 2009-01-07
Okay, I have both Ubuntu and Vista dual-booting on my laptop. And I've wanted to make a new partition to install XP as well. To make a new partition, I tried at first to use Vista's built-in partition manager (you know, the one on Start > Computer > Right-click > Manage?). Unfortunately, I was completely unable to shrink off anything from the Vista partition (NTFS), getting "0" as the amount available for shrinking. I tried simple things to get it working, like turning off paging and clearing out space. No luck.

Naturally, I looked around on the internet for people having the same problem. A website recommended I get a free trial of PerfectDisk 2008 and defragment with it. I used the SMARTplacement defrag option, but I still got 0 when I brought up the partition manager. Then I tried Consolidate Free Space defrag, and still nothing. After looking around the program for a bit, I noticed the option to defragment system files that were normally locked up by Windows, and it made me restart to do it.

I restarted and waited for time to pass. It must have been 20 to 30 minutes later that I checked again and had success! Instead of 0, the partition manager was now letting me shrink off a maximum of 96690.

Or so it seemed.

When I entered 15360 to shrink off for a partition, I waited a little less than a minute, and then I was given the error message in a pop-up box reading "Logical Disk Manager" as the title and the text in the box reading "Access is denied."

I repeatedly tried again hoping for results, but I kept getting the same message.

After repeatedly failing on Vista, I went into Ubuntu and used Gparted, but unlike Vista's partition manager, all the shrink options were grayed out. And yes, I did try unmounting the drive, but I still got nothing. After this, I tried going back to Vista hoping for better results.

I went digging around on the web and found others with similar problems. One guy said he used PerfectDisk and defragmented for Consolidate Free Space. I picked that option and left my computer to defrag as I went out.

I came back about 2 hours later and found the defrag finished. I tried again and got the same message. I looked around on the web again and noticed a user saying he got it to work in safe mode. So I gave safe mode a shot, and I still managed to get the same result.

I would try Gparted on a Live CD, but I don't have any spare media to burn it to or boot it from. Besides, I don't have the actual Vista disk to recover with (I only have factory-restoration disks made just for my laptop).

Now I went looking around again, and not only was I finding less information, but it seemed that I was stumbling into forums that had the EXACT same posts as one another.

I don't have anyone else to go to help for on this. Does anybody have any suggestions on how to partition this thing?

---

### Post by halovivek on 2009-01-07
how many currently partitions you have in your system.
if you have more than 3 primary and 2 or 3 logical partition vista will not allow to do so. 
can you post more details about you hard disk details.

---

### Post by SirSigma on 2009-01-07
How would I know the difference whether it's a logical or primary partition?

Also, what kind of details should I post about it?

---

### Post by proevofanatik on 2009-01-07
can i ask why you want xp and vista installed? seems like a waste of time to me.
the way ive got mine set up is im dusal booting xp and ubuntu 8.10. i only use xp for playing games. everything else is done on ubuntu. thats all you will ever need. vista is a total waste of space imo

---

### Post by SirSigma on 2009-01-07
> **proevofanatik said:**
> can i ask why you want xp and vista installed? seems like a waste of time to me.
the way ive got mine set up is im dusal booting xp and ubuntu 8.10. i only use xp for playing games. everything else is done on ubuntu. thats all you will ever need. vista is a total waste of space imo

I purchased the copy of XP already. Don't try and convince me otherwise.

Besides, if it's all good, I might erase Vista and keep XP and Ubuntu.

---

### Post by torgrot on 2009-01-07
How many disk drives do you have?  It sounds as if Logical Volume Management is enabled.  That would allow you to mount a disk as a folder on another disk drive.  It would give you the appearance of a single disk drive.  I beleive it can be turned on with only one disk though.  I would search Microsoft for Logical Volume.

torgrot

---

### Post by torgrot on 2009-01-07
How many disk drives do you have?  It sounds as if Logical Volume Management is enabled.  That would allow you to mount a disk as a folder on another disk drive.  It would give you the appearance of a single disk drive.  I beleive it can be turned on with only one disk though.  I would search Microsoft for Logical Volume.

torgrot

---

### Post by SirSigma on 2009-01-07
I'm not quite sure what you're asking, so I'll post a screenshot of the partitioner showing my current partitions. 

[img]http://img90.imageshack.us/img90/5016/partitionerscreenshotgc1.jpg[/img]

---

### Post by caljohnsmith on 2009-01-07
It looks like all four of your partitions are primary partitions, so you wouldn't be able to create another partition unless you turn one of your primary partitions into an extended partition. Can you post a screenshot of gparted too? It sure seems strange it won't let you shrink the partitions. Also please post:
```
sudo fdisk -lu
sudo sfdisk -d /dev/sda

```

---

### Post by SirSigma on 2009-01-07
Here's sudo fdisk -lu

```
sigma@Sigma-Laptop:~$ sudo fdisk -lu
[sudo] password for sigma: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x78cf670d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048   437184511   217055232    7  HPFS/NTFS
/dev/sda3       437192910   488392064    25599577+   5  Extended
/dev/sda5       437192973   486175094    24491061   83  Linux
/dev/sda6       486175158   488392064     1108453+  82  Linux swap / Solaris
sigma@Sigma-Laptop:~$ 
```

Here's sudo sfdisk -d /dev/sda

```
sigma@Sigma-Laptop:~$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=  3072000, Id=27
/dev/sda2 : start=  3074048, size=434110464, Id= 7, bootable
/dev/sda3 : start=437192910, size= 51199155, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=437192973, size= 48982122, Id=83
/dev/sda6 : start=486175158, size=  2216907, Id=82
```

And here's a screenshot of Gparted

[img]http://img152.imageshack.us/img152/3271/gpartedmq0.png[/img]

Also, I forgot to mention that mysterious unallocated space (1MB and 4.10MB) that only seems to show up on Gparted but not on Vista's partition manager.

---

### Post by caljohnsmith on 2009-01-07
OK, I see you do have an extended partition, so that's good news. How about trying these steps in Vista to see if Vista will then let you shrink its partition:
[LIST]
[*]**Disable the pagefile:**
Right-click "Computer" > Advanced System Settings > Advanced > Performance Settings > Advanced > Change Virtual Memory. Click on "No pagefiling" and then "Set." After reboot, delete C: pagefile.sys. To do that you might need to check "show hiddenfiles" and uncheck "hide system files" by doubling-clicking Computer > Organize > "Folder Options" > View.

[*]**Disable hibernation**:
Open a terminal as administrator: press the Windows key and "r" at the same time to get the run program/command dialog, then type "cmd", then press Ctrl-Shift-Enter, and finally type "powercfg -h off".

[*]**Disable "snapshots":**
Right-click Computer > Advanced System Settings > System Protection and uncheck all the drives.

[*]**Try shrinking the Vista partition more than once: **
After doing the above steps, if you can't shrink the Vista partition as much as you want, shrink it as much as Vista will let you, and then repeat the process again.
[/LIST]
How about giving that a shot and let me know how it goes.

---

### Post by SirSigma on 2009-01-07
I tried all those things and I've got nothing.

When I tried resizing by the maximum, the only difference was I waited almost 5 minutes to get the same access denied message.

---

### Post by caljohnsmith on 2009-01-07
I'm not sure how Vista's UAC or "User Access Control" works, but it sounds like you need to somehow give yourself administrative privileges when you are in Vista so you can do the repartitioning. Can you log in as administrator or somehow switch to administrator mode? I really don't know how Vista handles administrative access, so I'm sorry I can't help with that, but it sounds like that is the issue.

---

### Post by SirSigma on 2009-01-07
> **caljohnsmith said:**
> I'm not sure how Vista's UAC or "User Access Control" works, but it sounds like you need to somehow give yourself administrative privileges when you are in Vista so you can do the repartitioning. Can you log in as administrator or somehow switch to administrator mode? I really don't know how Vista handles administrative access, so I'm sorry I can't help with that, but it sounds like that is the issue.

I am using an administrator account (but not THE administrator account that Vista hides). And I also have UAC turned off.

---

### Post by caljohnsmith on 2009-01-07
In that gparted screen shot you posted it shows the sda2 Vista partition as locked, which means it was mounted when you took the screen shot; how about trying gparted again, but first right-click the Vista sda2 partition and select "unmount". Did you all ready try that? Is it successful unmounting the partition and removing the "keys" graphic symbol next to the partition? If so, can you shrink the Vista partition after that?

---

### Post by SirSigma on 2009-01-07
I think I already mentioned somewhere that I already tried unmounting on Gparted. That made no difference, but the difference between the Vista partition manager and Gparted is that all the options to resize are grayed-out.

---

