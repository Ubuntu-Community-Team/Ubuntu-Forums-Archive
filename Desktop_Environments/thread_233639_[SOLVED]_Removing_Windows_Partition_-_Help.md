---
title: "[SOLVED] Removing Windows Partition - Help"
date: 2006-08-10
forum: Desktop Environments
---

### Post by wieman01 on 2006-08-10
Hey Guys, 

I am planning to remove my Windows partition but I have no idea how to do that without impacting my Ubuntu installation. My current configuration is this (see the attachment also):

> /dev/hda1 : Windows
/dev/hda2 : Extended
/dev/hda5 : /home
/dev/hda6 : /[root]
/dev/hda7 : /[swap]

Any idea how I can remove the Windows partition and make use of the freed-up space by moving Ubuntu (root, home, swap)? Can I merge partitions using GParted? 

I think this can be quite tricky. I reckon I also need to update GRUB in that case. Just don't want to have any big surprises...

Thanks in advance!

---

### Post by wieman01 on 2006-08-10
Of course I could try to do it using PartitionMagic, but I am not sure how I would be able to update GRUB in that case... Just don't want to take the risk.

Thanks again.

---

### Post by soop on 2006-08-10
Why not just blow away the windows partition completely and just mount it as another mount point say /storage  or /home/storage or /home/username/storage or wherever you'd like it



If you need help let me know ...


> **wieman01 said:**
> Hey Guys, 

I am planning to remove my Windows partition but I have no idea how to do that without impacting my Ubuntu installation. My current configuration is this (see the attachment also):



Any idea how I can remove the Windows partition and make use of the freed-up space by moving Ubuntu (root, home, swap)? Can I merge partitions using GParted? 

I think this can be quite tricky. I reckon I also need to update GRUB in that case. Just don't want to have any big surprises...

Thanks in advance!

---

### Post by wieman01 on 2006-08-10
Good point, however, I want to merge it with the remaining (data) partitions in order to create a single big one. You see I have a number of fairly distributed data partitions around my Linux installation (for a number of reasons) but I want to do away with them once and forever. 

Therefore I need to merge them and move Ubuntu one way or the other. A tough one, hey? :-)

---

### Post by wieman01 on 2006-08-10
Is there anybody?

---

### Post by etank on 2006-08-10
First off make sure you have a backup of your stuff. Verify the backup. Test the backup again. Then read this thread [http://ubuntuforums.org/showthread.php?t=232925](http://ubuntuforums.org/showthread.php?t=232925). I would like to think that you could delete the Windows partition and then move/resize things and be safe. Good luck and let us know how it goes.

---

### Post by wieman01 on 2006-08-10
I'll give it a shot and keep you posted. Backups are no issue, because I keep my both computers in sync all the time. Thanks, man.

---

### Post by etank on 2006-08-10
Not a problem. I hope it works well for you.

---

### Post by wieman01 on 2006-08-10
Would you also know if the program also adjusts "fstab"? I am more worried about that actually. It may turn out that I cannot reboot after eliminating/merging partitions because the HD numbering would change as a consequence.

---

### Post by murataht on 2006-08-11
i am afraid you have to mess up with fstab yourself.

it wont be too difficult i think. you will just have home and /. so give it try, and there are always kind people to help you, if you are in some trouble. good luck.

---

### Post by wieman01 on 2006-08-11
> **murataht said:**
> i am afraid you have to mess up with fstab yourself.

it wont be too difficult i think. you will just have home and /. so give it try, and there are always kind people to help you, if you are in some trouble. good luck.

Alright, I thought so. I am not afraid to mess around with "fstab", just not sure if I will be able to **boot** at all after re-partitioning.

Can I use the live CD and change things in my local (root) file system if I have messed it up? Would I be able to change "fstab" this way?

---

### Post by maniacmusician on 2006-08-11
yes, you can do this, but make sure you do not change permissions or ownerships on any files while in the livecd environment, it could leave to conflicts. to accomplish what you want, boot from the live cd, and use the disk manager to mount your hard drive. in Xubuntu it is in Applications > System > Disks

---

### Post by wieman01 on 2006-08-11
> **maniacmusician said:**
> yes, you can do this, but make sure you do not change permissions or ownerships on any files while in the livecd environment, it could leave to conflicts. to accomplish what you want, boot from the live cd, and use the disk manager to mount your hard drive. in Xubuntu it is in Applications > System > Disks

Great, sounds brilliant. I am more confident now.

---

