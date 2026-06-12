---
title: "auto fsck of vfat ?"
date: 2005-04-29
forum: Desktop Environments
---

### Post by bazder on 2005-04-29
I installed Hoary on a separate second
drive /dev/hdb

Will it try to auto fsck the first drive
even though there's no mention of the
first drive in /etc/fstab because the master
boot record *is* in /dev/hda ?

I think the auto fsck actually screwed up
an earlier ntfs partition when I was using
Warty and I'm trying to avoid that happening
again.  I'm hoping FAT32 on a completely
separate drive will be less problematic?

---

### Post by bored2k on 2005-04-30
[QUOTE=ubuntu-geek]Please do not post questions here. This is for HOWTO's and FAQs only.[/QUOTE] Clear and simple. No questions on the Tips n Tricks subforum.

---

### Post by nad on 2005-04-30
At boot, fsck checks the /root file system only to see if it is clean. If is dirty it will then attempt to repair it. After a certain number of mounts (~30) it will run a full test to doublecheck.

As /root can not be on an ntfs file system there is no issue here. Your master boot record is another story. As the mbr is before any file system, fsck will never see it. Only programs that address the mbr can affect it. Maybe you had a grub issue.

Where does fat32 come into this?

---

### Post by bazder on 2005-04-30
[QUOTE=nad]
As /root can not be on an ntfs file system there is no issue here. Your master boot record is another story. As the mbr is before any file system, fsck will never see it. Only programs that address the mbr can affect it. Maybe you had a grub issue.

Where does fat32 come into this?[/QUOTE]

the auto fsck after 30 boots checked the entire previous drive including
the ntfs partition and I think it screwed it up as problems with that file
system appeared immediately after that (this happened twice with a
reinstall in between).

now the linux / is on a separate drive (IDE2)

XP is on a separate drive (IDE1) with two FAT32 partitions.

I want fsck to check the Linux drive and leave the other one alone.
From what you say it probably will - thanks.

---

### Post by N17R0 on 2005-05-28
[QUOTE=bazder]the auto fsck after 30 boots checked the entire previous drive including
the ntfs partition and I think it screwed it up as problems with that file
system appeared immediately after that (this happened twice with a
reinstall in between).

now the linux / is on a separate drive (IDE2)

XP is on a separate drive (IDE1) with two FAT32 partitions.

I want fsck to check the Linux drive and leave the other one alone.
From what you say it probably will - thanks.[/QUOTE]

Is this true that after 30 boots fsck checks the whole hard diks, and might screw up my NTFS partitions?
That would be **REALLY** bad!

---

### Post by N17R0 on 2005-05-31
[QUOTE=N17R0]Is this true that after 30 boots fsck checks the whole hard diks, and might screw up my NTFS partitions?
That would be **REALLY** bad![/QUOTE]

Please someone confirm this, I am linux newbie so I don't know if this is true.
And IF this is true, then how can I prevent this?

TIA

---

### Post by spencer on 2005-05-31
[QUOTE=N17R0]Is this true that after 30 boots fsck checks the whole hard diks, and might screw up my NTFS partitions?
That would be **REALLY** bad![/QUOTE]



Yes, I would like to no for certain the answer to this question too.

-spencer

---

### Post by spencer on 2005-06-01
[QUOTE=nad]As /root can not be on an ntfs file system there is no issue here. Your master boot record is another story. As the mbr is before any file system, fsck will never see it. Only programs that address the mbr can affect it. Maybe you had a grub issue.[/QUOTE]


Here is the answer in the above quote. I'll read more carefully from now on. Thanks.

-spencer

---

