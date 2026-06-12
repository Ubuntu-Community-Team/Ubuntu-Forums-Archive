---
title: "4 Primary Partitions, no Swap?"
date: 2008-12-07
forum: General Help
---

### Post by Xpyd3r on 2008-12-07
I'm trying to install Ubuntu on a harddrive with 4 Primary paritions, one of which is free for Ubuntu. But since I have 4 Primary already, what can I do about the Swap space?

---

### Post by hambone79 on 2008-12-07
You can replace the 4th primary partition with a logical partition that contains the root partition and the swap partition. You should be able to do this when you install Ubuntu.

Another option is to install Ubuntu on the primary partition and create a swap file (instead of a swap partition) on the root partition. This trick will allow you to create a swap file as big as you want which you can always resize later on. You can find more info here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by CatKiller on 2008-12-07
I can't add anything to your advice, hambone, which is exactly what I'd have said. A quick nomenclature correction, though, so that the OP can find more information to read should it be necessary; the final primary partition would be an *extended partition* (you can only have one extended partition) and the partitions inside that partition are *logical drives*. As far as I am aware, there is no limit short of drive capacity on the number of logical drives that are possible.

---

### Post by Slim Odds on 2008-12-07
> **CatKiller said:**
> ...the final primary partition would be an *extended partition* (you can only have one extended partition) and the partitions inside that partition are *logical drives*. As far as I am aware, there is no limit short of drive capacity on the number of logical drives that are possible.

That's a very "Windowsish" view of the partition table. I think that that wikipedia article needs an update.

From the Linux Partitioning HOWTO:
> **3.4. Logical Partitions**

     One primary partition of a hard drive may be subpartitioned. These     are logical partitions. This effectively allows us to skirt the     historical four partition limitation. 
     The primary partition used to house the logical partitions is called     an extended partition and it has its own file system type (0x05).     Unlike primary partitions, logical partitions must be contiguous.     Each logical partition contains a pointer to the next logical     partition, which implies that the number of logical partitions is     unlimited. However, linux imposes limits on the total number of any     type of partition on a drive, so this effectively limits the number     of logical partitions. This is at most 15 partitions total on an     SCSI disk and 63 total on an IDE disk. 
I think that explains it better.

---

### Post by falcon61102 on 2008-12-07
potatoe v. potato

The point was effectively delivered so the average user can understand it, is there anything better than that?

---

### Post by CatKiller on 2008-12-07
> **Slim Odds said:**
> That's a very "Windowsish" view of the partition table.

Could be. I learned partitioning mostly by trial-and-error back when I was using DOS, so I'd imagine that it's only really applicable to BIOS systems, rather than anything that handles disks differently. I suspect that it's relevant to pretty much everyone that's using this forum, though.

> From the Linux Partitioning HOWTO:
I think that explains it better.

As falcon says, we've got the point across between us. Extended Partition is definitely the well-understood term, and it can be referenced pretty much anywhere. *Logical* is pretty much useless as an adjective in this case, since it has more-or-less opposite meanings depending on the source of the information.

---

