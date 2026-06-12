---
title: "Odd disk size/usage numbers"
date: 2009-02-08
forum: General Help
---

### Post by themrfreeze on 2009-02-08
Hi all.

I'm pretty new to Linux, and am experiencing an odd problem.

I built a home theater PC and installed Mythbuntu 8.10 on it.  By default, it formatted my 250GB boot drive as follows:

primary partition:
/dev/sda1 12GB ext3, mount point / (6.5GB used)
extended partition:
/dev/sda5 915MB swap
/dev/sda6 220GB xfs, mount point /var/lib (71GB used)

I quickly found the boot partition too small, and the swap too small to enable sleep mode (I have 2GB of RAM), so I wanted to reformat the disk.  I booted off of a rescue CD and used partimage to make images of sda1 and sda6.  I then reformatted the disk using gparted as follows:

primary partition:
/dev/sda1 93GB ext3, mount point /
extended partition:
/dev/sda5 4GB swap
/dev/sda6 135GB xfs, mount point /var/lib

I then restored the two partitions from partimage (restoring sda6 required me to restore it to a 400GB external drive, then rsync it from there to sda6).

The system boots up just fine, but here's the problem.  If I do a 'df -h' command, sda1 appears as 12GB in size, with 5.5GB free...the size I had BEFORE the disk was reformatted.  If I open gparted, it shows sda1 as being 93GB in size, with 87GB used and 4.8GB free.  True to form, if I try to copy a file > 12GB in size to /, the disk runs out of space.  Why it says there's 87GB of data on sda1, I have NO idea.

I've been trying to accomplish this seemingly simple task for nearly a week now, and at this point I'm totally stumped.  Does anybody have any idea why I'm getting different sizes for sda1, and how it can be fixed?

Thanks much in advance for any help you can provide!

---

### Post by geirha on 2009-02-08
When you create a partition and then create a filesystem on that partition, the filesystem will by default, use the entire space of the partition, but it doesn't have to. The filesystem size can be any size <= partition size. When you copy the filesystem byte by byte, the filesystem will remain the same as before, and since the filesystem was 12GiB before, it will still be 12GiB when you copy it to the new partition, even if the partition is much larger. 

Resizing the filesystem is fairly easy though. Boot up the liveCD and run ```
sudo resize2fs /dev/sda1
``` When you don't give resize2fs a size parameter, it will resize to use the entire partition.

You'll probably be able to do this from the partition editor (System -> Administration -> Partition editor) as well, though I've never done that myself, so I don't know for certain if it has an option for it.

Your endevour would probably have been much easier if you just resized the partitions from gparted, instead of making images of the partitions and then recreating partitions.

---

### Post by themrfreeze on 2009-02-08
Thanks very much...that did the trick.

I actually did try resizing my partitions using gparted (after making the partimage backups), but for some reason it wouldn't let me do it.  Not sure why.

---

