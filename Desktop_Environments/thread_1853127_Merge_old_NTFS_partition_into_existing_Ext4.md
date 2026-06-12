---
title: "Merge old NTFS partition into existing Ext4?"
date: 2011-10-01
forum: Desktop Environments
---

### Post by BanderSnoot on 2011-10-01
Hi all,

I want to remove the old NTFS partition from the laptop where I have Ubuntu installed.

Ubuntu is running on an 45GB extended partition with 39 GB formatted Ext4 and three 2.1GB swap partitions.

The primary partition is 115GB of NTFS.

What I'd like to do is "add" the 115GB to the Ext4 partition.

I'd also like it to boot right into Ubuntu and not have the boot manager at startup.

What's the best way to do this?

---

### Post by BanderSnoot on 2011-10-01
After giving it some thought, maybe I should

- Back up Ubuntu system image

- Do a clean-wipe install onto the disk and setup the partitions the way I want.  No boot manager.

- Restore from the backup image(?)

I don't know what I'm talking about, what to watch out for, or if will get the result I want...

Your enlightenment greatly appreciated.

---

### Post by drs305 on 2011-10-01
Because your NTFS partition is a primary partition and Ubuntu is an extended partition, you will have to accomplish a lot of steps to join the two without reformatting. It can be done, however it won't be simple.

Normally I'd recommend creating an image and reformatting, but this presents it's own issues. You would have to boot the LiveCD and edit the Grub 2 menu (removing and/or changing the UUIDs and partition designations) and change the fstab settings before it would boot.

An alternative would be to shrink and reformat the NTFS partition to ext 3/4 and use it as a data partition. Then expand the extended partition to the left and enlarge the Ubuntu partition. You can also remove two of the three swap partitions - just keep the one listed in fstab. If more than one is listed, choose one and delete or comment out the other two.

The advantage of shrinking/moving things is that your Ubuntu partition will retain the same UUID and you shouldn't need to edit fstab or Grub. It will take some time to expand the / partition but it would take time to do it the other way as well. 

I wrote a guide about how to expand the Ubuntu partition if you want to keep the primary partition and not reinstall:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

Whatever you decide to do, make backups of your important files.

With only one OS, you shouldn't see the Grub menu on boot. You may need to run 'sudo update-grub' after everything is moved.

---

### Post by BanderSnoot on 2011-10-01
Thanks for the helpful response.

I decided it would be better to copy off stuff to keep and do a wipe and reload.

It's not that bad really, and since this is the third time, I'm getting better at it!  And it's already done!  8^)

In all seriousness, I am very impressed with Ubuntu.  Stuff just works (unlike my last experience with another distribution.)  When it was able to 1) discover a wireless printer, 2) let me see shared files on my Windows PC, 3) play all my media files without a hiccup and 4) run without me have to do any driver-fiddling and support all my hardware... well, it's worth a little bit of effort effort.

---

### Post by drs305 on 2011-10-01
Glad you had success. You didn't mention the boot issue so I'll assume Grub is behaving the way you wish.

If you don't have any further issues, would you please mark the thread SOLVED via the 'Thread Tools' link at the top right of the first post?

Happy Ubuntu-ing !

---

