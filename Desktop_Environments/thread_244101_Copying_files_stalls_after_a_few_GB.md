---
title: "Copying files stalls after a few GB"
date: 2006-08-25
forum: Desktop Environments
---

### Post by egd on 2006-08-25
I'm having copy stall problems getting data off NTFS partitions onto an ext3 formatted drive - similar to that described by ZagiFlyer @ [http://www.ubuntuforums.org/showthread.php?t=212964](http://www.ubuntuforums.org/showthread.php?t=212964), however, in my case there is no network involved.

The source drives are all mounted READ-ONLY and I can access any file individually. Whether I use Nautilus copy/paste, Krusader or Midnight Commander to copy my data off the NTFS partition to the ext3 partition, the copy operation starts like a bull in a china shop and then slowly grinds to a halt after roughly 7-12GB, ultimately causing Ubuntu to grind to a halt and requiring a hardware reset. This occurs irrespective of what data/directory tree I'm copying from.

At first I thought the target drive may be faulty (it's been in use for years) so I checked it and thereafter the source drive using manufacturer diagnostics and both drives checked out OK, report no file system errors etc. To be on the safe side I used GParted to repartition and reformat the target drive and retried the copy operation. Same proplem occurs...copy operation stalls and Ubuntu grinds to a halt requiring a hardware reset.

My strategy was simple - install Ubuntu, get one additional empty hdd, copy data off NTFS partitions to ext3, repartition and reformat NTFS partitions to ext3, et voila Windows - kiss my proverbial *** goodbye. Of course, it's never that simple, is it.

Three things I'd add:
- The same copying operation of the data under wxp or w2k3 completes without incident, stall or any issue;
- seems unlikely to be a network issue as described by ZagiFlyer; and
- we're not the only ones experiencing these problems [http://www.ubuntuforums.org/showthre...t=stalled+copy](http://www.ubuntuforums.org/showthre...t=stalled+copy) & [http://www.ubuntuforums.org/showthre...t=stalled+copy](http://www.ubuntuforums.org/showthre...t=stalled+copy)

I'm running ubuntu-6.06.1 on an Intel d975xbx, kernel 2.6.15-26-amd64-generic #1 SMP PREEMPT

Anyone have any ideas to resolve the issue? Seems to me like it may be a kernel bug and needs reporting?

---

### Post by egd on 2006-08-26
bump...

---

### Post by egd on 2006-08-27
> **egd said:**
> Anyone have any ideas to resolve the issue? Seems to me like it may be a kernel bug and needs reporting?

So I'm guessing I'm lucky enough to stumble upon a problem nobody has any idea how to begin to tackle or resolve.  Can anyone at least point me to an escalation path, I most definitely don't want to find myself reverting to any form of windows.

---

### Post by egd on 2006-08-31
For the benefit of others ...

I have found the cause of the problem. The target drive was a PATA drive with a PATA->SATA converter plugged in. Basically I think the drive or the converter was choking under throughput. When I replaced the target drive with a native SATA drive the problem disappeared.

---

