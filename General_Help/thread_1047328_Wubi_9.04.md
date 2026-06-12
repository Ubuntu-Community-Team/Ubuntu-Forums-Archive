---
title: "Wubi 9.04"
date: 2009-01-22
forum: General Help
---

### Post by HackerMan on 2009-01-22
Hi,

The major reason for this thread is to ask is the hibernate will be sipported by Wubi 9.04 of the next release of Ubuntu 9.04 ?

And if it will not damage the linux partition if windows crashs ?

Thank you very much in advance
HackerMan

---

### Post by azmo35 on 2009-01-22
Hi, the biggest reason that hibernate dosen't work on wubi, is because wubi it is kind off virtual and so if windows crashs it crashs ubuntu because no real partitions with wubi,i hope this help.

---

### Post by Yashiro on 2009-01-22
The answer is very probably, no. Hibernate hardly works 100% on 'proper' installs anyway. No great loss.

And wubi is not 'virtual'. It runs from a filesystem that is mounted from an NTFS partition.

---

### Post by azmo35 on 2009-01-23
Well,maybe so but [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) seed it is but maybe i'm wrong,sorry.

---

### Post by ago on 2009-01-24
It depends on whether the kernel will be able to hibernate using a swap file (as opposed to a swap partition).There was some work in this direction, but not sure whether it will be in 9.04 or not.

As for windows crashes corrupting linux, the situation was already much improved in 8.10. So that is unlikely. 

What will still happen is that if the windows filesystem becomes corrupted (because of a hard shutdown for instance), then it will not possible to mount the windows partition (and hence wubi if it was installed in there) until the windows fs is cleared from windows (chkdisk). This is because there are no linux tools at the moment to do fsck on ntfs.

---

### Post by Yownanymous on 2009-01-24
Hibernation mode is just a bain on your hard drive. Swap partitions are both old and very slow and overall unnecessary. Plus in the end they'll get so mixed up with data you'll find yourself with a nice corrupted disk.

---

