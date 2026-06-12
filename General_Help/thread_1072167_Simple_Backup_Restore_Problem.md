---
title: "Simple Backup: Restore Problem"
date: 2009-02-17
forum: General Help
---

### Post by GuiGuy on 2009-02-17
Hi,
I have been backing up using SImple Backup. It seemed to have done its job, with daily backups logged onto a backup HDD. Inspection shows that the archived files are definitely there. 

However, I had a failure today and my Thunderbird directory got trashed. 

Easy, I thought, restore. 

I started Simple Backup's restore and pointed it at my backup archives. 

It tells me there are no backup files found. 

Anyone know what's going on?

Thanks

---

### Post by asafche on 2009-02-17
when you formated the HDD what structure you configured it for? (ext3, fat32, nstf)

---

### Post by GuiGuy on 2009-02-17
> **asafche said:**
> when you formated the HDD what structure you configured it for? (ext3, fat32, nstf)

etx3

---

### Post by asafche on 2009-02-17
can you manually access those files?

---

### Post by GuiGuy on 2009-02-17
> **asafche said:**
> can you manually access those files?

Yes, but a restore that way is going to be tedious. The full backup is about 40G and takes forever to load into ark. I have about 20 incrementals since the last full backup.

Also, 

a) I just noticed a number of other files are trashed; and
b) starting simplebackup from a shell traces an error "cannot find /home/user/.simplebackup.conf"

thanks

---

### Post by GuiGuy on 2009-02-17
> **asafche said:**
> can you manually access those files?

Correction: The full backups are corrupted. I had three. I then checked the full backups from the other four PCs (ubuntu) in the house and they are all corrupted as well. :(

This is really annoying.

---

### Post by asafche on 2009-02-17
i don't really know this software, but my intuition is that the backup-ing itself created corrupted files. 

try to find out if any other user of this software mentioned a problem as yours.

---

### Post by GuiGuy on 2009-02-17
> **asafche said:**
> i don't really know this software, but my intuition is that the backup-ing itself created corrupted files. 

try to find out if any other user of this software mentioned a problem as yours.

The annoying part is that this is the software that a number of "knowledgable" people recommended  (here and elsewhere). It also features widely in Ubuntu discussions.

The log files indicated that there were no errors during the backup process. 

My suggestions to those contemplating [Simple Backup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite")? At your peril!

Cheers

---

### Post by GuiGuy on 2009-02-18
Sorry if I went a bit stupid here, but it has really annoyed me to see what I thought were diligent backup strategies for my home network fall in a heap because the backup program messed up the archives :(

Anyway, I had an Acronis image from about a month ago which helped. It just means I have lost the last month's emails. 

PS: I'll mark this as solved although I will now have to find alternative backup software. 

Thanks

---

