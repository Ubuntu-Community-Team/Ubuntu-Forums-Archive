---
title: "Saving files when switching to Ubuntu."
date: 2013-12-17
forum: Debian
---

### Post by ben20 on 2013-12-17
I am planning on switching from another Linux OS to Ubuntu 12.04 LTS.  The only problem I have is that I've been using another OS for so long  and have so many files on the current OS that I don't want to lose those  files when switching to Ubuntu. Is there any way to backup files from another OS and put them in Ubuntu. Thanks All.

---

### Post by buzzingrobot on 2013-12-17
The surest way is to back up the files to a USB stick or an external drive and restore them once Ubuntu is installed. Or, if the space is there, to something like Ubuntu One or Dropbox.

Another option:  Create a new partition on your machine.  Copy the files to the new partition.  When you install Ubuntu, handle the partitioning yourself (the "Something Else..." option), select the partition with the files *but do not* tell the installer to format it. The partition will not be formatted and it and its content will be available to the new Ubuntu installation.

This is a variation of the widely used technique of carrying over a separate /home partition between releases or new distros.

---

### Post by Iowan on 2013-12-17
I've never created a separate /home partition - though I've always wanted to (lazy, I guess). T'would certainly make the process easy if such already existed...

---

### Post by mips on 2013-12-18
Which files do you wanna backup, data or configs?

You could always just use grsync to backup and restore stuff.

---

### Post by oldrocker99 on 2013-12-21
I have two HDs in my box; my first drive is a dual-boot Windows and Linux, and my second drive is my /home folder. When I install a new system, I select "Something Else" from the installer, format the Linux partition and mount the second drive (without checking the "Format" box!) as /home. It works beautifully for me. If you have a single drive, backup your entire /home folder, and make a ~128GB system partition, and use the rest of the space for making a separate /home partition. Then you'll never need to do a restore to /home again.

DO keep a backup, of course!

---

