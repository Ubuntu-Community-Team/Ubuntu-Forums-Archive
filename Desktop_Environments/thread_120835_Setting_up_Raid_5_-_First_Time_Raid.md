---
title: "Setting up Raid 5 - First Time Raid"
date: 2006-01-23
forum: Desktop Environments
---

### Post by bond00 on 2006-01-23
I'm setting up Raid 5 for the first time in Linux and am unsure how to do it.  I have tried a couple different ways, but am wondering if anyone out there can provide a quick tutorial or point me in the right direction.

Currently I have four 300 GB drives partitioned with ext3 and also a swap drive. I then go to the console and type something like:

mdadm --create /dev/md0 --level=5 --raid-drives=4 (some other options) /dev/hd[egik]

The computer then creates the array and this is where I think I am messing up.  Do I create another ext3 filesystem for the array or do I not have to because it's already done?  If I do need to, what command/program is best?  

Also what is the correct command to mount the drive automatically through fstab? Are there any special commands.  

Sorry for all the questions.  I've just tried this several times and can't seem to get it to work.  Thanks for the  help.

---

### Post by silex on 2006-02-22
I've had limited experience with RAID under linux (roommate is putting together a  4x250Gb RAID 5 array as I type this), but I think the drives need to be formatted not as ext3 but as Linux RAID (the code escapes me now).  Then you use mdadm to build the raid, then put ext3 on that.  I think.

---

### Post by EmmEff on 2006-02-22
Yes, after /dev/md0 is created, you need to create the filesystem on it using mke2fs (or whatever mk...fs that you desire; I run ReiserFS on my software RAID5 array).

Add /dev/md0 to your fstab the same way you'd add a physical disk.

You might want to look into LVM as well as it makes the large RAID partition more manageable.  That's what I use in my config with 5 160GB drives.

---

