---
title: "ext3 or XFS?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by gary79 on 2005-10-18
I'm setting up a samba server to share 250gb of video.

Most of these files are around 1gb each but there are also TV programs around 200-350mb.

This will be shared over a 100mb LAN with a run of the mill VIA KT333 mobo and 1700+ amd.

To squeeze as much speed as I can but while still stable, what is the best file format choice.

---

### Post by yage on 2005-10-18
I would recomend XFS when dealing with files of this size...

---

### Post by bluck on 2005-10-18
[QUOTE=gary79]I'm setting up a samba server to share 250gb of video.

Most of these files are around 1gb each but there are also TV programs around 200-350mb.

This will be shared over a 100mb LAN with a run of the mill VIA KT333 mobo and 1700+ amd.

To squeeze as much speed as I can but while still stable, what is the best file format choice.[/QUOTE]

using xfs with a larger block size will likely give you better performance and less fragmentation.  its capable of block sizes up to 64KB.  I would only recommend this if you're filling the drive with relatively large files.  I believe XFS has a higher limit for maximum file size, as well.

---

### Post by metoo on 2005-10-18
One mobo? It's not my mother tongue, so "a run of a mill" doesn't say anything to me, but in case it is just one mobo or one 100Mbit line:

Use ext3 .
In case of emergency you can still access it in ext2 compatibility mode. XFS might be great, but sometimes has issues. It's more for the big kids (big servers).
ext3 is more integrated into the kernel, you should not have any problems with this.

You don't have a performance issue anyhow. Every file system can do way more than your little 100Mbit (that's what you meant, right?) network and locally to view the stuff, it's just a piece of cake for any file system.
Ext2 might be the fastes using the least CPU usage and you have a backup for sure.
But if you want to play it save, use ext3.

---

