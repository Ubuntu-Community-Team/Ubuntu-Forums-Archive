---
title: "Desktop backup solution"
date: 2010-08-17
forum: Desktop Environments
---

### Post by mo_roodi on 2010-08-17
Hi all,

I've recently started using Ubuntu as my main desktop operating system and I'm looking for a backup solution that is able to backup not only my documents and various other files that I have on the system, but I also need it to backup and create restore images for the operating system. 

Any help would be greatly appreciated. 

Mo

---

### Post by SoFl W on 2010-08-17
A question asked numerous times, a search would have turned up an answer.
[Clonezilla ]("http://www.clonezilla.org/")

For quick backups I use a simple function in my .bashrc file
```
function hbackup { # -- backup my home directory to the external drives
   cd /home
   cp -ru USERNAME /media/RAID1/Backups/home_dir/
   cd
   }

```Add ubuntu forum search to FireFox change to the /usr/lib/firefox-addons/searchplugins directory create a new file  "ubuntu_search.src " as sudo

```
<search 
 name="Ubuntu-Forums"
 method="GET"
 action="http://www.google.com/search"
 queryCharset="utf-8"
> 
  <input name="q" user>
  <input name="sitesearch" value="ubuntuforums.org">
</search> 
```

---

### Post by wkulecz on 2010-08-17
I don't think clonzilla is what he wants:

"Online imaging/cloning is not implemented yet. The partition to be imaged or cloned has to be unmounted."

Read up on rsync.  Hard drives are cheap, buy a second drive the same or larger than your current one and "clone it" with rsync from a root cron job.

Something like:

rsync -ax / /media/backup is what I use.

Its then very easy to boot from the backup drive if the main drive fails.

---

### Post by Frogs Hair on 2010-08-17
Back in Time from the repository  works nice for home folder backup and restore.

---

