---
title: "Undelete files on FAT32"
date: 2006-05-05
forum: Desktop Environments
---

### Post by technoboy on 2006-05-05
Oops, I accidentally deleted a file on a FAT32 partition sitting on an external hard drive. Is there anyway to recover it?

---

### Post by Qrk on 2006-05-05
In the top level directory of the partition, there should be a hidden folder named .Trash-username. You should be able to find what you deleted in there. 

If you deleted it from your trash, though, it'll be hard.

---

### Post by technoboy on 2006-05-05
Nup, I used the 'rm' command, so it ain't there. Does anyone know how to use dosfstools?

---

### Post by edoardo on 2006-08-09
boot from windows (*) and run this freeware
[http://www.adrc.net/data_recovery_software/](http://www.adrc.net/data_recovery_software/)

it's hard to find non-commercial undelete sw. this did the job for me. excellent stuff!

(*)assuming your data is more valuable than OS-religious beliefs of course
seriously, forensic has to use best-of-breed tools ..
Edit/Delete Message

---

