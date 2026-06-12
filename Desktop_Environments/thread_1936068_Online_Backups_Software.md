---
title: "Online Backups Software"
date: 2012-03-05
forum: Desktop Environments
---

### Post by rclodfelter on 2012-03-05
I'm looking for a product to backup my ubuntu installatiuon onto a nas drive so that if I lose everything I can restore back to that snapshot.

I've looked at Redo Backup, Clonzilla, and PING. Some how I screwed up my installation and had to re-install from the live cd after messing w/Clonezilla. :-(

What I'm looking for is something that can run with the system up. I don't want to have to boot up from a live cd. In Windows I've used Acronis for years to take an image of my HD. 

Any suggestions will be appreciated.

---

### Post by TheFu on 2012-03-05
A running system leaves important files open. That may cause corruption to your backups and may prevent a restore from working properly.

With that in mind, I usually perform a 2-stage backup method.
1) 100% mirror of the system - quarterly or so - after booting from alternate media
2) daily backups of all configs, programs, and data; I do stop RDMBS programs prior to running the backup to ensure those constantly changing files are backed up "clean". Others might dump their DBMS to a text file and perform their backup using that (and probably the open DBMS file too). We just assume the running DBMS files will be corrupt during restoration.

The first part of the backup can be accomplished in many, many, many different ways or you can simply keep a LiveCD around and plan a fresh installation instead.  Clonezilla and partimage and 'dd' or 'dd-rescue' are ways to accomplish this. There are many others.

The 2nd part of the backup can be accomplished in many, many, many different ways too. Popular methods include:
* rsync (I don't consider this enough of a backup)
* Duplicati / Duplicity / Déjà Dup
* rdiff-backup (my favorite)
* rbackup
* rdiff
* tar + gz

* dump
* Back-in-Time (Mom uses this)
* LVM snapshots
* Anaconda
* Amanda
* Bacula
* BackupPC

I've used many of these tools. If your NAS is running a Linux/UNIX file system (not NTFS), then you can make use of hardlink methods in your backups. Don't forget their are special files and file systems that you don't want to backup under Linux, so be certain to exclude those.

I really like rdiff-backup these days (and for the last 4 yrs).  Restoring a few files is trivial and doesn't mean I need to find the backup software. My backup script does a few things before running the backup too. Things like:
* dumping the current list of installed packages to a file.
* dumping the current hardware to a file.
* cleaning up cache files like ~/.adobe/ 
* mirrors critical files (password databases) to multiple other systems around the country.

These links should be helpful
* [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
* [http://wiki.debian.org/BackupAndRecovery#Backup_tools_and_suites](http://wiki.debian.org/BackupAndRecovery#Backup_tools_and_suites)

---

### Post by drfox on 2012-03-05
Consider CrashPlan 
[www.crashplan.com](www.crashplan.com)
They have a free version for backing up locally as well as to remote computers. 
They also have paid versions for backing up to their servers.
I've been using it for about a year and have purchased the family version and use it to sync data amongst various computers. I think the price is reasonable.
Larry

---

### Post by rclodfelter on 2012-03-21
I've tried many of the suggestions but still can't do what I want to. I'd like to be able to backup my system while it is online. I can't afford the downtime.

In the event of a crash I'd like to be able to reinstall Ubuntu and then copy back all my installed apps, settings and docs. I've tried that in a virtual machine using tar and deja_dup but I think I am copying back system files and hosing things up.

What I need are the directories to include and exclude to accomplish this.

TIA if any know this and can share.

---

### Post by TheFu on 2012-04-05
If you need list level of availability, then a single system isn't the answer. You probably want at least 2 systems and an application design that allows sending all transactions to both, 1 or the other system.  RAID, clustering, replicated filesystems, system and storage geographically separate by at least 500 miles, etc all go into a completely HA solution.

LVM snapshots is the easiest method to do what you want, but it adds complexity.

If you have a SAN, you can using something like BCVs on the storage side.
If you are only worried about an active DB file being opened, there are many different methods, techniques and tools to backup a running DB. Each is DB specific.

This sounds like a work - for profit - undertaking.

---

