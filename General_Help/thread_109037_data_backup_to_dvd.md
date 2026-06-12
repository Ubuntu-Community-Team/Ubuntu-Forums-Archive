---
title: "data backup to dvd"
date: 2005-12-27
forum: General Help
---

### Post by bsm0f0 on 2005-12-27
Hello all, I need a little help finding a backup solution for Ubuntu.  I'm having a hard time finding something to replace Nero BackupItUp on Windows.

Basically I have a Windows machine running as a file/backup server and would like to give the machine to a friend's child for school.  The machine does nothing but store documents and photos on a 160gb drive that are backed up to DVD via scheduled selective jobs in Nero BackItUp.

Is there an application that can do this in linux/Ubuntu?   Unfortunately NeroLinux does not include the BackItUp feature (or perhaps I'm wrong).  I searched on the forums and a few other sites but the enterprise level solutions (network backup) and creating images of the hard drive are not what I'm looking for (otherwise I'd just use ghost).

Gui or command line will work. I just need something that schedules tasks, allows for specific file and folder selection, and is reliable should I need to unarchive something.

Thanks for the help!

---

### Post by ninotob on 2005-12-27
Is that 160gb HD full?  That's about 35-40 DVDs.  It seems that everything would be faster, easier, and ultimately cheaper, if you just used a USB drive.  Backup and then take the drive offsite for safe keeping.

Anyway, from the command line, you can make "TAR" (tape archive) files, and compress them.  It can be selective or not, do incremental backups, and lots of things.

Start with "man tar" at the command line, it'll show you the possibilities.  That'll get you as far as the backups.  From there, you should probably look at "cdrecord" and command line CD/DVD writing materials.  I used to do my backups this way -- I don't burn discs anymore and I've sort of forgotten most of this end.

---

### Post by bsm0f0 on 2005-12-27
I looked into external hard drives ... unforunately, that's the more expensive route as the reason I use DVD is for archiving purposes. 75 cents for 4gb vs. $150 for 80gb is cheaper in the end and eventually I run out of space on the hard drives ... with DVD, I just put another one in.

I don't have much of an advantange in compressing the images but for the docs it might save me some space. I'll take a more in depth look at cdrecord to see if that will serve my purpose.  Thanks for the info ninotob.

I should add, I'm only using about 35gb of the 160gb at the moment ... that doesn't include OS, etc.

---

### Post by jchau on 2006-09-30
I'm also looking for a method of backuping files to DVDs (cheapest meadia I can find; don't have a tape drive).

Preferably, it should be able to burn the DVD on the fly (while the archive is being made); I don't have enough free HD space left to tar my entire file-system.  However, I do have enough space to store about 3 DVD images.

I want to use all the free space available on the DVD (so splitting a file between 2 DVDs is fine).  Compression will be nice too, but I'd like to be able to retrieve a file without loading the entire archive.  

I've considered using tar and cdrecord, but how do I get them to work together?  

The following features will be nice to have too:
- incremental backups (for the future)
- encrypted filesystem? LUKS on the DVD?

Since I have the DVD burner I don't need to do backups over the network.  


Do I need to get a full-blown suite like AMANDA or is there a simpler solution (like a command-line, shell-script, source for small binary, or a small package)?

---

