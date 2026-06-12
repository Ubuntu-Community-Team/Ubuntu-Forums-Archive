---
title: "Evolution not restore a backup"
date: 2007-12-18
forum: Desktop Environments
---

### Post by gaiterin on 2007-12-18
Hi.
I did a backup of Evolution (Menu File/Backup Settings) in my laptop.

When I restore this file (Menu File/Restore Settings) in my desktop, it not works.

Nothing restore! Not emails, not contacts....

Thanks.
Marquinos.

---

### Post by fdimmling on 2007-12-18
AFAIK the backup ist just a tar archive. You can inspect it and see if you have really backed up things. In principle you should be able to restore mail etc - or at least most of it - manually if everything else fails.

Friedrich

---

### Post by gaiterin on 2007-12-19
Yes, the compressed file is correct.
How can I restore it manually?
Extracting all file in my home/.evolution ?
Regards.
Marquinos.

---

### Post by fdimmling on 2007-12-20
Since the backup file contains the directory .evolution you should extract it to your home directory. I would rename the old .evolution dir in case something goes wrong and kill all evolution processes before extracting the archive. Logging out and logging in again should start the necessary processes again. Anyway I do not understand why the restore process is not successfull when the archive is ok.

Good luck

Friedrich

---

### Post by gaiterin on 2008-02-10
Hi!
The solution is this: Restore FROM the home folder! The restore file MUST BE in the home folder.

The restore file in a other folder not works! :O

Regards.

---

### Post by tcommbee on 2008-02-10
now, THAT's a feature! :-D

---

### Post by alejandro.mc on 2008-03-14
Thanks So Much Gaiterin That Was A Nice Piece Of Advice I Was Going Crazy Trying All Sort Of Tricks.. Thx

---

