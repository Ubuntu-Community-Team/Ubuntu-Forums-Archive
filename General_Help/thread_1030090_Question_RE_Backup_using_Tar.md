---
title: "Question RE Backup using Tar"
date: 2009-01-04
forum: General Help
---

### Post by schmickers on 2009-01-04
Hi all, I'm currently trying Ubuntu 8.10 - I last used 6.06 and found it problematic with my hardware, but I am finding 8.10 very stable on new-ish laptop.

I want to establish a backup scheme, and I plan on using Tar. I have read several tutorials which discuss what folders to exclude from a system backup. I'm just wondering if it is safe to exclude the /etc/fstab file? The reason I ask is that when I last used ubuntu, I attempted to do a system backup and then restore it onto a larger disk; it went relatively well but I was then stuck trying to edit fstab by hand because it was set up for the previous disk.

Essentially, my aim is to end up with a file that I can restore onto a larger or upgraded drive, or even a different machine, and have a working copy of my system restored without having to do too much fiddling.

Any ideas?

---

### Post by RealPSL on 2009-01-04
The newer releases of Linux distributions use uuid to identify the partitions and mount the partitions based on this uuid. These unique identifiers will be different from machine to machine so even if you backup the /etc/fstab and I think you should if you create more than the default file systems you will need to modify to input the uuid on your system. An example is below for the uuid in /etc/fstab:

```
UUID=ff1165de-7e3a-48c8-899d-840f3bc7f775 /home           ext3    relatime      
  0       2
```

Once you get to your new machine you can obtain the new uuid from the following command

```
$ blkid
....
/dev/sda9: UUID="ff1165de-7e3a-48c8-899d-840f3bc7f775" TYPE="ext3"
...
```

There is a wealth of information on system backups here [https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

I am actually considering sbackup myself.

[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html]("http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")

---

