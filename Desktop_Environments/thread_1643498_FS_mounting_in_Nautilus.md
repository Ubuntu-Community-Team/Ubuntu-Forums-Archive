---
title: "FS mounting in Nautilus"
date: 2010-12-12
forum: Desktop Environments
---

### Post by bugsvoid on 2010-12-12
Hello all,

I would like to understand how Nautilus automatically mounts the file systems / partitions which are not mounted automatically during boot time.

I have a ext3 partition (say, labelled 'misc') on my HD,this is separate from the root partition.

Now when I boot into Gnome, this partition is not automatically mounted. But when I open Nautilus, this partition appears in the computer. When I double click it, Nautilus automatically mounts this partition (under /media/misc). I am curious how Nautilus decides where to mount the partition & with what parameters. I have 2 issues here:

1. At times, the FS gets mounted to /media/misc, at times it gets mounted at /media/misc_. I have observed that sometimes the partition does not get unmounted correctly hence another directory is required when remounting. This is an issue if I want to have a soft link for this partition. Why is this going wrong?

2. I want to tweak the parameters with which this partition gets mounted. How do I set that (like owner, access permissions etc)? Is there any way APART FROM ADDING A SPECIFIC ENTRY IN FSTAB?

Regards,
Bugs

---

