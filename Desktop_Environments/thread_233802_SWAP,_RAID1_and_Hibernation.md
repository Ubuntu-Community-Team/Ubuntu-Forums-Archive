---
title: "SWAP, RAID1 and Hibernation"
date: 2006-08-10
forum: Desktop Environments
---

### Post by appye on 2006-08-10
Okay, I am learning a bit here (noob).  I have successfully set up a system booting into a software RAID1 setup.  I put the SWAP partitions on each drive on the outer tracks to help performance wise.  The swap partitions were not setup under software RAID.  I wanted to do the thing where I set them each to the same priority so they would be effectively stiped, further helping performance.  This seemed to be the logical choice because I striping them through raid seemed like it would create additional overhead, is this correct thinking?  How do I change this priority?

Also, I noticed that the computer does not want to hibernate.  The first time I tried it, it seemed like it wrote the RAM to disk (I could see HD activity for about 15-30 seconds) and powered down nicely. When I powered on, it did not hang at "Mounting root file system" while it loaded the RAM from disk (like my laptop does).  It did seem to hang there for several seconds, but then proceeded to boot up normally.  When I tried a second time to hibernate, it just kicks me back to the window I would normally see upon a proper resume, where the Workstation is locked, and it wants my password...

What am I doing wrong?  I know hibernation in Linux has something to do with writing RAM to the SWAP partition, but it is not all that clear to me.  What would be the best way to set up SWAP on a software RAID1 system?  Also, the RESUME= line in  "/etc/mkinitramfs/initramfs.conf" only has /dev/hda1 in there.  Should it not also have /dev/hdc1 (my other swap partition) listed as well?

Well, this newbie is kind of befuddled.:confused:

---

### Post by appye on 2006-08-10
UPDATE!

I have managed to syncronize the two swap partitions by editing /etc/fstab and giving them each a priority of 10.  Before they were -1 and -2 (as reported by "cat /proc/swaps") ...  The negative number did not work the first time, so I just set them both to 10 and that seemed to take.  Does it matter what priority number I assign to them?

---

