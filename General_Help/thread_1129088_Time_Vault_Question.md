---
title: "Time Vault Question"
date: 2009-04-18
forum: General Help
---

### Post by planemanx15 on 2009-04-18
I have been thinking about installing Time vault since my 8.10 system crashed.  I'm not too concerned about the data because I was able to retrieve it via a USB 8.10 bootable disk.  I'm going to rebuild it with 9.04 next week and had a question about time vault.  Is it possible to make a backup of my system and if it crashes again and needs a rebuild, to pull those files from the new build?  I'm going to have all the data sent to a USB hard drive so once its plugged in its mounted. I just want to know if the data can be retrieved from a second computer.  If it cannot be done, what is another simple GUI automatic backup solution?

---

### Post by juancarlospaco on 2009-04-18
**Back In Time.**

---

### Post by Dougie187 on 2009-04-20
I don't know how useful Time Vault is, since it seems like development hasn't changed in a while. However if you do decide to try it post some information about it here. But I would think it would work the way you described, but I have never tried it myself.

Also, there are some other choices you can look at on the TimeVault website, like flyback ([http://flyback-project.org/](http://flyback-project.org/))

---

### Post by StuartN on 2009-04-21
I like diff -qr dir1 dir2 to generate a list of all the files which have changed since the last backup - it is recursive, so it is a full directory tree. Meld is a graphical utility that displays changes between two directory trees and allows you to send changed (or new) files from dir1 to dir2 - you can save a comparison for reuse.

rsync -avh --delete dir1 dir2 makes a copy of dir1, only writing the files that need to be changed. dir2 can of course be an external or network drive. Grsync is a graphical version of rsync and provides plenty of help on the command line parameters.

A really neat idea is given by [http://blog.interlinked.org/tutorials/rsync_time_machine.html](http://blog.interlinked.org/tutorials/rsync_time_machine.html) where the option --link-dest is used to create Timemachine-style incremental backups.

I have as much disk space as laziness, so I simply rsync my entire ~/ structure to a network disk whenever I have made significant changes, and mirror dated copies of that onto an external drive occasionally.

---

### Post by Dougie187 on 2009-04-22
> **StuartN said:**
> I like diff -qr dir1 dir2 to generate a list of all the files which have changed since the last backup - it is recursive, so it is a full directory tree. Meld is a graphical utility that displays changes between two directory trees and allows you to send changed (or new) files from dir1 to dir2 - you can save a comparison for reuse.

rsync -avh --delete dir1 dir2 makes a copy of dir1, only writing the files that need to be changed. dir2 can of course be an external or network drive. Grsync is a graphical version of rsync and provides plenty of help on the command line parameters.

A really neat idea is given by [http://blog.interlinked.org/tutorials/rsync_time_machine.html](http://blog.interlinked.org/tutorials/rsync_time_machine.html) where the option --link-dest is used to create Timemachine-style incremental backups.

I have as much disk space as laziness, so I simply rsync my entire ~/ structure to a network disk whenever I have made significant changes, and mirror dated copies of that onto an external drive occasionally.

Sure thats easy, but in theory timevault would give you far more features. For instance, if you change a file, the file would be backed up as soon as you changed it. So if you decided you wanted to revert back to the previous version, timevault should have it for you.

---

