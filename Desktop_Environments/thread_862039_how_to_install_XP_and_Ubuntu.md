---
title: "how to install XP and Ubuntu"
date: 2008-07-17
forum: Desktop Environments
---

### Post by ashpachi on 2008-07-17
Hi all,

There is already ubuntu in my work station at office but it is not accepting me to install Windows XP Prof. It cant recognize the hard disk. Did anyone came across this sort of problem. Your help will be much appreciated. 

Regards,
Ash.

---

### Post by pmlxuser on 2008-07-17
usually the best way is to install windows first and then Ubuntu. however windows does not recognise the format that linux uses. The best way is to creat an NFS /FAT 32 partition while in ubuntu (u can use gparted) and then windows will recognize the partition and you can install windows then.

---

### Post by bigken on 2008-07-17
you will also have to repair your grub do some searching on the forum 1st before you do anything


you may also want to look at wine which runs windows applications in linux
and also vmware which allows you to run windows inside linux

---

### Post by stitchmysmile93 on 2008-07-17
You can install Virtualbox in ubuntu and then install winxp with Virtbox that's what I do... 

If you do this I have some advice don't use the install you can get from ubuntu get the .deb from Virtualbox's site.

Once you have it install run xp get updates etc then install guest additions. If you need any help just ask I recently installed it and it works great for me....

---

### Post by logos34 on 2008-07-17
Like pmlxuser said, windows doesn't recognize linux fs types, so you'll have to clear a space on the disk first using another partitioner...But if you have to shrink ubuntu / to do so you'll have to use Gparted from the ubuntu live cd (root ccannot be mounted when being resized).  Either format the space ntfs or vfat, or just leave it unallocated and let windows format it.  That's if you decide to put windows on a separate partition rather than run it as a guest OS in a virtual machine (which is probably the way I'd go if I had a choice).

---

### Post by stitchmysmile93 on 2008-07-17
Alright let me ask you a few questions what are your plans for xp ? Business or gaming or what ?

---

