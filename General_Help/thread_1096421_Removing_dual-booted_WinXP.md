---
title: "Removing dual-booted WinXP"
date: 2009-03-14
forum: General Help
---

### Post by PacSci on 2009-03-14
I installed WinXP Pro and Ubuntu on a computer, and XP has 300GB of the 500GB drive, with Ubuntu having about 200GB. I have never used XP, though (I just put it on in case I needed it), and now I've decided that I could really use that 300GB back. How would I go about destroying the XP partition and appending its space to my 200GB Ubuntu partition to create one 500GB partition for Ubuntu (with the swap partition, of course)

I know that it probably involves using gparted to delete the XP partition, then resizing the Ubuntu partition to fill the drive, but I wanted to make sure that there wasn't anything else that I needed to do first, or find out about any caveats. Could I do this while booted from HD, or would I need to use the LiveCD?

---

### Post by circa82 on 2009-03-14
You can format the XP partition from Ubuntu running off the hard drive, but allocating the free space will require a live CD. Best bet, use a live CD for the whole process. Yes, you'll format the XP partition then allocate the free space to the Ubuntu partition.

Also, that's a ton of space for Ubuntu. Have you thought about dividing up the 300GB for storage or something else?

---

### Post by taurus on 2009-03-14
If you want to resize your harddrive, you have to do it from either Ubuntu LiveCD or GParted LiveCD; can't do it in Ubuntu because you cannot resize a partition while you are using it.

And before you start resizing, let's see the layout of your harddrive--partitions.

```
sudo fdisk -lu
```

---

### Post by masterkoppa on 2009-03-14
In order to work with any partitions involving the same hard disk you must use another disk or use a live cd. Your assertion about how to remove it is correct, just in case I would do a backup of all important files beacuse if the resize fails you might lose the data. Although it has never happened to me or anyone I know, I always take this messure.

You might also want to remove Windows from the boot list this can be done by typing in terminal:
```
gedit /boot/grub/menu.lst
```
Then look for the Windows Xp option and set it to 0 or delete it.

---

### Post by PacSci on 2009-03-14
Okay, sudo fdisk -lu returns:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1030102f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   604156454   302078196    7  HPFS/NTFS    # WinXP drive
/dev/sda2       604156455   613923974     4883760   82  Linux swap / Solaris
/dev/sda3       613923975   976768064   181422045   83  Linux        # Intrepid

# It also said something about my USB external drive, but that's not relevant

```

Of course, I'm using grub to manage the dual-boot. Also of course, the stuff after the "#"'s wasn't in the output.

[QUOTE=circa82]Also, that's a ton of space for Ubuntu. Have you thought about dividing up the 300GB for storage or something else?[/QUOTE]

Storage might be a better idea - I could always put stuff on there if I need to, and maybe back up the important stuff on it in case my main partition fails (will still have external backup, though). Maybe I'll split it 50/50, with "/" having 250GB, and "/storage" or whatever having 250GB as well. So, just to confirm, I'll need to:

[LIST=1]
[*]Reboot into Live CD.
[*]Run gparted on the live CD.
[*]Delete the partition on /dev/sda1 (ntfs).
[*]Expand /dev/sda3 to whatever size.
[*]Create a new partion for miscellaneous storage.
[/LIST]

---

### Post by taurus on 2009-03-14
You have swap partition (/dev/sda2) between windows partition (/dev/sda1) and root partition (/dev/sda3).  

You can delete /dev/sda1 and make that an unallocated space but I don't think you can "give" that space to /dev/sda3, by passing /dev/sda2.  However, you can create a separate /home and/or use that space as a storage.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by mikewhatever on 2009-03-14
You should be able to delete sda1 and format it from Ubuntu while booted from the HDD. I think it's better then the original plan.
If you must resize sda3 and merge sda1 and sda3, use a Live cd. Just make sure to get the swap out of the way, and then fix the UUIDs in fstab and GRUB menu.

---

### Post by circa82 on 2009-03-14
GParted in Ubuntu off your HDD will allow you to format sda1.

Also, you could format both sda1 and sda2 and allocate xGB of free space to your Ubuntu install. 

Alternatively, you could also backup your Ubuntu install, format the entire disk, and start over.

---

### Post by PacSci on 2009-03-14
If I decided to move /home onto its own partition, then how would I migrate the contents of /dev/sda3 /home to /dev/sdathenewone? Would I boot into LiveCD, copy the /dev/sda3 /home to my external USB drive, do the repartitioning, then copy the /home on my external back to the /home which is now at the root of /dev/sdathenewone?

Also: If I deleted my swap and created a new one, would that have any lasting effects? What would I need to change to get the new swap to work?

Based on all of your advice, if I can change my swap, what I'll probably do is:

[LIST]
[*]Leave my 173GB / at the end, but add 27GB back for an even 200.
[*]Destroy my current 4.6GB swap, and create a new 10GB one.
[*]Add a 140GB /home, and move my current /home to it.
[*]Use the remaining 150GB for a /stuff, unless someone can think of a better name.
[/LIST]

---

### Post by circa82 on 2009-03-14
Personally, I'd leave your /home directory where it's at. If you wanted to create a partition for say, music storage. Create the partition and mount it as a sub-directory in /home ... something like /home/music. You can also create a /home/backup partition and backup files there.

As far swap goes; no, there will be no negative results of deleting and creating a new swap partition. 10GB; however, is overkill. What is your system RAM? I would suspect that even 4GB is overkill. For 1GB of RAM or more, use a 1GB swap partition. If at any time you need more swap space, create swap file for 'on the fly' swap space.

---

### Post by PacSci on 2009-03-14
Okay. So, now, I'll probably just extend my / to 249GB, destroy my swap and create a new 2GB one (same as my system RAM), and create /stor (storage) as 249GB.

(Last post of the night, so I won't get feedback until the morning.)

---

### Post by circa82 on 2009-03-15
You'll boot Ubuntu Live CD and enter the desktop.
Then start GParted
- format sda1 and sda2 (keep an eye on device names as they will likely change)
- allocate XGB of free space to your / partition
- create your storage partition
- create your swap partition (just select 'swap' as the filesystem)
- - sda3 (your / partition) should end up as sda3, but verify that before moving on

Close GParted and open a terminal:
```
# [color=blue]sudo mkdir /mnt/ubuntu[/color]
# [color=blue]sudo mount /dev/sda3 /mnt/ubuntu[/color]  <-- / partition -- replace sda3 if necessary
# [color=blue]sudo nano /mnt/ubuntu/etc/fstab[/color]
```
Create a new entry for your storage partition:
```
[color=red]/dev/sda#	/stor 	<filesystem>	defaults	0 2[/color]
```
Change /dev/sda# to the correct partition #. Change <filesystem> to the filesystem you selected in GParted.
Verify that the 'swap' entry is using the correct device name (ie: /dev/sda2) and change it if necessary.

---

### Post by PacSci on 2009-03-16
The reformat operation went off without a hitch. My new fdisk -lu reading is:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1030102f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   509613929   254806933+  83  Linux
/dev/sda2       509613930   515397329     2891700   82  Linux swap / Solaris
/dev/sda3       515397330   976768064   230685367+  83  Linux

```

Thanks for all of your help. (By the way, how can I migrate my Rhythmbox library to the new /stor partition?)

---

