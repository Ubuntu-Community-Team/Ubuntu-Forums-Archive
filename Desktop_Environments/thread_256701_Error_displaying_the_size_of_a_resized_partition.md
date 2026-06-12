---
title: "Error displaying the size of a resized partition"
date: 2006-09-13
forum: Desktop Environments
---

### Post by TheForkOfJustice on 2006-09-13
I've recently used my LiveCD to resize my /home partition to get rid of +90GB of empty space.

I also had a chroot set up _exactly_ like it says here:

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

I had made an error, I believe, by including the fstab edits that linked the /home directory to /ver/chroot/home as suggested by the above link so things would be 'easier'. I had already had /dev/hda4 linked to /home.

Now when I go into gparted, hda4 displays that it is almost full, when in fact it now should have +90GB of free space available. I believe it's showing the amount of space left in my root partition, while at the same time saying it is the size of my /home partition, hda4.

I commented-out the additions to my fstab and rebooted. No change.

How do I fix the ability of the system to detect  the proper size AND empty space of hda4?

ALSO

Why can't Ubuntu (kernel 2.6) read NTFS extended partitions but Puppy Linux (kernel 2.4) can? I had an extended partition in there before under WinXP but had to get rid of it since Ubuntu couldn't read it, hence leading to my current problem.

If I reinstall Ubuntu and redo partitioning, can I create an extended partition and use a partition in that as my new /home folder?

---

