---
title: "Can't backup"
date: 2020-11-09
forum: Desktop Environments
---

### Post by w9wi on 2020-11-09
I've been configured for weekly backups.  I'm using the default Deja Dup backup system deployed with Xenial 16.04.  
Suddenly last week, the backup process left a window behind indicating the backup failed:
"Failed to read /tmp/duplicity-(six random characters)-tempdir/mktemp-(more random characters)".

If I trigger a manual backup, I get the "Backing Up" window.  A /tmp/duplicity-(six random characters)-tempdir folder is created containing two mktemp-(more random characters) files of substantial size.  

Also created is $HOME/.cache/deja-dup/(lengthy hex directory name) and $HOME/.cache/deja-dup/metadata .  

The (lengthy hex directory name) folder contains three large duplicity-full-signatures-2020nnnnTnnnnnnZ.sigtar.gz files and three empty files - lockfile.lock and two with the machine's hostname followed by a lengthy list of decimal digits.
The metadata folder contains only a README.  (it was deleted before I could look at the contents, see below)

After a few minutes, the error message returns.  The unreadable mktemp- file was in fact one of the ones created when the backup started.  
The metadata directory (and its contents) is deleted.  So are the lockfile.lock and one of the hostname files in the (lengthy hex directory name) directory.  The other hostname file remains.  (it remains of zero size)
And, the /tmp/duplicity-(code)-tempdir directory is also deleted.  

I've tried deleting the leftover directories under $HOME/.cache -- it doesn't help.  

If I were to venture a wild guess, I'd say this happened when the machine shut down during a full backup.  (my girlfriend was insistent my machine was eating all our Internet bandwidth & I established a cron job to shut it off when I left for work.  Worked fine during incremental backups but since full backups take longer, it wasn't done when the cron job hit.  I have quietly deleted the cron job:) )  
But I may be way off about that.

Ideas?  Thanks!

---

### Post by TheFu on 2020-11-09
2 questions.

Have you tested a full restore from a backup? Better would be using a restore from 8 days ago.
and
Did you wipe the target directory where the backup sets get placed?

---

### Post by w9wi on 2020-11-09
I'm kinda reluctant to do a restore or wipe existing backups when I know there's a problem with the backup process...

But...

I do have enough room on the target volume to store another full backup.  I changed the destination directory & tried again.  It looks like it's *probably* working.  (it's showing "Scanning: " and a list of every file in the source path.  That wasn't happening before.  And it's been working longer than it did before without crashing out.  Ah, and now it says it's backing up (every file in the source path).  Again, that wasn't happening before.)

I don't expect to stay awake long enough to see it complete:)  I'll check back in in the morning & report what happens.  

I am very curious why it's crashing out on the old path.  There are 23,700-something existing files in that path, that's not a "magic number" (if there were 32,767 I'd say it was a smoking gun) but maybe fills a cache somewhere?  I suppose it doesn't make a huge difference, I can just leave it backing up to the new path & delete the older backups out of the old one to keep disk usage down to a reasonable level.

FWIW both backup paths are on a USB external hard drive formatted for NTFS.  Again, there's plenty of space on that partition.

Thanks!

---

### Post by TheFu on 2020-11-09
sometimes backup areas become corrupted. You already know the likely reason.
ntil you actually restore AND use those backups, you really don't know wether all this effort is for nothing at all.  I see this far too often.  Backups going for years, but there was a flaw and critical information wasn't included or was always corrupt.

Please test your restore process quarterly.  Virtual machines are perfect for these tests.

---

### Post by w9wi on 2020-11-10
The backup completed successfully.  

I have successfully restored selected recently-changed files.  

I like the VM idea for backup testing but that's not a practical option right now.  (maybe when I build my next machine, hopefully next summer)

---

### Post by TheFu on 2020-11-10
So - thread solved?   **Thread Tools** button near the top ---> SOLVED. 
About once every 3 yrs or so, one of my backups for 1 system will become corrupted and I have to start a new backup area for that system. After about 30 days, I'll remove the old area.

BTW, backup and restore for data files is trivial.  It is getting all the necessary OS stuff and settings where it becomes more difficult.  Took me 5 attempts (tests) to get all the stuff I needed in the backups so that the OS could be restored to completely different hardware - say after a house fire or flood where everything except the backups was lost.  Ya'll.

---

