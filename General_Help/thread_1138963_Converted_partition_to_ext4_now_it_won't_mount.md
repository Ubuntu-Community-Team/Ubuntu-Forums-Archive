---
title: "Converted partition to ext4 now it won't mount"
date: 2009-04-26
forum: General Help
---

### Post by glennric on 2009-04-26
I just upgraded to Jaunty, and thought I would try ext4 on one partition.  I converted the partition to ext4 using
```
tune2fs -O extents,uninit_bf,dir_index /dev/sdb2
```
Then I ran fsck on it, and tried to mount it.
It wouldn't mount and said
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
"dmesg | tail" returned
```
EXT4-fs: no journal found.
```
If I run fsck on the drive it shows it is clean.  If I check the partition in gparted it gives more information that seems to be saying the files on the partition are intact.  

How can I get this partition to mount?

There are about 9 large files on this partition (system backups).  It is not a big loss if I can't recover them, but it would be nice if I could.  Not to mention good practice in the event of an actual file system problem.

---

### Post by todak on 2009-04-26
Look [here]("http://www.cyberciti.biz/tips/linux-convert-ext3-to-ext4-file-system.html") and see if that might help.

---

### Post by glennric on 2009-04-26
Nope that doesn't help.  That is how I converted the partition to ext4, but then it won't mount.  I should point out that I have converted partitions to ext4 using that method on another, and they work fine.  Something odd is happening with that partition on this computer.

---

### Post by Beerprophet on 2009-04-26
[LEFT]I had the same problem about half an hour ago. The command that fixed it was this one: tune2fs -j /dev/XXX (where XXX is your drive).
It will say "Creating journal inode: done" by time, and after that you should proceed as in the tutorial (mounting, modifying fstab etc).
[/LEFT]

---

### Post by glennric on 2009-04-26
I have found a way to recover the files using sleuthkit.  The "fls" tool from that package lists all of the files on the drive with inode, and the "icat" tool can copy the files referenced by inode to another drive.

However, I still would like to figure out how to get this partition to mount.

---

### Post by Beerprophet on 2009-04-26
See my reply above. Forgot to add that apparently I was upgrading from ext2 to ext4, and never had ext3. Maybe this is part of the problem.

---

### Post by glennric on 2009-04-26
Beerprophet:  I will try that once I have the files backed up.

---

### Post by glennric on 2009-04-26
Yeah, I was converting from ext3 to ext4.  If I run "tune2fs -j /dev/XXX" I get "The filesystem already has a journal."  This seems to be at odds with what dmesg is telling me after attempting to mount the partition.

Any other ideas?

---

### Post by glennric on 2009-04-26
Never mind.  I gave up and reformatted the partition directly to ext4.  Now it works fine.

---

### Post by whoop on 2009-04-29
> **Beerprophet said:**
> See my reply above. Forgot to add that apparently I was upgrading from ext2 to ext4, and never had ext3. Maybe this is part of the problem.

groggyboy successfully converted from ext2 to ext3, see the second post in my HOWTO: convert ext3 your ext3 file system to ext4 (in jaunty): [http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

