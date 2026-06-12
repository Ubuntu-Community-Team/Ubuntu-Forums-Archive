---
title: "backupPC, muliple hosts"
date: 2011-05-13
forum: Desktop Environments
---

### Post by chitowner2 on 2011-05-13
Any backupPC gurus out there?

I think my query is pretty basic, but after perusing the various config settings in the backupPC CGI I am uncertain how to do this, but am certain it is a normal approach.

I want to define scheduling so that only one host backup runs at any given time, eg, I want to avoid having any two hosts (clients) being backed up in overlapping time periods. 

This is because I know that one of my hosts will require 16+ hours to complete a full backup, and that is with the maximum bandwidth my LAN can provide, and if backupPC tries to run any of the other hosts during that period, everything on the LAN will slow down and in particular the time to complete any backup will be extended.

If someone who knows this CGI well enough could kindly outline which steps to take to achieve this I would be very grateful.

Thanks,
CT
:redface:

---

### Post by DommerD on 2011-06-01
Hi CT.  I'm working on setting up BackupPC as well.  
In your /etc/backuppc/config.pl file, change the MaxBackups to 1. The default is 4.

> 
$Conf{MaxBackups} 
Maximum number of simultaneous backups to run. If there are no user backup requests then this is the maximum number of simultaneous backups.


Dom

---

### Post by chitowner2 on 2011-06-02
> **DommerD said:**
> Hi CT.  I'm working on setting up BackupPC as well.  
In your /etc/backuppc/config.pl file, change the MaxBackups to 1. The default is 4.

Dom

Thanks Dom, I wasn't sure what that setting was for.
CT

:popcorn:

---

### Post by DommerD on 2011-06-04
You may also want to check out the parm $Conf{MaxUserBackups}.  Its the maximum number of user initiated backups that are allowed. So the total number of backups that could run simultaneously would be MaxUserBackups + MaxBackups.

I'm doing a lot of testing right now, but will be rolling it out to my network over the next few months.  So far, for backing up Windows XP machines, I've found that using rsync has been much better than trying smb.  It takes a little more configuration, but not much. I'm running the latest version of BackupPC, 3.2.1.

If you have any issues, let me know, I may have hit them too.

Dom

---

