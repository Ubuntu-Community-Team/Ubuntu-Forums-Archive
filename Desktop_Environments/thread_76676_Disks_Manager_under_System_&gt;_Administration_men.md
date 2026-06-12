---
title: "Disks Manager under System &gt; Administration menu"
date: 2005-10-15
forum: Desktop Environments
---

### Post by unclben on 2005-10-15
I have a couple partitions I'd like to automount at every boot. One is a partition on the same disk as my Ubuntu install, formatted ReiserFS. The other is a partition on a separate HDD in the same computer, formatted NTFS. I have added folders for each in /mnt.

I was going to do everything directly in fstab, but then I noticed the nifty 'Disks' tool under the System > Administration menu. For both drives, I picked the correct 'Access Path' in /mnt. For both drives, I hit the 'Enable' button. Unfortunately, I can only access the files as root and Ubuntu doesn't automount them at the next boot.

Am I doing something wrong, or is the Disks Mgr only useful for temporary, root-user file access to other drives?

(side note: In the course of all this, I finally read the man page for fstab. It may be the most helpful one I've seen yet.)

---

### Post by unclben on 2005-10-17
bump-ola

---

