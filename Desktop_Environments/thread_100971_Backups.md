---
title: "Backups"
date: 2005-12-08
forum: Desktop Environments
---

### Post by CharlieC on 2005-12-08
I would like to backup my entire Ubuntu hard drive to a partition on a large USB external drive. In the Windows world I really like Norton Ghost but that does not work on the Linux file systems. 
Any suggestions?

Thanks
Charlie

---

### Post by IdolizingStewie on 2005-12-08
You don't need any extra programs to backup your entire system. The tar command will work, though I believe there are programs in Synaptic if you don't like the command line. Check this HOWTO thread. [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

### Post by ubuntu_demon on 2005-12-08
sbackup is an easy graphical backup tool.

[quote=$apt-cache show sbackup]
 Simple Backup Suite is a set of backend backup daemon and Gnome
 GUI frontends that provide a simple yet powerful backup
 solution for common desktop users.
 .
 Backups can be written to local directory or remote servers using
 Gnome VFS technology. A fine control is possible regarding what
 folders and files to backup. Files can be excluded even with a set
 of regular expressions. Regular backups can be scheduled.
 .
 This tool has been written with Google sponsorship during Summer
 of Code 2005 with mentoring help from Ubuntu.
[/quote]

$ sudo apt-get install sbackup

it will appear in system->administration.

(The default backup settings can take a lot of harddisk space!)

---

### Post by matthew on 2005-12-08
[quote=ubuntu_demon]sbackup is an easy graphical backup tool.[/quote]
That is awesome! I have installed it and will be testing it out. At first glance I am very impressed.

Thanks for the reference!

---

### Post by ubuntu_demon on 2005-12-09
np :)

sbackup will probably get into Dapper (more polished). See : 
[https://wiki.ubuntu.com/HomeUserBackup](https://wiki.ubuntu.com/HomeUserBackup)
[https://wiki.ubuntu.com/SimpleBackupSolution](https://wiki.ubuntu.com/SimpleBackupSolution)

here's a wiki about a way to backup from the terminal :
[https://wiki.ubuntu.com/BackupYourSystem](https://wiki.ubuntu.com/BackupYourSystem)

---

