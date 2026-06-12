---
title: "Resize partitions without LiveCD"
date: 2009-02-12
forum: General Help
---

### Post by topher200 on 2009-02-12
I searched around, but couldn't find my question asked anywhere. I want to resize my partitions (using GParted or equivalent) but I don't have a CD drive to boot the LiveCD off of. Can I just unmount the drives and will everything be fine? Is there a mode I can boot into that won't mount them?

The only reason I ask is I know that you can get serious problems by messing with partitions, and without a CD drive I may not be able to fix them.

FYI- I've tried using a bootable USB stick before but I couldn't get it to work on this desktop.

---

### Post by blazemore on 2009-02-12
As long as you aren't using a partition, you can unmount it and resize it.
Just not your / partition.

---

### Post by topher200 on 2009-02-12
OK- so what if I want to resize my / partition? (it's one of two i want to increase)

---

### Post by swordfishRU on 2009-02-12
maybe it's simpler make a bootable live usb?

regards...

---

### Post by blazemore on 2009-02-12
Yes, the easiest is to boot from LiveCD or USB.

---

### Post by dcstar on 2009-02-12
> **topher200 said:**
> I searched around, but couldn't find my question asked anywhere. I want to resize my partitions (using GParted or equivalent) but I don't have a CD drive to boot the LiveCD off of. Can I just unmount the drives and will everything be fine? Is there a mode I can boot into that won't mount them?

The only reason I ask is I know that you can get serious problems by messing with partitions, and without a CD drive I may not be able to fix them.

FYI- I've tried using a bootable USB stick before but I couldn't get it to work on this desktop.

You **cannot** resize an in-use partition, if you cannot boot off a USB then you need to move that hard drive to a PC that can be booted, and resize it on that.

---

