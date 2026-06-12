---
title: "Creating Windows Partition"
date: 2009-06-17
forum: General Help
---

### Post by phillyman1025 on 2009-06-17
I have a completely ubuntu machine and I was wondering how to create a windows partition for dual booting.

---

### Post by VMC on 2009-06-17
> **phillyman1025 said:**
> I have a completely ubuntu machine and I was wondering how to create a windows partition for dual booting.

Get Gparted and open it from a livecd. Then shrink either from beginning or the end. Windows doesn't like to be anywhere but first partition. You can circumvent that though. Once you shrink your linux partition then use Gparted to create NTFS.

If you do move Ubuntu to second partition you might have to redo UUID's.

---

### Post by coffeecat on 2009-06-17
As you don't give specific details of your partition layout, I can't give you specifics, but the easiest way is to boot up from the live CD and go to System > Adminstration > Partition Editor to create a NTFS partition for Windows. If you have unallocated space on your disc you can use that, or you might have to shrink your Ubuntu root partition to make space. If you do the latter, ensure you have backed up fully in case of a catastrophic failure - it happens occasionally.

Two other things to be aware of:

Windows **must** boot up from a primary partition. Linux does not have this limitation. Depending on your partition layout, it may or may not be difficult to create another prinary partition for Windows.

When you install Windows it **will** overwrite the MBR meaning that temporarily you won't be able to boot into Ubuntu. You will have to repair grub. You will then have to edit grub's menu.lst file to add an entry for Windows, otherwise you won't be able to boot into Windows.

Have fun! :)

---

### Post by coffeecat on 2009-06-17
> **VMC said:**
> Windows doesn't like to be anywhere but first partition.

Point of information - this is not entirely so. Windows does not have to be on the first partition, merely on a primary partition, which can be the second third or fourth instead of the first. I have two laptops, each with Windows (one XP, one Vista) on the second partitions.

In fact Windows only has to boot from a primary partition. If you put the NTLDR in a primary and do some clever hacking, you can even put Windows on a logical partition. But life is short - Windows on a primary, any primary, is good enough for ordinary mortals. :p

---

