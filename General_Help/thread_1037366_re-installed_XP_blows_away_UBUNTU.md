---
title: "re-installed XP blows away UBUNTU"
date: 2009-01-11
forum: General Help
---

### Post by hayre on 2009-01-11
Yo:

TWO QUESTIONS:

QUESTION 1: 
Downloaded Ubuntu several months ago – ignorantly put in on a NTFS 
Partition (yes – it is not only possible to do, but UBUNTU worked fine
There until now).

Recently had to re-install Windows XP (what a surprise!).  Did it.  Now lost 
UBUNTU and since it is on an NTFS partition GRUB 
(which I didn’t even know existed until now)
Will not let me put that partition as bootable.  

Also, I have reason to believe that possibly the “menu.lst” file  in that UBUNTU has gotten messed up.  (The details for why I think menu.lst may be messed up 
would take quite a while to explain.)

Is there a way (maybe by using windows boot.ini ??)  to load the NTFS UBUNTU 
at least once so I could get the files I need from that UBUNTU?

QUESTION 2:
I downloaded the lastest UBUNTU and installed it on a UNIX style partition.  I 
Thought that maybe I could get to the NTFS UBUNTU files from  the new UBUNTU.
However, both the install and gparted do not see the other disk (where XP is on one partition
And UBUNTU NTFS is on another).  The old UBUNTU could see all the partitions
On both drives.  Is there a way to get the new UBUNTU to see both drives like the old
One did?  If there is maybe I could get the files I need from the old NTFS UBUNTU…

Thanx in advance.
Johnny

---

### Post by _sleeper on 2009-01-11
when you say lost, do you mean that your box boots directly to winxp?

if that's the case, the problem is not the format of the hard drive -in this case ntfs-, but the fact that you reinstalled windows. apparently winxp, whipped out grub, so you need to reinstall it.

---

### Post by chex_m8 on 2009-01-11
I believe you can use the ubuntu live cd to mount the ubuntu patition and retrieve what ever files you need to get.

---

