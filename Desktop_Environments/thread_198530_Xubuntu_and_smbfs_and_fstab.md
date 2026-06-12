---
title: "Xubuntu and smbfs and fstab"
date: 2006-06-17
forum: Desktop Environments
---

### Post by satbunny on 2006-06-17
Before I bore you all, does Xubuntu support mounting external samba shared drives using fstab and smbfs?

I moved my laptop from Badger Gnome Ubuntu to Dapper Xubuntu, and my fstab which worked fine under Badger now fails with some very esoteric error messages.

I thought I'd check that Xubuntu supports what I want to do. I did install samba using apt-get btw.

The fstab reads:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#//Dell/musicshare       /media/musicshare   smbfs   rw,uid=100,gid=1000,credentials=/root/.smbcredentials    0   0
#//Dell/p2p /media/p2p smbfs rw,uid=1000,gid=100,credentials=/root/.smbcredentials    0   0
#//Vaio/Y /media/Y smbfs rw,uid=1000,gid=100,credentials=/root/.smbcredentials    0   0
#//Vaio/Data /media/Data smbfs rw,uid=1000,gid=100,credentials=/root/.smbcredentials    0   0
//Vaio/AnnDocs /media/AnnDocs smbfs rw,uid=100,gid=1000,credentials=/root/.smbcredentials    0   0
#//Dell/musicshare  /media/musicshare  smbfs  -o guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0


The command [italic]sudo mount -a[/italic] reports:

> 
[mntent]: line 14 in /etc/fstab is bad
mount: wrong fs type, bad option, bad superblock on //Vaio/AnnDocs,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I then run [italic]sudo dmesg | tail[/italic]
and get:

> 
[4311465.509000] smbfs: mount_data version 1029990773 is not supported


The fstab worked fine on the same shares/machines but with Ubuntu Bagder (It also works fine on my Mandriva 2006.0 box, and my XP boxes mount the same share easily (AnnDocs is on a Mandriva Samba server)

Any ideas?

---

### Post by gerbman on 2006-06-17
[QUOTE=satbunny]Before I bore you all, does Xubuntu support mounting external samba shared drives using fstab and smbfs?

I moved my laptop from Badger Gnome Ubuntu to Dapper Xubuntu, and my fstab which worked fine under Badger now fails with some very esoteric error messages.

I thought I'd check that Xubuntu supports what I want to do. I did install samba using apt-get btw.

The fstab reads:



The command [italic]sudo mount -a[/italic] reports:



I then run [italic]sudo dmesg | tail[/italic]
and get:



The fstab worked fine on the same shares/machines but with Ubuntu Bagder (It also works fine on my Mandriva 2006.0 box, and my XP boxes mount the same share easily (AnnDocs is on a Mandriva Samba server)

Any ideas?[/QUOTE]Do you have the smbfs package installed?

---

### Post by satbunny on 2006-06-20
Ah ha! I'll check.

---

### Post by satbunny on 2006-06-21
That was it! Thanks, it all works fine now.

---

### Post by gerbman on 2006-06-21
[QUOTE=satbunny]That was it! Thanks, it all works fine now.[/QUOTE]Cool. You're welcome :)

---

