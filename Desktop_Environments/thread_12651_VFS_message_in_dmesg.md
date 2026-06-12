---
title: "VFS message in dmesg"
date: 2005-01-26
forum: Desktop Environments
---

### Post by buldir on 2005-01-26
VFS: Can't find ext3 filesystem on dev hda2.
VFS: Can't find ext2 filesystem on dev hda2.

Why would I be getting these messages during bootup?  I am using reiserfs for both my drives.  Here's my /etc/fstab:

proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs defaults        0       1
/dev/hdb1       /export         reiserfs defaults        0       2
/dev/hda3       /home           reiserfs defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdb2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

Thanks.

---

### Post by tsvetan on 2005-01-26
I have the same issue.  The same messages with root reiserfs partition.
  The system boots and works ok, but it seems that the boot process is slower than it can be.

---

### Post by kingmob on 2005-02-11
I have the exact same problem :(.

---

### Post by jeremy on 2005-02-11
Me too.

---

### Post by Davepet on 2005-02-11
I have the same situation, but I don't think it's so much a "problem". I suspect that the boot process systematically scans for the various filesystem types & is just reporting the progress. They could have used a less alarming message, IMHO.

It *would* be nice to be able to eliminate that step & speed up boot time, though.

dave

---

### Post by kxs on 2005-06-27
same problem here. if it`s not something to worry about then how to get rid of this message?

---

