---
title: "How to restore after a lvremove?"
date: 2006-05-11
forum: Desktop Environments
---

### Post by MichaelZ on 2006-05-11
Hello,

I wanted to resize a LVM partition, but I could not use GParted and QTParted. Therefore, I have done something quite stupid :(.

I have used a Live CD and in a terminal give the command:

> 
sudo lvremove /dev/hda5 -ff
 
Now, I cannot use Ubuntu normally. If I use GParted it still see the /dev/hda5 LVM (flag) partition.

Could someone please let me know how should I do to restore from the lvrmove command?

For info, GParted sees:

/dev/hda1 (ext3, flags: boot)

/dev/hda2 (extended, flags: none)
----/dev/hda5 (unknow, flags: lvm)

Thank you very much.

Best wishes,
Michael

---

