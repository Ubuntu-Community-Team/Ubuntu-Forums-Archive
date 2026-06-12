---
title: "Ubuntu 7.10 system failure"
date: 2008-03-16
forum: Desktop Environments
---

### Post by Oblanda on 2008-03-16
I was using dual boot for months and everything worked in perfect harmony. 
On a 160GB Hitachi HDD there is one NTFS 20GB partition for WinXP, one FAT32 100GB for data and the rest is ext2 for Ubuntu 7.10.
The system was almost always on, with Ubuntu loaded most of the time.
One day, after a day being shut down, both systems failed to load. WinXP got stuck in an endless loading process, while Ubuntu showed a few different load problems. First it didn't want to start loading at all, next time it loaded the login window but failed to log in.  After that (and ever till this day) when it starts loading, at about 5-6% of progress bar it comes all black with this message:
> BusyBox v1.1.3 (debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) (blinking cursor)

XP worked OK after restart, except some long loadings which I believe is due to NOD32 AV.
Hard Disk works perfectly normal, too. I tried some programs that allow seeing ext2 partitions from XP and the data seems fine.

Is there anything I can do except reinstalling the system (which I do not prefer right now)

---

### Post by GTvulse on 2008-03-16
Hmm... That's bad news. It means that a great part of your filesystem got hosed and you lost critical system files. Your best bet is to rescue your data files from the Windows partion using [ext2fsd]("http://www.fs-driver.com/") and then reinstall the system. Do make sure to use ext3 or another journaling filesystem the next time.

---

### Post by Oblanda on 2008-03-16
So I DO have to reinstall the system? That really is bad news. 
OK, thanks for help

P.S. I was actually using ext3. I mentioned ext2 only because that program was originally for ext2 but able to read ext3, too or something (Ext2 IFS). 
What is the difference between the ext2/3 anyways?

---

### Post by GTvulse on 2008-03-16
The difference between ext2 and ext3 is that the latter does journaling. Loosely speaking, the data is written to disk twice, once to a special file called the journal bypassing disk and system caches. Then it is written to disk at the operating system and hardware leisure. In case of a hard crash, the file checking is faster, usually much faster, than in a classic non-journaling filesystem (say, ext2, FAT(nn), NTFS) because there is a second copy of the data to check the actual data on disk.

I've seen the symptoms you described in the past and they point out to hardware failure. You may have a failing disk controller (fixable by adding an expansion card to your mainboard and attaching the disk there) or a 
badly seated interface/power cable (fixable by reseating the cable connectors, while being well grounded. Don't attempt on a carpeted floor without an anti-static strap on your wrist!). The probability that this happens to a PATA disk is higher that one might suspect.

---

### Post by Oblanda on 2008-03-16
It seemed like a hardware failure to me, too, but I'm not sure what could possibly go wrong. 
Recently I had had to replace the WDC 160GB HDD with a new one (because of a mysterious end of it's life I would say). It was still under the warranty and they gave me Hitachi of the same characteristics for lacking the WD. 

Now, since there is a possibility of some hardware failure with the new HDD, should I start to suspect there is something wrong with some other part of the system and my HDDs will just keep dying? Blame motherboard? Or maybe poor power supply? 

Sorry but your last post was somewhat confusing to me (maybe it's my bad English).
I should check my HDD connection and avoid touching carpet without some anti static something round my wrist? Why is this the first time I'm hearing that warning? I've installed this HDD myself, on a carpeted floor, without any anti static gadgets around.. I was wearing shoes as I can recall... 
Should I contact the service for this?
I know this might be off topic but since you've already mentioned...and I have got no other place to ask..

---

### Post by GTvulse on 2008-03-17
It is that one can never be too careful with static electricity, but putting a hand on your power supply if it is grounded in the connection outlet is more than enough.

Hmm.... You may want to check your power supply as well. On your first HD, II think you were lucky that it died so soon. When Seagate, WD and Maxtor became one company, the quality of their products dropped sharply. In ymy experience Samsung, Toshiba and Hitachi are the brands to buy today (this may change, many Hitachi drives made in the early 00's were duds).

---

