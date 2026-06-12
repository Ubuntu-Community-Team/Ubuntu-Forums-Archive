---
title: "I Need a Backup Solution on Ubuntu --HELP"
date: 2009-02-11
forum: General Help
---

### Post by darthpenguin on 2009-02-11
OK so I need a backup solution for Ubuntu. I have TimeVault running but I don't understand what it is doing. When I look at the drive it is backing up to (an external USB HDD ext3 mounted at /backupdisk) I see all kinds of cryptic stuff. Where are the files?

All I need is for Ubuntu to automatically (daily) detect any changes to my ~/ (home) folder and copy those files and folders to my external disk. perhaps keep up to 7 backups so that when it backs up on Monday last Monday's backup is deleted. I think this is called incremental backups. 

I don't need it zipped or anything. I want to be able to see the files on the backup to know that they are in fact backing up. I don't want write permissions because I have no reason to remove anything from the backup. I would like to see a log file so that I know if something isn't backing up or if there is some other error. I don't need this so that I can recover one file at a time. I need this in case my hard drive crashed. I don't want to loose all my docs, pics, videos, etc.

If I could get all this in a GUI with a system tray icon/notifier and a progress bar/indicator that would be perfect and, in fact, I can't imagine why such a program dosn't ship with Ubuntu.

I know many create a script that uses rsync and keeps it in /etc/cron.daily it's no GUI but it seems to work for them. I have never written a script before. If this is the best way to backup could I get some coaching on building a script that will do all the above functions. But go slow, I'm kinda a noob.

Thanks in advance for any help

also I would like to backup Evolution. I use gmail and it leaves messages on the server so that is backed up on-line I guess. but can I incorporated a backup of my contacts in a script or can I automatically sync my contacts between evolution and gmail?

---

### Post by Tibuda on 2009-02-11
I use [grsync]("apt:grsync"), which is a friendly interface for rsync.

---

### Post by darthpenguin on 2009-02-11
I have looked at grsync but i have a few problems with it.

I don't think it can schedule backups. And It tends to hang, freeze, and crash.

any other suggestions?

---

### Post by Tibuda on 2009-02-11
> **darthpenguin said:**
> I have looked at grsync but i have a few problems with it.

I don't think it can schedule backups. And It tends to hang, freeze, and crash.

any other suggestions?
Yeah, it doesn't schedule backups, but never crashed with me. I manage cron with [gnome-schedule]("apt:gnome-schedule"), which you can use. You can also try [TimeVault]("https://launchpad.net/timevault") or [Flyback]("http://flyback-project.org/"), but I never used them.

---

