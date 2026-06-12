---
title: "fresh install boot problem"
date: 2006-08-25
forum: Desktop Environments
---

### Post by buck chocolate on 2006-08-25
So I've installed 6.06 a couple of times now and each time it installs and boots up fine for the first couple of times. Then it hangs on boot at this point...

[IMG]http://i12.photobucket.com/albums/a236/linkdup/CIMG0534.jpg[/IMG]

This happened this time after maybe the 4th boot. I installed the OS, then the next boot I installed easy ubuntu, then I think the next boot it booted fine but I didn't do anything to the system except maybe change the root password and make it loginable. Then the next boot is when it started to hang I think.

This is my harddrive situation and I'm thinking it might have something to do with this. hda1 is XP32, hda2 is XP64, hda3 is ubuntu, hda4 is swap and hda5 is my home directory.

[IMG]http://i12.photobucket.com/albums/a236/linkdup/HDsituation.png[/IMG]

XP64 partitioned the free space on the drive (at the time of install hda1 was a 50gb partition and the rest of the drive was free space) so XP64 automatically created an extended partition of the full free space size and a partition for the install inside of that. This is where I think things are getting screwy for ubuntu install. I have no idea why it would do what it's doing but this is all I can think of now.

Btw it's an ext3 partition. Do you guys recommend XFS over ext3?

Take care guys

---

### Post by zxee on 2006-08-25
After a hang or non-booting situation I would check /var/log/boot for messages. Nothing jumps out about your set up/partitions that seem like a potential problem. As far as file systems I like reiserfs. It's fast and pretty dependable. I don't think grub and xfs are a good match-but someone with more experiance in xfs might correct me.

---

### Post by buck chocolate on 2006-08-25
> After a hang or non-booting situation I would check /var/log/boot for messages
How if it's not booting? :)

---

### Post by varchar32 on 2006-08-27
i have the exact same problem with my new installed ubuntu. It was a clean install and added only a few things. now it loads up to mounting root file system then hangs. Windows partion works fine. It is like randomly doing this most of the time yet sometimes loading normal. I have 2 hard disk and each hd have extended partitions for ntfs, fat32 and ext3. Linux partition very similar to yours. root, swap and /home. This was happening with Mandrake randomly also.](*,)

---

### Post by buck chocolate on 2006-08-27
Yeah it's wierd. I've been having this problem longer than I've had my raid setup so I'm pretty sure that doesn't have anything to do with this particular issue.

I still think it might have something to do with the extended partition. I've triple booted before without issues but usually I manually setup ALL partitions with my first OS install witch is always XP32. Then I'll install XP64 then linux into the existing partitions without having any extended partitions.

I was mainly hoping that someone here had experience with this situation so I didn't have to reinstall 2 OS's.

---

