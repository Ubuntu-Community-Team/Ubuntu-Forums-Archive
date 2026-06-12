---
title: "Tar or rsync for backup?"
date: 2009-04-29
forum: General Help
---

### Post by opteron180 on 2009-04-29
Do you use tar or rsync to backup your system? I have been using tar to backup and wondering should I migrate to rsync.

As my knowledge - rsnyc can do incremental backup but it is uncompressed; tar compress the files but no incremental option.

---

### Post by Kareeser on 2009-04-29
tar has an "update" option, as long as you don't run the command with the switch "z", as that archives it.

Personally, I use both. I set up a cronjob to backup all the important files into .tar.gz, and then use rsync to transfer the backup to other computers.

---

### Post by Simian Man on 2009-04-29
I only really back up source code and papers all of which are in plain text files.  Tar with compression makes these backups so small that there is no point in anything fancy.  What kind of data are you backing up?  Is it easily compressible like text files, or pre-compressed like jpeg images or mp3s?

---

### Post by lovinglinux on 2009-04-29
Why not using both? I use rsync to do incremental backup, but then I compress the content for storage.

---

### Post by kpkeerthi on 2009-04-29
tar for root and /boot

rsync (incremental) for /home. 


There is no point tarring up home contents as most of it are videos, mp3 and jpgs that are already compressed formats. It a waste of time and cpu compressing contents that are already compressed.

---

### Post by lovinglinux on 2009-04-29
> **kpkeerthi said:**
> tar for root and /boot

rsync (incremental) for /home. 


There is no point tarring up home contents as most of it are videos, mp3 and jpgs that are already compressed formats. It a waste of time and cpu compressing contents that are already compressed.

Good point, I forgot about that. I do incremental backups of home, but I exclude everything from the sync, except the hidden files. Then I use tar to compress the most important not-hidden folders. I don't back up media files, because I haven't enough space.

---

### Post by shel-hall on 2009-04-29
> **opteron180 said:**
> Do you use tar or rsync to backup your system? I have been using tar to backup and wondering should I migrate to rsync.

As my knowledge - rsnyc can do incremental backup but it is uncompressed; tar compress the files but no incremental option.
I much prefer to have plain files on the backup medium, rather than anything compressed, bundled, archived, etc.  It makes restoration much easier.  It's more reliable, as well, since most systems that bundle/archive files are liable to lose large chunks of those archives if one part is unreadable.  "tar" used to be infamous for writing archives it couldn't read, because of hidden faults glossed over when it wrote the archive.

I currently rsync our workstations and laptops to a central server, then rsync that to an off-site server, where the data eventually gets written to tape.

"rsync" does compress stuff over the wire, though the files it writes are exact copies of the ones it reads.  Its differential transfers, copying only the files and parts of files that have changed, means that backups are really fast, after the first one.

-Shel

---

### Post by logos34 on 2009-04-29
tar + gzip (/home)

For / I just take a weekly image with Partimage (also .gz compressed)

---

### Post by opteron180 on 2009-04-29
> bundle/archive files are liable to lose large chunks of those archives if one part is unreadable. "tar" used to be infamous for writing archives it couldn't read, because of hidden faults glossed over when it wrote the archive.

I agree with your point, backup reliability is one of the major factor I am looking into over capacity and speed. 
I save all my documents in a central file server, leaving the needs to back up 20GB root files via tar - saved me over 70% of drive space. For me, backing up 3 times will approximately equal to a full rsync mirror - pretty good redundancy.

> tar has an "update" option, as long as you don't run the command with the switch "z", as that archives it.
I believe most home users use tar to save space, taking out the -z switch would destory the original purpose of tar.

---

