---
title: "GRUB error 17"
date: 2006-08-02
forum: Desktop Environments
---

### Post by ladiesrockmysox on 2006-08-02
i have created a new partition on my HD for ubuntu. now, i cant even get the choice to choose between ubuntu and windows. whenever i boot, i get GRUB ERROR 17. thats it. any help would be greatly appreciated.

---

### Post by coffeecat on 2006-08-02
From the [Grub manual]("http://www.gnu.org/software/grub/manual/").

> 17 : Cannot mount selected partition

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 
What filesystem did you choose for your new partition? Which partitioning software did you use? What exactly did you do?

---

### Post by ladiesrockmysox on 2006-08-02
type is NTFS i believe, software, the software the Ubuntu CD provided for me. other than that, default installation

---

### Post by coffeecat on 2006-08-02
You installed Ubuntu to a NTFS partition??!! :shock: I'm not following you. You used the partitioning software on the Ubuntu CD - that's Gparted. It will create NTFS partitions, but I'd be amazed if the CD will let you install Ubuntu to one. Before we go any further I think you need to confirm whether this is so.

A word of explanation in case you don't know this. NTFS is the proprietary Microsoft filesystem for Windows NT and Windows XP. Linux can read from NTFS reliably, but writing to NTFS in Linux is experimental and not to be recommended.

---

### Post by ladiesrockmysox on 2006-08-02
i dunno...im just trying to convert to linux, and im not having a good time doing it. perseverence is what i need. the file system was ext or something of the sort. i am also talking to one of my friends who is a linux junkie. he told me to install LILO or something like that. he gave me directions, ill see how that works

---

### Post by coffeecat on 2006-08-02
Ext was probably ext3, and that's fine. It's the filesystem the Ubuntu installer would choose if left to itself. Anyway, best of luck with Lilo. Post back if that doesn't work because Grub is usually very reliable and there must be a reason for the error.

Enjoy Linux, and in particular enjoy Ubuntu. And welcome to the forum. :)

---

### Post by ladiesrockmysox on 2006-08-02
thanks alot

---

