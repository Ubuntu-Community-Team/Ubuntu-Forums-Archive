---
title: "Which folders should I backup?"
date: 2009-05-01
forum: General Help
---

### Post by amrbekhit on 2009-05-01
Hello all,

I've been moving wholly to Ubuntu these past few months and the issue of backups has popped up.

On Windows, I stored everything in My Documents and when backing up, it was a case of just backing up the entire My Documents folder. In Ubuntu I have thought of just backing up my home directory but a question has come up.

As I understand it, the home directory, as well as storing my personal files and folders also contains program settings. Should these program settings also be backed up? What I'm worried about is restoring my home directory at some point in the future, and overwriting existing settings. For example, if I backed up my machine when OpenOffice was at version 3, then later on, I restored my archive onto a machine where OpenOffice was on version 4, would my restored settings cause any problems with the program?

Also, I downloaded the Simple Backup Utility from the repos and noticed that there were several folders which they automatically include in the backup (/var, /usr/local, /etc) - as I understand, for example, /usr/local contains my installed applications. If I restore this at a later date when newer versions of these same applications are already installed on my machine, could this not screw up my installation?

So in brief, should I just backup my regular files and folders or is it advisable to backup these extra parts of the file system as well?

Thanks

--Amr

---

### Post by theozzlives on 2009-05-01
You shouldn't let your backups get that old in the first place.

---

### Post by mb_webguy on 2009-05-01
Restoring configuration files shouldn't be a problem as long as you're not restoring settings from an earlier version of Ubuntu to a more recent one.  Ubuntu doesn't upgrade applications for a given version once it's released except for bug fixes and security updates, so you generally don't have to worry about your configuration files being incompatible with new versions of software -- because your software generally won't change.

The /usr/local directory contains software you've installed locally, such as compiling from source, rather than through the package manager.  It's generally a good idea to backup this directory since the software in /usr can easily be restored the package manager, while restoring locally installed software would necessarily be more difficult.

The /var directory is suggested for recommendation because it contains system-wide data files.  For example, the default web directory for Apache is located here, as is the default data directory for MySQL databases.  

Likewise, the /etc directory contains system-wide configuration files.  If you've changed these files, you definitely want to back them up.

As for what you *should* backup, it just depends on what you consider important, and what would be most difficult for you to recover without a backup.  If you only install software from the repositories, don't install software that keeps data in the /var directory, and don't alter system-wide configuration files, you can get by with just backing up your home directory.  If any of the above isn't true, you might think of also backing up the related directories as well.

---

