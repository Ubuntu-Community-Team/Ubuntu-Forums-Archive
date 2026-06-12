---
title: "Vista / Ubuntu Dual boot - reinstall of Vista"
date: 2009-05-30
forum: General Help
---

### Post by DAHstra on 2009-05-30
I'm VERY new to Ubuntu and still trying to learn how to have Ubuntu do all that I love in Windows.  Until then, I need to use my Windows Vista, which is seriously malfunctioning since Service Pack 1.  I can't browse to update sites, my wireless connection kills after extended use.  Service Pack 2 killed IE alltogether as far as browsing.  Mozilla is fine.  Ubunutu doesn't kill after extended Net use and I don't have blocked sites.  It sounds like malware but after running Spybot and AVG and Adaware and others I can't see any problems.  

I want to restore my Vista, however I'm afraid of losing my Ubuntu booter.  What Can I do to restore or safeguard my Ubuntu partition and booter so I don't lose that too?  I've never run a Windows restore so I don't know what to expect.  Will it kill my dual booter and restore the standard Windows one?

I didn't "share" the drive when I installed Ubuntu.  I made 3 partitions.  1 for Windows, 1 for Swap and 1 for standard Ubuntu 9x.

Any help or suggestions greatly appreciated for this newbie.  :-)

---

### Post by tommcd on 2009-05-30
If you reinstall Vista it will overwrite your master boot record (MBR) and you will not get the grub boot loader on botup. Grub can be easily reinstalled from the Ubuntu live CD:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

