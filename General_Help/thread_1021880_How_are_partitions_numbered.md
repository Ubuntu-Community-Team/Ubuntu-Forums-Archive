---
title: "How are partitions numbered?"
date: 2008-12-26
forum: General Help
---

### Post by noctis_vulpes on 2008-12-26
Hi, I was messing around with my partitions, and I just became curious:

This is what my partitions look like right now

sda1 - ntfs,
sda6 - ext3, /
sda7 - ext3, /home
sda8 - swap
sda5 - ntfs,

I initially divided my HDD with Windows install CD into 3 parts - C, D, and E drive. sda1 is C, sda5 is E, and sda 6~8 are what used to be D. 

Now, I was wondering exactly what are the rules being applied to the numbering of those partitions? That is, why are they numbered the way they are right now?

I just got curious, because I can't figure out why sad 2~4 should be missing from that list. sda1 is primary partition, so that makes sense... but I am not really sure why rest of them are numbered so.

Can anyone give me an explanation?

Thanks.

---

### Post by p_quarles on 2008-12-26
1-4 are reserved for primary partitions. It appears that you have one primary partition, one extended partition (which doesn't show up as such because it is not mounted) and four logical partitions numbered 5 through 8.

---

### Post by ELF_O8 on 2008-12-26
> **p_quarles said:**
> 1-4 are reserved for primary partitions. It appears that you have one primary partition, one extended partition (which doesn't show up as such because it is not mounted) and four logical partitions numbered 5 through 8.

True Dat.

---

### Post by noctis_vulpes on 2008-12-26
p_quarles: Thank you so much for that explanation. I guess I should have been able to figure that out, knowing that there can only be 4 primary partitions...

so sda2, technically, would refer to the extended partition itself?

---

