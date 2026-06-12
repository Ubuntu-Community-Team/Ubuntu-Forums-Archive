---
title: "suggested options for using rsync to backup"
date: 2009-04-08
forum: Desktop Environments
---

### Post by graysky on 2009-04-08
I have a new hdd that I'd like to use to mirror some of my data.  I thought I'd go about doing it via rsync and wanted to get suggestions for the community as to the best set of switches to use.

I was thinking about the following after reading through the [rsync manpage](http://www.ss64.com/bash/rsync_options.html):

```
rsync -avux --progress --delete-after /home /media/backups/home
```

What do you guys think?

---

### Post by vanadium on 2009-04-08
> the best set of switches
What is "best" for you is not necessarily "best' for me. These switches are "options" after all, allowing you to make choices that suit you nest.

Mirorring a partition requires the options "-a --delete" at minimum. If you want to preserve hard links in the copy, you additionally need the -H switch. This considerably slows down the backup proces, though, which is why that option is not turned on by the -a option by defauult.

---

### Post by crazy ivan on 2009-04-09
I use 

```
rsync -av --progress --delete-after /home/ /media/backups/home
```

to see if its working.. and 

```
rsync -a --delete-after /home/ /media/backups/home
```

in my cron scripts to sync between various harddisks. Emphasis on "/home/" to avoid additional folders...

---

### Post by FrankT-Qc on 2009-04-09
One thing's for sure, you want to start with "-n" which stands for "don't do nothing, just tell me what you would do" ... Believe me, it's 30 seconds well spent...

have fun

---

### Post by hictio on 2009-04-10
If you are going to use rsync a lot to make backups, take a look at [Rsnapshot](http://rsnapshot.org/), its an amazing Perl script to use rsync to keep snapshots of parts of your system (or the whole thing)
It is on the repositories.

---

### Post by ahbart on 2009-04-10
I used a script to backup with rdiff-backup (It is in the repository), but recently found a new frontend for that: pybackpack.
Very easy.

---

