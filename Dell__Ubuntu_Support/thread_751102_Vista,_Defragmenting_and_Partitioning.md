---
title: "Vista, Defragmenting and Partitioning"
date: 2008-04-10
forum: Dell  Ubuntu Support
---

### Post by atish on 2008-04-10
Dear All,

I have a Dell XPS M1530 Product Red which comes with Windows Vista. The HDD is 320 GB. I want to partition the disk and install Ubuntu (with allocation of about 250 GB) alongside Vista. However, when I run a defragmenter, it shows that a small chunk of memory blocks being occupied somewhat midway of the full HDD. Since, contiguous memory of 250 GB is not available, I will have to devide the HDD memory into 50%-50% for Ubuntu and Windows. Allocating about 150 GB to Windows would be a waste :-(

I have run the defragmenter for 4-5 of times but it has not released 'those' memory blocks.

I am worried if 'those blocks' are storing some vital Vista files and if I force partitioning then the Vista might give problems or worst that the laptop may not even boot into the Vista.

Has anyone else faced a similar problem ?

Can someone tell me what could be a possible solution ? I do not want to get rid of Vista at this stage as the laptop has some warranty benefits with it.

Help ! Help ! :confused:
- Atish .

---

### Post by pbcartwright on 2008-04-10
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)
Dual-Booting Windows XP/Vista And Ubuntu 7.04

In this tutorial I will teach you how to dual-boot between Windows XP/Vista and Ubuntu.

This tutorial will be split up into two parts:

    * Part one for people who have no operating system installed.
    * Part two for people who have Windows XP/Vista installed and don't want to re-install Windows.

---

### Post by thebigbluecan on 2008-04-11
Try on vista a program called "auslogics disk defrag"... Google it... It might help.

---

### Post by SirKhan on 2008-04-11
atis, try this program, called Acronis*Disk Director Suite! it's the "most best" for Vista I have seen so far (and I've seen a few, believe me) I'm 99% sure it will handle your resizing/partitioning problems! ;)

---

### Post by atish on 2008-04-28
Dear pbcartwright, thebigbluecan and SirKhan,

Thanks for your replies. I tried the suggestions by you all and especially by "pbcartwright". Unfortunately, shriking VIsta did not work as much as I wanted because, I believe, there were some "immovable" file. However, the problem has been solved : I used GParted to partition the disk and asked it to shrink the disk to the desired size. GParted is smart enough and can read, write, copy, move, delete the NTFS (windows) files. And it did move the "immovanle files" as well as partitioned the disk to my desired size.

Many Thanks,
- Atish .

---

