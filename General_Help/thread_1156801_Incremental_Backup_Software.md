---
title: "Incremental Backup Software"
date: 2009-05-12
forum: General Help
---

### Post by MMoudry on 2009-05-12
Hello,
I am looking for a software that would allow me to backup the whole (or part) of my system to DVDs. Ideally it should work like this :

1. I install the software and configure it to generate chunks of data of a certain size (eg. 4200 MB for a DVD)
2. The software creates a map of filesystem and hashes all the files and directories
3. The software generates several chunks of data data in a backup directory directory that I burn to DVDs
4. Periodically the software scans all of the filesystem and compares the hashes and directory structures to see whats changed. When a change is detected it writes a diff into a new chunk of data into the backup directory
5. When the diff chunk has reached the size limit it starts a new chunk so I can write the old chunk onto a new DVD

Basically, and ideally this software would generate a binary image of the filesystem and after generate incremental data of the changes. It would work a bit like revision repositories (i.e. Subversion). Also it should maintain a change backlog so that files that werent changed but only moved are not backuped again but only the move is stored into the log.

Does anybody know of a software that does this, or is this possible with the standard linux tools?

Thanks

MM

---

### Post by LoloftheRings on 2009-05-12
I'm using rsync for this job, and used cron to make it happen every day at a specific time (lunch time for me)
Rsync incrementally copies a filesystem to another.
If you want to make one file, you could use rsync in combination with tar which can put everything into one file and optionally compress it.
Burning can be done using brasero.

---

### Post by sahabcse on 2009-05-12
Try Amanda backup tool. For more info click [here]("http://sahabm.blogspot.com/2008/05/amanda-setup-in-ubuntu-710-with.html")

---

### Post by MMoudry on 2009-05-12
> **LoloftheRings said:**
> I'm using rsync for this job, I checked the rsync and it looks like that the target filesystem needs to have a copy of the old file for this to be efficent. rsync in itself doesn't maintain any local log of what was backuped or not. I meant to delete the file chunks after they are burned. Will check Amanda....

---

