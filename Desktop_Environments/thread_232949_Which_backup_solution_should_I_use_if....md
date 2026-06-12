---
title: "Which backup solution should I use if...?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by kentl on 2006-08-09
Hi!

I want to start making backups according to the following schedule:

I have a given set of directories from which I want to backup some files, not necessarily all. It's good if I can exclude files from the backup using a regular expression. With this set I want to:
[LIST=1]
[*] Perform a daily incremental backup.
[*] Perform a weekly full backup.
[*] Store all the weekly full backups on my hard drive for one month.
[*] Burn a monthly backup to a CD or DVD in which I include the latest weekly full backup. This CD or DVD will be archived with my permanent backups.
[/LIST]

Perhaps using a cron job would be the best approach? And if so using which commands? I'm picky about the above backup scheme and I don't want to change it, as I think it's well thought through.

All answers will be greatly appreciated. :D

---

### Post by etank on 2006-08-09
Take a look at Simple Backup. It is in the repos.```
sudo aptitude install sbackup
```It should do all the things that you are wanting except the burn to CD. Otherwise you could do the same thing with tar and a coulple of cron jobs.

---

### Post by kentl on 2006-08-09
It seems like it fulfills my needs. Thanks for the suggestion! :)

---

