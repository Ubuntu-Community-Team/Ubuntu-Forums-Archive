---
title: "Hard drive related lock ups"
date: 2009-04-08
forum: General Help
---

### Post by digimatic on 2009-04-08
Solved..but I thought I would post here as it has taken me days of searching and eventually guesswork to solve this so hopefully it will be helpful to someone else.

Intel Quad core with raid 5 on sata drives ICH9 SATA controller and XFS

For a while now I have had strange lockups when running "busy" virtual machines via VMware...I was initially blaming Vmware and then suspecting a hardware fault even though memtest etc found nothing amiss. Generally when under heavy disk access the machine would slowly grind to a halt. Eventually only a ping would respond.

Then I upgraded my network to 1000baseT and then noticed that copying a large file (50GB) via NFS would also result in the same lockup with 100% repeatability..Usually about a quarter of the way though.

I tried copying the same file via scp..this also resulted in the copy operation stalling at roughly 40% but I was able to halt the scp process and then the machine came back as normal.

After lots more hardware tests..some head scratching and lots of net searching I decided to blame the cfq scheduler which is default in ubuntu desktop but not in the few Ubuntu Servers I have deployed with a similar configuration.

In the end adding elevator=anticipatory to my boot line appears to have cleared this problem, you can of course just prod /sys in the right way to do this at runtime..but adding the elevator line does it for all block devices in my array.

Since doing this I can run multiple VM's whilst also copying the same file with no problems. So it looks like cfq might be a bad choice with software raid and/or xfs and a heavy disk load.

---

### Post by dcstar on 2009-04-09
> **digimatic said:**
> 
........
Since doing this I can run multiple VM's whilst also copying the same file with no problems. So it looks like cfq might be a bad choice with software raid and/or xfs and a heavy disk load.

I use Reiserfs for my VMs, it seems to be a good choice for the nature of VMs (large filesize efficiency, and I can turn off useless overheads like access timestamping) and I have had no problems with copying big files using the default CFQ.

That said, I don't use software RAID or really hammer the VMs that often.

---

