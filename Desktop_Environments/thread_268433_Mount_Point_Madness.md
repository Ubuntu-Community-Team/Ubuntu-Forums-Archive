---
title: "Mount Point Madness"
date: 2006-09-30
forum: Desktop Environments
---

### Post by o_O on 2006-09-30
OK, this is soooo weird I don't even know where to start...

When I booted my XP / Ubuntu dual boot machine today, I found one of my partitions (a FAT32 partition I use for sharing data between both OS's), usually called "Files" and mounted in /media/Files appeared under the name "org/eclipse". 
Now, what confuses me is that "org/eclipse" is nowhere to be found in /etc/fstab or /etc/mtab, neither is it a valid mount point in /media. I have not touched anything related to partitions or mount points. 

Unmounting/mounting works, and it seems to mount the partition in /media/Files, but under that strange name...

AFAIK, the only Eclipse on this box is the Java IDE, and I really doubt that's the problem... So, any ideas? I think I might just try to re-label the partition somehow, but if anyone has any suggestions, post 'em.

---

### Post by aysiu on 2006-09-30
Is that partition in your /etc/fstab at all? If not, maybe you should put it there and specify to mount it at /media/Files?

---

### Post by o_O on 2006-09-30
/media/Files was and still is in the fstab. 

Relabelling did not work, but issuing "sudo etc/init.d/dbus restart" on the terminal did. If when I reboot it ceases to work I'll add the command to my startup programs and hope it definitely solves my problem.

According to my research in these forums, it's a bug in HAL/DBUS... Strange, since I've been using Ubuntu for about a year and I had never experienced it.

Thanks anyway, aysiu. I'll post back after the reboot. ;)

---

