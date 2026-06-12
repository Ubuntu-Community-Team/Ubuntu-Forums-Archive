---
title: "Ext4 system hang on deleting directory"
date: 2009-04-27
forum: General Help
---

### Post by jasper_m on 2009-04-27
Hello,

I have installed filesystem as EXT4, /, /home, /var being separate partitions. 

Now I have copied a large directory (my old /var) to my home directory (not encrypted) with SCP, and when I try to delete it with rm -Rf the system hangs and must be rebooted (no reaction to even caps lock etc).

fsck.ext4dev says the FS is fine though.

Is there a known solution for this?

Thank you in advance,
Jasper

---

### Post by Inwards on 2009-04-29
Just had the same issue here on a clean Jaunty install.  This is un-good.  I was looking forward to the ext4 speed increase, but if this is any indication, it's not worth the risk.

---

### Post by rainydayz on 2009-05-12
I have the same problem. Impossible to predict whether a delete action is going to cause a hard hang.

---

### Post by waterfox on 2009-05-13
I have the same problems. When I delete files fra the trashcan it freezes. The same has happened a few times when I transfer big files to an external HD. If this is a issue concerning ext4 I better go back to ext3 and wait until the problem gets fixed, maybe with 9.10? I have also experienced very slow transfer from internal HD to external HD, many times as low as 2-4 Mb/s

---

### Post by azolotko on 2009-06-10
You can find additional information about this bug here:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/330824]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/330824")

---

### Post by afeasfaerw23231233 on 2009-09-10
I wish I saw this thread earlier. Now I experienced exactly the same problem. What should I do now? 
My system is ubuntu 9.04 x64 with ext4 file system.

---

### Post by afeasfaerw23231233 on 2009-09-10
Last time I was copying 40GB files. During the copying I emptied the trash box. Then my computer freezed, I could do nothing but press the hard reset button. After reboot I noticed that the disk space reduced by around 20GB, but the files that ought to be copied disappeared. 

I already fsck my drive. But the disk space is still 20GB less then it should be. What can I do to fix it? Thanks in advance!

---

