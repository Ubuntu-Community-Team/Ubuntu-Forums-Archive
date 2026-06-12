---
title: "SimpleBackup"
date: 2008-12-30
forum: General Help
---

### Post by 4-PackDad on 2008-12-30
Hey;

Just installed "SimpleBackup"...

Runs fine except for **'1'** problem.

It can not see/reconize my config file.

./bkup: line 99: /home/quadhouse/.simplebackup/bkup_config: No such file or directory


Here's my config file:
# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
# Configuration values for Simple Backup:
# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
bkLoc='/tmp'
logLoc='/root/.simplebackup'
finalLoc=''
mustBeMounted='false'
cpbkuploc='/media/Back Up/Simple Linux Backup'
silent='0'
useronly='false'
bkupuser=''
userbcklistfile='/home/quadhouse/BackupFiles.txt'
userexclistfile='/home/quadhouse/ExcludeFiles.txt'


The Config GUI also says '/home/quadhouse'

I can see the config file is there where it should be.


Any One have any ideas...?

Thnx,
Bill

---

### Post by hal8000 on 2008-12-30
Never used the program,  but can you post the output of:

ls -l /home/quadhouse/.simplebackup

It appears line 99 cannot find a config file here.

---

### Post by xjcannonx on 2008-12-30
> **4-PackDad said:**
> Hey;

Just installed "SimpleBackup"...

Runs fine except for **'1'** problem.

It can not see/reconize my config file.

./bkup: line 99: /home/quadhouse/.simplebackup/bkup_config: No such file or directory


Here's my config file:
# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
# Configuration values for Simple Backup:
# - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
bkLoc='/tmp'
logLoc='/root/.simplebackup'
finalLoc=''
mustBeMounted='false'
cpbkuploc=[COLOR="Blue"]'/media/Back Up/Simple Linux Backup'[/COLOR]
silent='0'
useronly='false'
bkupuser=''
userbcklistfile='/home/quadhouse/BackupFiles.txt'
userexclistfile='/home/quadhouse/ExcludeFiles.txt'


The Config GUI also says '/home/quadhouse'

I can see the config file is there where it should be.


Any One have any ideas...?

Thnx,
Bill
Don't know much but why are there spaces here? If they are supposed to be spaces try using % to fill the gap or just use an underscore _ instead of a space

---

### Post by 4-PackDad on 2008-12-30
Hey;

Here U go...

ls: cannot access /home/quadhouse/.simplebackup: No such file or directory

Or maybe this is better...

quadhouse@quadhouse-desktop:~/SimpleBackup$ sudo ls / /home/quadhouse/SimpleBackup/bkup_config
/home/quadhouse/SimpleBackup/bkup_config

/:
BackupFiles.txt  dev		   initrd.img	   mnt	 srv  vmlinuz
bin		 etc		   initrd.img.old  opt	 sys  vmlinuz.old
bkup_config	 ExcludeFiles.txt  lib		   proc  tmp
boot		 home		   lost+found	   root  usr
cdrom		 initrd		   media	   sbin  var



Later,
Bill

---

### Post by xjcannonx on 2008-12-31
It is looking in /home/quadhouse for a directory named ".simplebackup" and the name of the directory you have in /home/quadhouse is "Simplebackup" 

Try to create a directory named ".simplebackup" and put the bkup_config in there, make sure the s is lower case and a . is in front of the s -- A . in front of a folder makes it "hidden"

---

### Post by 4-PackDad on 2009-01-01
Hey;

That makes sence....

Still Learning the syntax.

Did what you suggested...
Something still not right.
Doesn't want to backup to my external drive.

Here's the output:

[email]quadhouse@quadhouse-desktop:~/.simple[/email]backup$ sudo ./bkup
Starting backup in directory '/'
Full backup last performed about 1 day(s) ago.
Performing incremental backup using '/root/.simplebackup/timestamp'
-rw-r--r-- 1 root root 0 2009-01-01 11:35 /root/.simplebackup/timestamp
Copying files...
Done collecting and compressing files; return code 2.
Done!


looking at the config file...

finalLoc=''
cpbkuploc='/media/Back Up/Simple Linux Backup'

Shouldn't they be the same...?

Thnx,
Bill

---

### Post by 4-PackDad on 2009-01-04
Hey;

Found What I needed.......:D

While batchfiles/scripts & GUI's are nice.

I like to KISS & tell.

My thanks to:
Heliode

Tutorials & Tips
The place to find Ubuntu related Tips & Tricks.

 Howto: Backup and restore your system!


Thanks also go to:
bgs100

go'n to try shBackup later

Later

---

