---
title: "Recognizing partitions in Ubuntu after changing them"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Nicko68 on 2006-09-10
I'm pretty new to Linux (I dabbled a bit with Red Hat a few years ago, but that's about it).  I have a dual boot Windows XP/Ubuntu (Dapper Drake) system.  When I installed Ubuntu, my external hard drive was set up with 3 logical partitions, the first fat32, the second ntfs, and the third fat32.  I booted into Windows XP and using Partition Magic, I resized a couple of the partitions on my external hard drive and changed the types to fat32, fat32, ext3.  When going back into Ubuntu, it no longer was able to mount the 2nd and 3rd partitions, I'm assuming because their types changed.

I changed the partitions back to what they were to get around the problem for now.  Assuming I want to change the types again, how do I get Ubuntu to recognize the new partitions?  Can I do it in the UI or do I need to modify files directly?  Was there a better way to repartition othe rthan doing it with Partition Magic in XP?

Thanks in advance

Nick

---

### Post by mssever on 2006-09-10
When it comes to creating Linux partitions, you really should do it from within Linux, using fdisk, gparted, or equivalent.

Also, any time you change a partition's format, you need to change its entry in /etc/fstab. The type column needs to be updated (note that Linux calls FAT vfat and that all types are in lowercase), and the options column might need to be updated, as well--depending on the specific change.

---

### Post by Nicko68 on 2006-09-10
Thank you for your reply.

If I use gparted, will it automatically fix my /etc/fstab file, or is it just "safer" to manipulate ext3 partitions using it rather than PMagic?

---

### Post by mssever on 2006-09-10
It's just safer (and less problematic) to use GParted for editing ext3 partitions. As far as I know, you'll need to edit fstab by hand. But that doesn't necessarily mean that there isn't an automated tool. I've been using Linux ling enough that I'm perfectly comfortable with making thos changes by hand and I probably wouldn't know about (or use) another tool if it were available. Nothing against those hypothetical tools, just my personal style.

---

