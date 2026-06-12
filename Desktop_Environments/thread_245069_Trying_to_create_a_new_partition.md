---
title: "Trying to create a new partition"
date: 2006-08-27
forum: Desktop Environments
---

### Post by erikcw on 2006-08-27
Hi all,

I've been trying to create a new partition on my hard drive, but can't seem to get it working.

Background:
I am dual-booting XP and Dapper.  Here are the partitions:
01 HP-Recovery Partion - 8GB fat32 (/dev/sda1)
02 XP - 120GB NTFS
03 free (Status Hidden) - 91.45GB (NOTE:this is from a qtparted resize operation I did on my XP partition last night to try to free up space for a dedicated /home ext3).
04 / - 57.53GB ext3
05 extended 2.47GB
06 => linux-swap - 2.47GB


I'm trying to turn that free space on number 03 (/dev/sda-1) into an ext3 partition, but I'm not haveing any luck.

QTParted does not give me the option of creating a partition.  fdisk said there was no free space.

What am I missing?

Thanks!
Erik

---

### Post by RRS on 2006-08-27
You can only have 4 primary partitions on a drive.

If I'm reading your partition order correctly here's what might work for you:
>Expand your / to fill the free space forward
>Shrink the / from the back to effectively move the free space next to your extended partition
>Now stretch your extended forward into the free space.

This should allow you to create and formatt a new partition inside the extended partition.

You'll have to do this from a live cd as qtparted won't allow you to make changes to a mounted partition if you run it from your installed system.

If you could post a screenshot of your current partition layout from qtparted it may help verify if this is a workable solution or maybe help someone else provide a different (better?) fix for you.

---

### Post by erikcw on 2006-08-27
Thanks for the response!  Attached is a screen shot of my qtparted.  So I am effectively going to move my / partition "back" via resizing so that I can add another extended partition?

---

### Post by Ramses de Norre on 2006-08-27
No, so that you can enlarge your extended partition and make a new logical partition inside the extended one.
An extended partition is a partition that holds one or more logical partitions. This is done because you can only have 4 primary partitions on a hard disk and the extended one counts as one primary no matter how much logical ones there are inside.

---

### Post by RRS on 2006-08-27
> **Ramses de Norre said:**
> No, so that you can enlarge your extended partition and make a new logical partition inside the extended one.
An extended partition is a partition that holds one or more logical partitions. This is done because you can only have 4 primary partitions on a hard disk and the extended one counts as one primary no matter how much logical ones there are inside.


Correct, I think you explained it a little better then I had, thanks.

[QUOTE=erikcw]......effectively going to move my / partition "back" via resizing.......[/QUOTE]

You actually want to move your / partition (/dev/sda3) forward (left) towards the beginning of the drive and then expand /dev/sda4 to place the free space inside it and create another logical partition in addition to your swap partition in the extended partition.

Once the space is in the extended partition it can be further divided if you wish. I seem to recall the limit here is 10 or 20 logical partitions inside a single extended.

Remember though you can't do this with qtparted from Ubuntu itself as your / and swap partitions will be mounted so you have to run it from the live cd. 

The gparted live cd, available [here]("http://gparted.sourceforge.net/livecd.php"), might do a better job as it's a newer version then the one included with the Ubuntu cd.

---

### Post by erikcw on 2006-08-27
I've been trying to move my / partition left, but qtparted won't seem to let me.  "Move" is a disabled option for the partion, and resize will only let me resize down.

Am I missing something?  Should I be using another tool?

Based on the results of some google searching, I converted / from ext3 to ext2 to assist the moving/resizing.

Thanks!

---

### Post by RRS on 2006-08-27
Hmmm, I now seem to recall that qtparted only allows resizing to the left (says while rapping self on knuckles)

OK, plan B:
Since swap is the only thing in your current extended partition you could simply delete /dev/sda4.
Then create a new extended partition in the free space and a new swap partition in it.
You should now be able to expand /dev/sda3 to include the 2.47gb at the end of the disk.

Since your / partition position and # won't change this should have no effect on grub so your dual boot capability shouldn't be affected.

If anyone with more experience sees any flaws or potential pitfalls here your welcome to jump in.

BTW, just realised, your swap partition seems rathe large. The general recommendation is one to one and a half the size of your ram. If you have 1g or more of ram then the swap will probably be rarely used so I would thing 1g would be plenty. That's all I have with 512 ram.

Don't worry, one way or another we'll make use of your free space.

---

