---
title: "moving an LVM partition (a physical volume)"
date: 2009-03-06
forum: General Help
---

### Post by Xbehave on 2009-03-06
I want to move a partion to the end of the free space in front of it, but the free space is smaller than the partition. how do i do this?

Parted cant handle lvm partition and as far as i can tell despite a 2006 mailing list post they cant move a partitions raw data without knowing what fs it is. is this correct?

pvmove only deals with partitions so it cant move to an overlapping position. Am i wrong?

AFAIK this means i have to use the dd to manually move the data to the end of disk (/dev/hda , not even a partition) and then manually make the partition using parted (parted -mk ...). the problem is that i don't know how to make sure dd moved the end of the disk 1st (as the start will over-write itself otherwise), how do i do this?

*also it would be a lot easier if i could move all the used pv extents to the start of the pv and shrink it to that size as it wouldn't be larger than the remaining disk space anymore. how can i do that?

---

### Post by Xbehave on 2009-03-07
a nice man in #lvm helped me sort out the lvm problem
> [Fri Mar 6 2009] [23:49:48] <Romster> You must add in --alloc anywhere to be able to do this
[Fri Mar 6 2009] [23:49:48] <Romster> Say you have a gap in the PV at 1000-1200 and you want to remove the last 99 PEs off the bottom of the PV at 5100 on /dev/sda2.
[Fri Mar 6 2009] [23:49:48] <Romster> 
[Fri Mar 6 2009] [23:49:48] <Romster> # pvmove --alloc anywhere /dev/sda2:5001-5100 /dev/sda2:1000-1099
and even told me how to find the fragments
> [Sat Mar 7 2009] [00:04:09] <Romster> lvs -o +seg_count,seg_pe_ranges
[Sat Mar 7 2009] [00:04:12] <Romster> there we go.
[Sat Mar 7 2009] [00:04:38] <Romster> seg_count says how many fragments of the LV there is, 1 if it's contagious.
[Sat Mar 7 2009] [00:04:55] <Romster> seg_pe_ranges is the range of PV extents it uses.
[Sat Mar 7 2009] [00:05:50] <Romster> the annoying part is having to find the gaps. to get the right pvmove command.
[Sat Mar 7 2009] [00:06:16] <Romster> if you have more than 1 PV you can jsut say move LV name to another PV

and a [[COLOR="Cyan"]fedora howto[/COLOR]]("http://fedorasolved.org/Members/zcat/shrink-lvm-for-new-partition") showed me how to resize the lvm volumes


But now i have a new problem, ive managed to sort out the lvm stuff and move the extended partition to a primary partition, but id quite like get the actual partitions sorted too.
```
Number  Start    End         Size        Type     File system  Flags
 2      63s      144584s     144522s     primary  ext3         boot
 1      144711s  234441647s  234296937s  primary               lvm

```
how do i move partition 1 to start at 144585 instead of wasting 2 tracks (only a few kilobits)?
If i had ext i could just use parted but it seams parted never got round to implementing the raw mode and so it isn't up for the job (seams like nothing but ext is supported in linux these days).

could i do it with dd?
how can i reorder the partitions to have the correct numbering?
are there any partition tables better than ms-dos that Linux supports?

---

