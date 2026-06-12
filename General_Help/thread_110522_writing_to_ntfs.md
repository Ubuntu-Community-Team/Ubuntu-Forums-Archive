---
title: "writing to ntfs?"
date: 2005-12-31
forum: General Help
---

### Post by Kurt Dodrill on 2005-12-31
From what I heard, running Linux and writing to a NTFS drive will corrupt the filesystem. I have linux by itself running on a 37gb raptor and 4 other hardrives,all NTFS, for storing data. Since I download alot of stuff, Im looking for the easiest way to write to these other drives, if possible, avoid using xp to do so. through samba my brothers xp box can read my files over network, but will writing to reiserfs or ext3 from xp corrupt it too, even through samba?

---

### Post by three_sixteen on 2005-12-31
[QUOTE=Kurt Dodrill]From what I heard, running Linux and writing to a NTFS drive will corrupt the filesystem. I have linux by itself running on a 37gb raptor and 4 other hardrives,all NTFS, for storing data. Since I download alot of stuff, Im looking for the easiest way to write to these other drives, if possible, avoid using xp to do so. through samba my brothers xp box can read my files over network, but will writing to reiserfs or ext3 from xp corrupt it too, even through samba?[/QUOTE]

I run linux on an NTFS drive with a linux partition on it.

See this thread.

[http://www.ubuntuforums.org/showthread.php?t=107401](http://www.ubuntuforums.org/showthread.php?t=107401)

---

### Post by Kurt Dodrill on 2005-12-31
[QUOTE=three_sixteen]I run linux on an NTFS drive with a linux partition on it.

See this thread.

[http://www.ubuntuforums.org/showthread.php?t=107401](http://www.ubuntuforums.org/showthread.php?t=107401)[/QUOTE]

wouldnt that involve reformatting with a windows disc? how do you make your drive ntfs then have a linux partition and not a ntfs partition and a ext3/reiser partition?

---

### Post by Kurt Dodrill on 2005-12-31
from what im seeing, writing to ntfs from linux is out of the question unless using risky programs. it looks like the only way i can do it is to copy the files using samba over the network to the xp box, then take out the drive from the linux computer and put it into the xp box to write to.

---

### Post by soulestream on 2005-12-31
> but will writing to reiserfs or ext3 from xp corrupt it too, even through samba?

samba does the writing so file system doesnt matter in that case. If not you would have to have all the machines on a network the same. 

It would be better to format a drive FAT32 for your shared data. 

People will tell you that you can use captive for linux to write to NTFS and there are aps that allow XP to write to ext2(3 maybe). But its always better to use native writing. 

soule

---

### Post by Kurt Dodrill on 2005-12-31
[QUOTE=soulestream] But its always better to use native writing. 

soule[/QUOTE]
 
yeah id definitly rather use native writing, i dont want to try anything that "kinda" works or could destroy the data.

---

### Post by spade_shark on 2005-12-31
Lets clarify several things.  First writing to NTFS local mounted partions from linux is ... not the best choice.  If I understand the setup correctly, your brothers system will not harm your ext3 through samba shares.  Do not misunderstand what the NTFS / ext3 issues are.  Once your files leave your system, (file sharing, ftp, webdav, whatever) it is the other systems responsiblity to handle the writes.  Look at it like a translator, once your file read/write leaves your system the destination handles all its own read/writes.
>  but will writing to reiserfs or ext3 from xp corrupt it too, even through samba? No, this is fine.  Millions of users do this all day ;)

Linux EXT3 , XFS --->Network--> XP (NTFS) system = no issues.   

XP (NTFS) system --->Network--> Linux EXT3 , XFS = no issues.

Do not use: Linux /mnt/localdrive/ntfs_partion for writing (goes for removable local drives as well).  This is where the mess begins.

Maybe you should mount the NTFS drives in your brothers sytem and one by one clear the data off a drive.  Mount the now empty drive under your linux box as (XFS for large file support dvd maybe?) and move all data from your XP machine to your linux machine...drive by drive.  After a little work all drives will be mounted / partioned (xfs, etx3 ) and running under your linux box.  Happy downloading.

---

