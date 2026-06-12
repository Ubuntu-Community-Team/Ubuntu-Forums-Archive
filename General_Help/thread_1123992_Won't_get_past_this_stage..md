---
title: "Won't get past this stage."
date: 2009-04-12
forum: General Help
---

### Post by ShadeMK on 2009-04-12
Hi, I have recently been wanting to dual boot Ubuntu with Windows XP but I am having some problems.

I installed Ubuntu with Wubi, everything went fine, until this happened. I get stuck at one screen forever. It says this:

Loading, please wait...

BusyBox u1.10.2(ubuntu 1:1.10.2-1ubuntu6) built in-shell(ash)

Enter 'help' for a list of built-in commands.

(initramfs)

Thank you!

---

### Post by gabak on 2009-04-12
1- if u have partition NTFS and it has errors u got a lot a trouble.
2- get hirens cd and convert it to fat32 much stable (use partition magic)
3- resize partion and make EXT3 partition manually (over 10gb is fine or more) and SWAP partition of 2gb is fine nt more than that.
then install ubuntu manually and set it up to install on EXT3 , and it will do the trick.

---

### Post by ShadeMK on 2009-04-12
> **gabak said:**
> 1- if u have partition **NTFS** and it has errors u got a lot a trouble.
2- **get hirens cd and convert it to fat32 much stable (use partition magic)**
3- resize partion and make **EXT3** partition manually (over 10gb is fine or more) and **SWAP** partition of 2gb is fine nt more than that.
then install ubuntu manually and set it up to install on **EXT3** , and it will do the trick.

I bolded all the things I didn't understand. Sorry for being such a noob  :oops:.

---

### Post by ShadeMK on 2009-04-13
Can anyone else help me? I couldn't understand much of what Gabak was saying.

---

### Post by ShadeMK on 2009-04-14
Do you guys need more information? Please please please help me!

---

### Post by lisati on 2009-04-14
[NTFS]("http://en.wikipedia.org/wiki/Ntfs"), [FAT32]("http://en.wikipedia.org/wiki/Fat32#FAT32"), and [EXT3]("http://en.wikipedia.org/wiki/Ext3") are different ways of [formatting a disk]("http://en.wikipedia.org/wiki/Disk_format").

I think what gabak is trying to say is to have a look at the way your disks are organized, there might be errors there that need attention.

---

### Post by ShadeMK on 2009-04-15
I used Wubi to install Ubuntu, I didn't use a disk.

Oh lord, if anyone else reads this for some reason, please forgive my stupidity,

---

