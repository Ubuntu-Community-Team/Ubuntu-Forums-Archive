---
title: "I lost my NTFS partition somehow... need help plz"
date: 2006-09-11
forum: Desktop Environments
---

### Post by RoamenCota on 2006-09-11
My layout is an IBM X30 lappy, with 768mb ram, 1.2ghz proc, and a 60gb seagate spinpoint.  I run my hd partition setup @primary - 10gb windows (soon to be smaller), 4.5gb ubuntu (reiserfs), 1.5 swap; @extended - 29gb ntfs, and 11gb ext3.  

Now when i first installed ubuntu, i could see my two ntfs partitions on my desktop (1.how do u remove the shortcuts from the desktop?).  But i recently came upon the program ntfs-3g which is supposed to allow linux to write to ntfs partitions.  so, i went and installed it but i couldnt get it to work. the problem was that it was supposed to be installed after ntfs-3g was installed and therefore it would be able to write (i did not do this because i had data on the partitions).  so a few weeks after i install 3g, i boot up my lappy and bam, wtf happened to my partitions?  i think they are just not mounted properly so i was wondering if anyone could (2.) diagnose this problem for me and (3.) help me fix it.  

Thanks all, I <3 ubuntu cuz its sooooooo sexy and much better than windows.  i just have yet to get as good with it as i am with windows.  when i do though, rest assure, bye bye microshit. =D

---

### Post by monktbd on 2006-09-11
1.) you can set that in gconf-editor (call it with the terminal) somewhere in the settings for nautilus, desktop. 
2.) what do 
> sudo fdisk -l
and
> cat /etc/fstab

say?

---

