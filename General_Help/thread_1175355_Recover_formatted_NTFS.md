---
title: "Recover formatted NTFS"
date: 2009-06-01
forum: General Help
---

### Post by nuttycc on 2009-06-01
I did such a stupid thing; in my computer I have sda with Ubuntu on, sdb with Windows XP and (when I made my mistake) sdc with my USB pen in. 

At root prompt I typed 'mkfs -t vfat /dev/sdb1' instead of sdc1 :oops: it didn't seem to 'wipe' everything, the process took seconds and it is a 250 gig drive/partition. Is there anything I can do :(

---

### Post by nuttycc on 2009-06-01
[http://www.handhelds.org/pipermail/familiar/94/9459.html](http://www.handhelds.org/pipermail/familiar/94/9459.html)

I followed the instructions in there and it didn't work :(

---

### Post by dandnsmith on 2009-06-01
That 'solution' is totally inappropriate, and may have wrecked the XP partition irretrievably. You've already told it to make an ext3 filesystem (which will have inserted suitable master inodes), and then completely removed the traces by clearing the partition table to write a new one.

I don't suppose you have that disk backed up with a full image?

Failing that, the best hope is a manufacturers recovery partition and software.

You might be able to get a lot files from the HDD, but I don't value the chances of a full recovery of applications and data.

---

