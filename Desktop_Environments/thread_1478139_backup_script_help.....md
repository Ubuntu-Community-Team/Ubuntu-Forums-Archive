---
title: "backup script help...."
date: 2010-05-09
forum: Desktop Environments
---

### Post by speedway on 2010-05-09
Hi all

I am not much of a commandline person aside from following orders, so to speak. I am looking for help with a shell script that could be run from cron to backup some of my files on a nightly basis to another drive in the same machine.

Basically I want to back up the following:

My home dir, including "hidden" files e.g. ".XXXX"
/etc/X11/xorg.conf
/etc/samba/smb.conf
/etc/network/interfaces
/etc/resolv.conf
/etc/fstab
 plus execute a MySQL backup script for one particular database.

Can all that be done in one script? Anyone care to show me the way of accomplishing all that... please :) :KS

Please be gentle, I am more a desktop warrior than a command line warrior.

Thanks in advance

Cheers
Bruce

---

### Post by jd65pl on 2010-05-09
take a look at [rsync]("https://help.ubuntu.com/community/rsync"), and [mysqldump]("http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html")

---

### Post by speedway on 2010-05-09
Great, thanks. Rsync might be my friend, mysqldump not so much. There is already a utility to back the DB up on the system (MythBuntu) so it would be simply a case of starting that.

Off to do some reading.....

Cheers

---

