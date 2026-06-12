---
title: "Full backup"
date: 2011-01-29
forum: Desktop Environments
---

### Post by zander x on 2011-01-29
Hello. Not really sure if this is the right place, but here goes...

I have a dual boot system and I screwed up Windows very nicely, but I still need it every now and then. Before I run the restore wizard (which I bet is going to erase EVERYTHING), I need to know how to make a complete backup of my Ubuntu installation so that I can restore it when I re-install Ubuntu after Windows gets reinstalled.

---

### Post by Jahid65 on 2011-01-29
[Redo Backup]("http://redobackup.org/") or clonezilla.

In case of re-installation of windows, your ubuntu will remain safe. you just have to restore the grub. [How to restore grub2]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by bluff on 2011-01-29
It depends,

Are you restoring your Windows enviroment by a manufactorers restore cd/dvd/partition or from a original Windows cd/dvd?

If it's the latter then you cna just reinstall Windows from the cd/dvd and the from a ubuntu live cd re-install grub.

If you are doing a manufactorers restore then you will have to backup your system.

to do this (you can do this a few different ways):

1. backup system following this howto [https://help.ubuntu.com/community/BackupYourSystem/TAR]("https://help.ubuntu.com/community/BackupYourSystem/TAR") or [https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")
2. copy the backup file onto a cd/dvd.
3. restore your windows system.
4. reinstall ubuntu.
5. restore your unbuntu system according to the howto

---

### Post by zander x on 2011-01-29
> **bluff said:**
> It depends,

Are you restoring your Windows enviroment by a manufactorers restore cd/dvd/partition or from a original Windows cd/dvd?

If it's the latter then you cna just reinstall Windows from the cd/dvd and the from a ubuntu live cd re-install grub.

If you are doing a manufactorers restore then you will have to backup your system.

to do this (you can do this a few different ways):

1. backup system following this howto [https://help.ubuntu.com/community/BackupYourSystem/TAR]("https://help.ubuntu.com/community/BackupYourSystem/TAR") or [https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")
2. copy the backup file onto a cd/dvd.
3. restore your windows system.
4. reinstall ubuntu.
5. restore your unbuntu system according to the howto

I love this place. Support is quick and concise.

I am having to run the manufacturer's restore, so I will use the 5 steps. But there's a problem... I can't find where the backup file(s) are and the ones I could locate weren't put where I specified, not I'm not feeling too confident about doing it now. Forgot to mention that I am using Simple Backup.

---

