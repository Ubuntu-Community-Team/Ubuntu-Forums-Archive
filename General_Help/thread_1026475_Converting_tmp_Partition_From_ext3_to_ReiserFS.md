---
title: "Converting /tmp Partition From ext3 to ReiserFS?"
date: 2008-12-31
forum: General Help
---

### Post by adamlau on 2008-12-31
/tmp is on a separate partition. Wanted to convert the existing ext3 filesystem to ReiserFS. Since /tmp is destroyed and recreated upon boot time, can I simply:

1. Modify /etc/fstab to reflect reiserfs for /tmp.
2. Reboot into GParted Live [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).
3. Delete and recreate /tmp with ReiserFS.
4. Reboot into a properly working system.

And will changing the filesystem type modify the UUID of the partition? Need some answers before I proceed, thanks!

---

### Post by ibutho on 2008-12-31
/tmp is not destroyed and recreated upon boot time. Some distros and other Unix like operating systems empty the contentsof /tmp at shutdown or boot time and others do it after a set amount of time e.g. daily, weekly etc. 

Your steps should work. You can even use the Ubuntu live cd i you wish because its partitioning tool is actually gparted.

---

