---
title: "Ok what do I do exactly for a regular backup."
date: 2006-04-22
forum: Desktop Environments
---

### Post by eugman on 2006-04-22
I need to do regular backups as tar.gz files into a fat32 partition. I'd like to have it cron'd to do the backup once a week. If possible I'd like the archives to be broken up into the root folders so if I want to burn a a dvd of home and var I can do that.

Also if it's possible I'd like to be able to do incremental updates instead of having
to make new archive files every single week. It'd also be nice to have an easy way to be able to restore to the backup state by live cd if I mess up my installation. 

I generally understand the tools needed to do all of this but I have no idea exactly how.

---

### Post by aysiu on 2006-04-22
Officially it's a Qt application (not a Gtk one), but it should work in Gnome, too. Look into *kdar*--it's in the repositories.

---

### Post by st0kes on 2006-04-22
You could implement a shell script to run nightly via cron. A really good one was posted on linuxforums.org a few weeks ago --> [here's the link]("http://www.linuxforums.org/forum/linux-newbie/58607-home-directory-backup-script-newbies.html").

---

### Post by claydoh on 2006-04-22
also look at [sbackup]("http://sbackup.sourceforge.net/HomePage"), it is pretty comprehensive, though not quite as much as dar/kdar, I do not remember if it will break down archives by size however.

---

### Post by aysiu on 2006-04-22
I tried sbackup. What I didn't like about it was the lack of a progress bar. When you start the backup, it says the backup is running in the background, but it gives you no indication of when it'll be done.

---

