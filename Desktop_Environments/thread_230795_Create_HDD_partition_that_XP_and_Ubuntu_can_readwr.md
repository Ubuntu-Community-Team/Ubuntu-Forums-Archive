---
title: "Create HDD partition that XP and Ubuntu can read/write to?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by RichardSchollar on 2006-08-06
Hi Everyone

Very new to linux, very ignorant of everything.  Do have plenty of hard disk space, and due to networking difficulties (subject of a thread in the Networking forum) can't connect to internet/email while in Ubuntu.  No floppy drive, either.

Hence,  I would love it if I was able to create a hdd partition that both Ubuntu and XP could read and write text files to (basically so that I can save the results of commands in the shell to paste to this forum in the aforesaid networking thread).

Is this possible? How would I go about it if so? Should I create it in XP or in Ubuntu? No idea how to actually create a partition in Ubuntu by the way.

Thanks for any and all replies 

Richard

---

### Post by tcollogne on 2006-08-06
Hi,

First, writing from linux to a ntfs partition is experimental and not recommended for important data.
I have also win xp en (k)ubuntu, but I did the other way around. I created a ext3(linux) partition and made that accessible from windows. 
To do this I used a ext3 driver for windows. With this driver you can access linux partitions. I find it to work perfect. 

The ext3 driver for windows can be found here [http://www.fs-driver.org/](http://www.fs-driver.org/)

If you need any more help, just let me now.

Greetz

---

### Post by RichardSchollar on 2006-08-06
That's amazing - thank you very much for that suggestion!  It works a treat!  That will make my life much easier :)

Richard

---

### Post by Scythe!? on 2006-08-06
You could make a FAT32 Partition too.

---

### Post by tcollogne on 2006-08-06
No problem. Glad I could help.

The problem with fat32 is that (at least I thought so) the filesystem can not handle files over 4 gb.

---

