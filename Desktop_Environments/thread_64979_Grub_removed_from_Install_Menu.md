---
title: "Grub removed from Install Menu"
date: 2005-09-12
forum: Desktop Environments
---

### Post by hawkeye1315 on 2005-09-12
Hi,
I am trying to install Hoary using expert mode. After partitioning my single 20 BG HD as follows (approx figures):
10 GB FAT32 for WinXP
9.9 GB LVM
- 9.4 GB ext3 /
- 512 MB swap
100 MB ext3 /boot

and returning to the Install menu, Grub is now removed from the list of install options, leaving me with LILO as the only choice. I have seen other posts here with people succesfully installing both Grub on LVM partitioned systems. Is there something with my partitions that Grub can not handle and thus is being removed as an install option? Thanks in advance

---

### Post by tonysathre on 2005-09-13
i have a question first, why are u running xp on a FAT32 partition?

expert mode? at the boot prompt did u just hit enter? thats the easiest way to install

---

### Post by hawkeye1315 on 2005-09-13
I am running WinXP on a FAT32 partition because I may need to access files from both O/Ses...unless there's another way I'm not familiar with.

No I did not just hit enter at the prompt, I typed "expert" and hit enter. I find you learn more by taking control, experimenting and making mistakes rather than just automagick like in Windows.

---

### Post by tonysathre on 2005-09-13
i would suggest u just hit enter because its a lot easier to do, ask anyone on here, i havent heard anyone say they wanted to do it the hard way before. yes there is a way to access files on a NTFS partition from linux, first open a terminal and type:

sudo mkdir /media/windows

then type this to backup your fstab:

sudo cp /etc/fstab /etc/fstab_backup

then type: (any text editor will work)

sudo gedit /etc/fstab

then on the bottom line of the file add this:

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

doing this will allow the NTFS partition to automount on boot as read-only so you can view your xp files.

PS: the spacing on  line that needs to be added to your fstab is not correct.  you should be able to tell where each item needs to line up, just look at the other lines in the file for reference.

---

### Post by hawkeye1315 on 2005-09-13
I am aware of the NTFS mounting method you mention. However, this method only allows me to see files created under WinXP from the Linux O/S but does not allow the inverse: I also want to "see" files created under Linux from the WinXP O/S (ie: I want to be able to read and write from and to either O/S).

I don't udnerstand why you say my partitions are complicated. Aside from the FAT32 Windows partition, I have one ext3 /boot partition and one LVM partition that holds my / and swap space. From the page you provided:

"The "normal" way of running an LVM root file system is to have a single non-LVM partition called /boot  which contains the kernel and initial RAM disk needed to start the system."

So that explains why I have an ext3 /boot partition. Now as for the LVM, I simply wish to take advantage of LVMs features. For example, if I wanted to add another hard disk and have the space made available under / I can now do so with the LVM partition. If it were a simple ext3 partition, I would have to either reformat and reinstall or remount some other directory to that drive. Correct me if I am wrong.

As for the swap partition, true I didn't have to mount it under LVM but if I add more RAM, I could resize the swap partition using the same LVM techniques.

Please let me know if I am wrong with any of my understanding.

P.S. I can appreciate that it may be "easier to do", but IMHO, part of the beauty of Linux is that you can customize, tweak and play with it to get it to do just what you want without having to install things you don't want or need. If that's called doing it the "hard way", then I am suprised I am the first that you have heard who wants to do this.

---

### Post by tonysathre on 2005-09-13
i would try installing with normal mode and see if that works, then install LVM after installation

---

