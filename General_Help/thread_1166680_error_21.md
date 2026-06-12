---
title: "error 21"
date: 2009-05-22
forum: General Help
---

### Post by rabble88 on 2009-05-22
I have a dual boot system with windows xp on my internal hd and ubuntu 8.02 on my external hd.  i recently moved and in doing so lost the power cord for my external.  when i tried to boot without the external plugged in, and i get the error 21 message.

i can't find my external cord anywhere, so that's not an option.  i can plug the external in internally, but ultimately i'd just like to get into windows.  if anybody knows how that'd be great.  thanks in advance.

---

### Post by Crafty Kisses on 2009-05-22
The issue is that GRUB is installed on your internal drive rather than your external drive. So what you want to do is find your Windows CD if you still have one, then run the following in Windows:
```
fixmbr
```
Now if you don't have your Windows CD, you might be able to fix this issue with [SuperGRUB]("http://supergrubdisk.org"). It's pretty straight forward. Once you have fixed the GRUB error, try to install again but make sure you install GRUB to the proper device. In my case my external HD is usually **/dev/sdf1**. So make sure, to confirm this you might want to run:
```
sudo fdisk -l
```
My external drive from that command is the following:
```
Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       30402   244196352    7  HPFS/NTFS
```
Try that and see if that doesn't get you up and running.

---

### Post by rabble88 on 2009-05-22
thanks loads for the tips, but i found the cord(after hours of searching) and connected my now broken external case which amazingly worked.

however, I would like to know if you can tell me how to fix this problem so that I don't have to have the external plugged in to run windows, just ubuntu, i'd be happy to exchange my first born.

---

