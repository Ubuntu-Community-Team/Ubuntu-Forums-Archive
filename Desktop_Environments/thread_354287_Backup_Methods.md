---
title: "Backup Methods"
date: 2007-02-05
forum: Desktop Environments
---

### Post by impaler on 2007-02-05
Heya all, I trying to get my head around a good backup statergy. My current OS system is.

Grub
Windows xp x64
Ubuntu Dapper

Both operating systems are on different partitions with their applications installed alongside their operating system. I also have a 150 gig partition as 'media' storage using fuse with ubuntu I am able to read write NTFS. I want to backup my Operating system partitions onto DVDs it should be around 30 gigs of data whilst they are in a current virus free and working order. Is there a linux software that will keep my grub, ubuntu and windows install intact for dvd backup? I would incrimentally backup my media drive separately.
 
For windows I used a program [Cobian Backup]("http://www.educ.umu.se/~cobian/cobianbackup.htm") which automated incriemental backups to any destination I needed which was insanely flexible.

Would anyone else share their approach of backups? :)

---

### Post by lhtown on 2007-02-05
I would imagine that what you are asking could be done. I don't know about doing it automatically. However, I would guess that most Ubuntu desktop users don't bother backing up the operating system since it is so easy to install and generally very reliable if you don't do goofy stuff.

If you are concerned about getting back up quickly after a hard drive failure, you might consider dual disks with RAID like servers use.

---

### Post by impaler on 2007-02-06
Thanks lhtown I am aware that in the case of ubuntu being easy to install but after investing large amounts of time into getting ubuntu and windows working the way I want there is always the chance of something stuffin it up, most likely me messin with things :) The other fact that I still rely on windows apps means that I need something to back up everything. Mirroring a hard drive is very cool but isnt realy a backup in my opinion the data on both hard drives are still dynamic a static backup on some dvds would be better :)

Does anyone use something like norton ghost to backup and if so will it back up multipile partitions and keep the grub loader and the master boot record intact? I know ghost would work with a windows backup but having two diffferent file systems and OS might cause incompatibility issues?

---

### Post by samurailink3 on 2007-08-27
I wouldn't suggest using Norton Ghost to backup your Ubuntu partition. It says here [https://help.ubuntu.com/community/BackupYourSystem/TAR]("https://help.ubuntu.com/community/BackupYourSystem/TAR") that Ghost sees the Ext3 partition as a damaged Ext2 partition and this causes a lot of trouble. Don't do that ;)

If it were my set up, I would probably just clone the drive over to another cheap, small drive and keep that in a safe place. I've done this before with a pc that the main hard drive was starting to go, I used the ultimate boot cd. [http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/") Its free of cost and has worked well for me in the past. About programs that can do that... I'm not aware of any, but I'm kinda new to back up methods :)

Hope that helps a little bit!

---

