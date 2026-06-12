---
title: "Clamav can scan Windows for viruses from within Linux."
date: 2008-07-03
forum: Desktop Environments
---

### Post by rocketman768 on 2008-07-03
If you run linux, you can scan your windows partitions with clamav antivirus without having to boot into windows.

[http://linuxhelp.blogspot.com/2005/10/clamav-free-anti-virus-solution-for.html](http://linuxhelp.blogspot.com/2005/10/clamav-free-anti-virus-solution-for.html)

If you are scanning ntfs partitions, you might need the ntfs-3g module which gives you write access to those partitions.

---

### Post by pac-man on 2008-07-04
isn't the ntfs-3g natively supported and installed in 7.10 and 8.04 ?

---

### Post by coffeecat on 2008-07-04
I managed to do the complete opposite by mistake once on a multibooting computer with Windows XP and about 8 Linux installations. I'd already installed [Ext2 IFS for Windows]("http://www.fs-driver.org/") but forgotten about it. One day I set AVG scanning in Windows and went off to do something else. When I came back an hour or so later I found that it was methodically working its way through all the Ext3 Linux partitions looking for Windows viruses.

It didn't find any. :roll:

---

