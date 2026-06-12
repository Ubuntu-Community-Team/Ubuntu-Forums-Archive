---
title: "Can I revert to Ubuntu 7.1 from my cd?"
date: 2009-02-18
forum: General Help
---

### Post by JimBuntu on 2009-02-18
I currently have upgraded to Ubuntu 8.1 from 7.1 and have all kinds of problems. 7.1 ran perfectly. Can I just stick my disk back in and install 7.1? Also, I want to do this on a dual boot laptop. If I do this will it just install on the Ubuntu partition. Or will it erase my xp partition?

---

### Post by exploder on 2009-02-18
You should be able to just reinstall 7.10 over 8.10. You will have to edit /grub/menu1st and remove the 8.10 lines. Back up your data first, just in case.

---

### Post by geirha on 2009-02-18
The support for 7.10 ends in april 2009, so I wouldn't recommend installing it. Try explaining the problems you are having.

---

### Post by JimBuntu on 2009-02-18
I am in another thread...

---

### Post by Hobgoblin on 2009-02-18
> **JimBuntu said:**
> I currently have upgraded to Ubuntu 8.1 from 7.1 and have all kinds of problems. 7.1 ran perfectly. Can I just stick my disk back in and install 7.1? 

You could do a fresh install of 7.1, losing any settings, extra software etc.  But your problems most likely stem from upgrading.  If you are going to do a fresh install then you should try 8.10 first.

---

### Post by JimBuntu on 2009-02-18
ok that sounds good. Will this erase my windows partition? or, Will it just install on the Ubuntu partition and leave everything else alone?

---

### Post by JimBuntu on 2009-02-18
Ok guys I want to reinstall the 8.10 but need to know if I can just put the disk in and go. I have a dual boot setup and dont want to erase my windows partition.

---

### Post by geirha on 2009-02-19
It won't install anything automatically, it will ask you what it should do first, and when you are on the partitioning part, you'll want to make sure it installs to the correct place. You might have to choose the manual partitioning option for that.

---

### Post by Mercury_Alpha on 2009-02-19
During the install, a partition manager will pop up giving you a graphical representation of your hard drive partitions. Everything tagged as "NTFS" is Windows. If I remember correctly, each partition will be partially shaded in. That represents the amount of data on each partition, in case you want to resize anything.

All you should need to do is delete all the ext3 partitions. You may want to take this opportunity to make a partition for Ubuntu's /home directory. That way, you can reinstall Ubuntu later without affecting any of your data.

---

### Post by linux_tech on 2009-02-19
Backupup your home directory to a flash drive then run the live cd to install. When partitioning delete existing ext partitions and create new ones

---

