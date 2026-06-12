---
title: "LVM with a corrupted disk."
date: 2006-08-24
forum: Desktop Environments
---

### Post by soulcoughy on 2006-08-24
Here's my story:
I recently added a disk to my LVM group that appears to have had bad sectors or something.  When the kernel attempts to read from a certain spot on the disk, it crashes.  As the disk is very new, it can't contain much data.  It has only been in the group for a day or two.  I want to remove the bad volume and replace it with another.  I've added the new volume and tried to use pvmove to get the data off the disk and remove it, but it crashes due to the problem with the bad disk!  Is there a way to just force the removal of the disk from the volume, and hope the filesystem can recover?  The only way I can think of to save my data is to transfer what I have now to another volume, then recreate the whole group and transfer it back.  The problem is, I don't have that kind of freespace!  I really don't want to lose my data!  Any ideas?

Thanks
Brian

---

### Post by soulcoughy on 2006-08-25
I fixed it.  dd is a lifesaver.  I dd'ed what I could from the bad disk to another, then did a pvmove on the target.  I lost a little data, but it seems to be mostly in tact, and xfs_repair seems to have caught most of it.

---

