---
title: "Ubuntu 6.x and rdiff-backup and Keep"
date: 2007-03-15
forum: Desktop Environments
---

### Post by Edk on 2007-03-15
I am trying to run Keep (Under Gnome and KDE) or rdiff-backup from the console

Whatever I do I get horrendous error messages, which I reproduce below.

It does not matter whether I backup to a local folder or to my NAS - which is the eventual aim of the game.

System details:
My version of Python is reported as:

Python 2.4.4c1 (#2, Oct 11 2006, 21:51:02)
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)] on linux2

My rdiff-backup version reports as:
rdiff-backup 1.1.5

Gnome version 2.16.1

Ubuntu 6.10

Error message is:


[INDENT]An error occured making /home/edward backup:
Exception 'class ErrorLog has no attribute '_log_inc_rp'' raised of class 'exceptions.AttributeError': File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 295, in error_check_Main try: Main(arglist) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 315, in Main take_action(rps) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 271, in take_action elif action == "backup": Backup(rps[0], rps[1]) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 328, in Backup backup_final_init(rpout) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 430, in backup_final_init ErrorLog.open(Time.curtimestr, compress = Globals.compression) File "/usr/lib/python2.4/site-packages/rdiff_backup/log.py", line 216, in open else: cls._log_fileobj = cls._log_inc_rp.open("wb", compress = 0) Traceback (most recent call last): File "/usr/bin/rdiff-backup", line 23, in ? rdiff_backup.Main.error_check_Main(sys.argv[1:]) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 295, in error_check_Main try: Main(arglist) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 315, in Main take_action(rps) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 271, in take_action elif action == "backup": Backup(rps[0], rps[1]) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 328, in Backup backup_final_init(rpout) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 430, in backup_final_init ErrorLog.open(Time.curtimestr, compress = Globals.compression) File "/usr/lib/python2.4/site-packages/rdiff_backup/log.py", line 216, in open else: cls._log_fileobj = cls._log_inc_rp.open("wb", compress = 0) AttributeError: class ErrorLog has no attribute '_log_inc_rp[/INDENT]


Has anyone ANY idea what this is all about?  Please be gentle with replies as I am still a learner!

Failing that what is a good backup program to back up to a NAS?

Thanks


Ed

---

