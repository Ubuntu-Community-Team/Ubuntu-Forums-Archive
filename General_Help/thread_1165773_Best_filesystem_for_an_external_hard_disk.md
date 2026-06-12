---
title: "Best filesystem for an external hard disk?"
date: 2009-05-21
forum: General Help
---

### Post by monsterstack on 2009-05-21
I'm not bothered with compatibility for Windows. I just want the best choice of filesystem for safety and speed. I can't really find much difference between them all, though, really. I'm probably going to go for ext3 unless somebody advises otherwise.

Anyone care to make some recommendations? Much appreciated. :)

---

### Post by solwic on 2009-05-21
> **monsterstack said:**
> I'm not bothered with compatibility for Windows. I just want the best choice of filesystem for safety and speed. I can't really find much difference between them all, though, really. I'm probably going to go for ext3 unless somebody advises otherwise.

Anyone care to make some recommendations? Much appreciated. :)

ext4 is supposedly faster than ext3, especially with larger files.  It's pretty new, though, so there may be some bugs.  

I use ext4 on my 500GB SATA, and have had no issues so far.  It's fast and stable.  

Just my opinion, though.

---

### Post by vernonrj on 2009-05-21
IMO, you should have at least a small ntfs partition on the drive. You never know when you'll need to interface with a Windows machine.

---

### Post by Wiebelhaus on 2009-05-21
> **iRun said:**
> ext4 is supposedly faster than ext3, especially with larger files.  It's pretty new, though, so there may be some bugs.  

I use ext4 on my 500GB SATA, and have had no issues so far.  It's fast and stable.  

Just my opinion, though.

Is it backwards compatible? If your using an ext3 system and format your external with ext4 will they cooperate without issues?

---

### Post by Ericyzfr1 on 2009-05-21
I use a couple of USB drives that I converted to ext4, no major issues. I found one little issue on one of my drive though, it is separated in 3 partitions, when I tried to create a folder....the next time I connected the drive the folder was gone, I fixed it by copying a larger file and since it worked fine. I have no real explanation for what happened.

---

### Post by logos34 on 2009-05-21
> **vernonrj said:**
> IMO, you should have at least a small ntfs partition on the drive. You never know when you'll need to interface with a Windows machine.

That hasn't been an issue for a long time.  

[fs-driver]("http://www.fs-driver.org/faq.html") allows windows to read and write to ext2/3. (no ext4 support yet, though).

Personally, I'm waiting for the bugs to be ironed out of ext4, then I'll probably switch because it sounds like they've made some big performance leaps over ext2/3

---

### Post by vernonrj on 2009-05-21
It's true that you can install a third-party add-on for Windows... it still has to be installed though. If you're going for non-windows, I'd still go for compatibility, so it would be ext3 for me.

---

### Post by monsterstack on 2009-05-21
> **vernonrj said:**
> IMO, you should have at least a small ntfs partition on the drive. You never know when you'll need to interface with a Windows machine.

Nope, not a chance. I have been 100% Microsoft-free for over a year. No Wine, no dual-booting, no nothing. I have nothing with which I wish to share with a Windows PC.

> **iRun said:**
> ext4 is supposedly faster than ext3, especially with larger files.  It's pretty new, though, so there may be some bugs.  

I use ext4 on my 500GB SATA, and have had no issues so far.  It's fast and stable.  

Just my opinion, though.

That sounds all right. Ext4 is supposed to be pretty hot all round. I haven't managed to find anything about its use on external devices, though. I might give it a go and see how it works.

---

### Post by logos34 on 2009-05-21
> **vernonrj said:**
> It's true that you can install a third-party add-on for Windows... it still has to be installed though. If you're going for non-windows, I'd still go for compatibility, so it would be ext3 for me.

Ubuntu comes out-of-box with read+write support for NTFS (-->ntfs-3g driver)

So I don't understand the need for ntfs or fat32

---

### Post by evermooingcow on 2009-05-21
> **monsterstack said:**
> Nope, not a chance. I have been 100% Microsoft-free for over a year. No Wine, no dual-booting, no nothing. I have nothing with which I wish to share with a Windows PC.
Yes. No need to taint your disks.

I've been using ext4 for about two weeks so far on the root and home partition. No issues here so far.

---

### Post by egalvan on 2009-05-21
> **logos34 said:**
> That hasn't been an issue for a long time.  

[fs-driver]("http://www.fs-driver.org/faq.html") allows windows to read and write to ext2/3. (no ext4 support yet, though).


fs-driver still has issues with large inodes....
which everything from Hardy 8.04.2 on up seem to use...
(ok, so it's the partitioner used...
still, you need to watch out.)

direct quote from their website...

[I] Large inodes
The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup. [/I]

---

### Post by logos34 on 2009-05-21
come to think of it, I did run into the inode issue once last year with XP and Mandriva

---

