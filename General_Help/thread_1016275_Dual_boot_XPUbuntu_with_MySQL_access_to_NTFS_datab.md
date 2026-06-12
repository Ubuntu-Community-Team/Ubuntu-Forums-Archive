---
title: "Dual boot XP/Ubuntu with MySQL access to NTFS databases"
date: 2008-12-19
forum: General Help
---

### Post by cscj01 on 2008-12-19
I have a dual boot system using XP SP2 with MySQL 5.0.67 and Ubuntu 8.10 with MySQL 5.0.67. My databases are on an NTFS partition created in XP and use InnoDB. I would like to use the same databases, temp space, and log files no matter which OS I am using. If I can do this, the changes I make while in one OS will be there in the other OS when I boot to it. Additionally, my logs will reflect the true state of the data.

My NTFS partition mount point in Ubuntu is /media/Data, and I have tried to point to my databases, temp file, and log files by specifying /media/Data/... for the appropriate path and/or file for each in my.cnf on Ubuntu. However, MySQL in Ubuntu cannot access the InnoDB files.

All my table names are lower case although I do have some directories on the NTFS partition with embedded spaces in their names.

Something else seems to be going on. MySQL documentation states that tables and logs are binary compatible between Linux and Windows. So, I copied my database files to my Ubuntu file system. In Ubuntu, MySQL Administrator only shows my myISAM tables. MySQL Query Browser shows the InnoDB tables, but says they are empty.

With that, I am wondering if I need to copy the ibdata1 file and ib_logfile0 and ib_logfile1 files as well.

I am going to try that to see if I can access existing InnoDB data of my XP system from my Ubuntu system after copying it. If I can, I am still at a loss as to why I cannot access those files when I am in Ubuntu. When I created a my.cnf with data path, InnoDB data path, log path, and temp data path pointing to the files on the NTFS drive, MySQL would not initialize. Using the command 'sudo /etc/init.d/mysqld start' only results in a fail indication with no other information.

I also modified the apparmor configuration file to include the NTFS paths and reloaded the apparmor profile.


Any help or advice would be greatly appreciated.

---

### Post by dcstar on 2008-12-20
> **cscj01 said:**
> I have a dual boot system using XP SP2 with MySQL 5.0.67 and Ubuntu 8.10 with MySQL 5.0.67.
.........

I didn't see an innodb plugin for that version on their website, should it work without one?

---

### Post by cscj01 on 2008-12-22
I am not aware that MySQL 5.0.67 requires a plugin under Ubuntu 8.10.  I can create an InnoDB database from scratch, so InnoDB databases must be supported

---

### Post by cscj01 on 2008-12-31
Well, I can say for sure that MySQL data and log files are not binary compatible between Windows XP and Ubuntu 8.10.  After copying my data files to Ubuntu, I could only see MyISAM tables with MySQL Administrator.  MySQL Query Browser showed the InnoDB tables but said they were empty.  So I copied ibdata1, ib_logfile0, and ib_logfile1.  MySQL choked (would not start; only showed "Fail" as a reason.

It seems to me the solution to this issue should be simple; just point MySQL to the data, no matter the OS.  But, that doesn't work.

Say it ain't so, Joe.

---

### Post by albertmatyi on 2009-10-20
OK. I couldn't get it working neither. It is because you should change the context of the file (using chcon), which is not supported by NTFS.... If only I could disable the checking of the context.

btw this is the command for changing the context, so mysql could work 

chcon -R -u user -r role -t mysql_db_t /path/to/data

matyas

---

