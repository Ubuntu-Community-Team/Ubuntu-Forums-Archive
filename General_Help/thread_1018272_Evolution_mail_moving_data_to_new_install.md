---
title: "Evolution mail: moving data to new install"
date: 2008-12-21
forum: General Help
---

### Post by 73ckn797 on 2008-12-21
This thread may not be in the correct section but I figure it will be a starting place. I performed a search for related info but found none. This is not only a question but also my work around to accomplish the task. There may be another procedure that will do the same thing but I have not read or found such info in the forums. If you have a better solution, please feel free to comment.

I have installed Ubuntu 64 bit on a separate drive and had the 32 bit on another drive. I wanted to transfer all of the Evolution Mail settings, mail and address books into the new installation. This could apply whether it is 32 or 64 bit but generally ought to work.

Evolution provides a backup feature which I used and it stores that as "*evolution-backup.tar.gz*" by default to whatever location is designated. When I try to perform a restore into the new installation, it would not work.

Looking at the files that are in the Evolution folder, once I have performed the backup, I find a file named "*backup-restore-gconf.xml*". In that file, displayed in Firefox, I found the line stating, "*uid="1223775624.6713.19@Computer1*", which is/appears to be the user ID and location of the original installation. Performing a restore backup from within Evolution, on the new drive, failed using the backup file created. The file "*backup-restore-gconf.xml*" is included in the backup file created by Evolution.

To accomplish the transfer I omitted that file, copied the */home/myname/.evolution* folder contents and all of the data was recognized by the new installation. I am guessing that I could also delete that file from the compressed backup file or change the line in the "*backup-restore-gconf.xml*" file to reflect the new drive (ie ... computer 1 to computer2) and accomplish the same results, keeping the "uid" the same.

Is this something that anyone else has attempted?

What has been your experience?

This seemingly would apply only on trying to transfer the data to a different drive or the same drive if it has been renamed during the Ubuntu installation.

---

