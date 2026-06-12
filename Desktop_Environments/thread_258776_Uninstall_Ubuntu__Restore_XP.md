---
title: "Uninstall Ubuntu / Restore XP"
date: 2006-09-16
forum: Desktop Environments
---

### Post by Anthraxx on 2006-09-16
I've decided to get a separate computer for each OS. I want to fully remove Ubuntu from my XP machine and restore XP fully. I was also wondering: will this remedy the performance increase that XP suffered since installing Ubuntu?

---

### Post by BrokeBody on 2006-09-16
Nope. :)

---

### Post by Anthraxx on 2006-09-17
k, but how do I remove it?

---

### Post by mssever on 2006-09-17
Delete the Ubuntu partition. On the XP install CD, there should be some kind of option to fix the MBR. Then, you can use Partition Magic to resize the XP partition--or to create another one.

---

### Post by nu2this on 2006-09-17
When you got your PC did it come with restore disks? Or as in the case of my PC I had to dl'd 4 disks from the company(Gateway) after I registerd the PC.
If you got those disks then use those,they should take your PC back to what it was when you 1st got it. Also your PC w/ WXP will be fast again for a little while but it'll start to slow dowm again mine did.

---

### Post by pay on 2006-09-17
Boot up the XP cd and enter the recovery console. After putting in your password type ```
fixboot
fixmbr
```
and that should reinstall the XP boot manager

---

### Post by bigken on 2006-09-17
delete the linux partions boot from win xp cd go to repair console 
follow prompts then type 

fixmbr
fixboot 
exit 

reboot pc and your back into windows 

or run the fix 1st then delete and format the linux partions using windows

---

### Post by RealGomer on 2006-09-30
Quick question. Will using the Recovery console - fixboot / fix mbr mess up any of the files on the WinXP2 partition?:confused: 
I put Ubuntu on my laptop but I can't get the wireless to work. I'm going to put it on my test system instead.
Thanks!

---

### Post by wpshooter on 2006-09-30
> **Anthraxx said:**
> I've decided to get a separate computer for each OS. 

Good idea.

---

### Post by bigken on 2006-09-30
> **RealGomer said:**
> Quick question. Will using the Recovery console - fixboot / fix mbr mess up any of the files on the WinXP2 partition?:confused: 
I put Ubuntu on my laptop but I can't get the wireless to work. I'm going to put it on my test system instead.
Thanks!


no it wont run fixmbr 1st then fixboot ;)

---

### Post by jchau on 2006-09-30
> **Anthraxx said:**
> I was also wondering: will this remedy the performance increase that XP suffered since installing Ubuntu?

Why would you want to fix an increase in performance? Wouldn't you want your computer to perform better?

---

### Post by DragonAura on 2006-09-30
I have a similar problem...

I have Ubuntu and Windows XP on one system. Ubuntu doesn't connect to the internet for me so I want to remove it WITHOUT reinstalling XP.

Is there a way to do this? :-k

---

### Post by bigken on 2006-09-30
> **DragonAura said:**
> I have a similar problem...

I have Ubuntu and Windows XP on one system. Ubuntu doesn't connect to the internet for me so I want to remove it WITHOUT reinstalling XP.

Is there a way to do this? :-k

yes run the fixmbr and fixboot from recovery console and in window 
just format the drives ;)

---

### Post by DragonAura on 2006-10-01
> **bigken said:**
> yes run the fixmbr and fixboot from recovery console and in window 
just format the drives ;)

Thanks!! :D

---

### Post by Zelut on 2006-10-23
Here's a situation.  I will be installing Ubuntu (dual-boot) on a machine and in the long-term will need to revert it to the XP partition.  I'm assuming I can simply use gparted or any other NTFS enabled partitioner to wipe & restore the full XP partition.

Is the XP CD required to fix the MBR & if so (I'm assuming it is) does it have to be the original CD or just any XP CD?

---

### Post by pony-tail on 2006-10-24
Some "system restore " disks do not have the console but all XP disks do - so any XP disk that will take your Windoze Key will do - If it will not take your key , you will not be able to enter the console If you have a seagate disk they have a utility called disk wizzard that can repair your MBR and replace it with factory code - Other brands may have similar - I do not personally use XP ( although I own 2 liscences ) but I do use Win2k and The method os the same

---

