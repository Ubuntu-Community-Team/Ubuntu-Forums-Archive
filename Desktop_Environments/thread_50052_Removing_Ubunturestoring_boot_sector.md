---
title: "Removing Ubuntu/restoring boot sector"
date: 2005-07-18
forum: Desktop Environments
---

### Post by endtime on 2005-07-18
Let me first say that I'm not removing Ubuntu through any fault of Ubuntu itself - it's my favorite distro.  However, I've decided that I'd rather format the secondary hdd it's on and use it for backup.

My hda/C:  is a 160 GB Samsung (IDE 2 master) with XP Home SP2 on it, and my hdb (IDE 2 slave) is from a six-year-old Dell - 12.6 GB.  GRUB is installed on the boot sector of my hda/C: and I want to get rid of it and restore the normal Windows boot.  At the end of whatever process you recommend to me, I want to be able to format the Dell drive and I want my PC to boot Windows without asking...if that might involve leaving GRUB and simply removing the Ubuntu options that's ok, but I'd rather not have to worry about it.  Thanks in advance for any help.

---

### Post by codejunkie on 2005-07-18
**Backup Backup Backup** now that that's been said you can reinstall the default windows boot loader by putting in your windows xp cd. boot to the cd and choose recovery console and when you get to the command prompt type ```
fixmbr
``` that will reinstall the default windows boot loader. [SIZE=4]**It cannot be a restore cd set if you use a restore cd set it will erase all your data **[/SIZE] before you do this backup all your important data just in case something go's wrong because i don't want you blaming me if it does and you loose all your data hope this helps.

---

### Post by endtime on 2005-07-18
Thanks - is that the only way to do it?

---

### Post by sooqing on 2005-07-18
since u using DELL.. use ur resource disk to boot into WIN98's DOS mode and performP:

fdisk /mbr

---

### Post by codejunkie on 2005-07-18
[QUOTE=endtime]Thanks - is that the only way to do it?[/QUOTE]
if you are wanting to have windows only on your pc yes. if you still wan't a dual boot system and you just want grub to load windows by default and not ubuntu you can edit your /boot/grub/menu.lst file and set windows to be the default os for grub to load.

---

### Post by endtime on 2005-07-19
[QUOTE=sooqing]since u using DELL.. use ur resource disk to boot into WIN98's DOS mode and performP:

fdisk /mbr[/QUOTE]

I don't have a Dell, I just have a hard drive from an old Dell...I built my A64 3000+ system.

[QUOTE=codejunkie]if you are wanting to have windows only on your pc yes. if you still wan't a dual boot system and you just want grub to load windows by default and not ubuntu you can edit your /boot/grub/menu.lst file and set windows to be the default os for grub to load.[/QUOTE]

Thanks...I guess I'll have to dig up the CD, hopefully it's not at home (I'm back at school early to work).

---

### Post by codejunkie on 2005-07-19
[QUOTE=endtime]I don't have a Dell, I just have a hard drive from an old Dell...I built my A64 3000+ system.



Thanks...I guess I'll have to dig up the CD, hopefully it's not at home (I'm back at school early to work).[/QUOTE]
if you have a broadband connection at School i havent tested it but i was told that the ultimate boot cd @ [http://ultimatebootcd.com/](http://ultimatebootcd.com/) provide tools to do the same thing but i don't know for sure. if you can't find your windows cd it might be something to look at.

---

### Post by endtime on 2005-07-19
[QUOTE=codejunkie]if you have a broadband connection at School i havent tested it but i was told that the ultimate boot cd @ [http://ultimatebootcd.com/](http://ultimatebootcd.com/) provide tools to do the same thing but i don't know for sure. if you can't find your windows cd it might be something to look at.[/QUOTE]
 Cool, thanks.  I actually have a super-fast connection - I had to borrow an adapter when I got here this summer because the jack in the wall is a fiberoptic one.

**Edit:** Would [this](http://www.sysint.no/Nedlasting/MbrFix.htm) do what I'm looking for, painlessly?  Found it through ultimatebootcd.com.  It sounds like exactly what I need but I want a second opinion before I mess with my boot sector.

---

### Post by codejunkie on 2005-07-19
[QUOTE=endtime]Cool, thanks.  I actually have a super-fast connection - I had to borrow an adapter when I got here this summer because the jack in the wall is a fiberoptic one.

**Edit:** Would [this](http://www.sysint.no/Nedlasting/MbrFix.htm) do what I'm looking for, painlessly?  Found it through ultimatebootcd.com.  It sounds like exactly what I need but I want a second opinion before I mess with my boot sector.[/QUOTE]
from what i read yes it looks like it will do what you need but i cant guarantee how well it will work, so again backup before you try it because i don't want you to loose all your data.

---

### Post by endtime on 2005-07-19
[QUOTE=codejunkie]from what i read yes it looks like it will do what you need but i cant guarantee how well it will work, so again backup before you try it because i don't want you to loose all your data.[/QUOTE]
 Okay, thanks for all the help codejunkie.

---

### Post by debian_n00b on 2005-07-19
For anyone who is interested, here is how to backup MBR and restore.


Code:

dd if=/dev/hda of=/home/user/mbr_backup bs=512 count=1
(replace HDA with appropriate drive. HDA, B, C or D)

The BS option tells DD to copy 512 bytes at a time. The count tells DD to do this only once. Quick and dirty stuff. It results in only the fist sector, the MBR and partition table, getting coppied.

It's the first 446 bytes that is actually the MBR. The remaining 66 bytes is the partition table. So, if all you want is the MBR and not the table, replace 512 with 446. 

To restore, it would be the reverse of above command. You just substitute the input file(IF) with the output file(OF)

dd if=/home/user/mbr_backup of=/dev/hda bs=512 count=1



This is good to do anytime your MBR, or partition table, changes.

---

### Post by hypeiv on 2005-07-19
Yea also mbr's are not that hard to recreate... if you mess something up report back and we will tell you how to fix it... if you can't boot into windows you can use the windows cd to fix it... if you can't boot into linux you can use the ubuntu cd to fix it....

---

### Post by endtime on 2005-07-20
[QUOTE=hypeiv]Yea also mbr's are not that hard to recreate... if you mess something up report back and we will tell you how to fix it... if you can't boot into windows you can use the windows cd to fix it... if you can't boot into linux you can use the ubuntu cd to fix it....[/QUOTE]

Great thanks guys...I downloaded the MbrFix app.  I haven't touched my MBR yet, but I played with the driveinfo commands and stuff.  If I screw anything up I'll make sure you hear about it. :D

---

