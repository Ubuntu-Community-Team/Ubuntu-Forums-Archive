---
title: "Cannot write to external harddisk"
date: 2009-06-07
forum: Desktop Environments
---

### Post by skatebiker on 2009-06-07
Using a WD Passport external harddisk I make regularly backups to it.
But during the backup stage the HD allows writing some folders and files and during the operation

cp -auv ~/Documents/f_etc/* /media/WDPASSPORT/backups/klaas/f_etc

it issues a message 'cannot copy to read only file system'


When I issue a chown on the external HD 

chown -Rv klaas:klaas WinOnCD/

it issues 

chown: changing ownership of `WinOnCD/cdda_9': Operation not permitted
failed to change ownership of `WinOnCD/cdda_9' to klaas:klaas

However when I issue a chmod

chmod -R 755 WinOnCD/

it works fine.

The HD has a FAT32 file system.

When I mount the HD to a Windows XP VMware session within Kubuntu everything works fine.


Another problem: whe I issue fdisk -l
I get the message 
Cannot open /dev/sda
Cannot open /dev/sdb

However except for the external HD copying everything works fine.

What is going on ?

---

### Post by Boondoklife on 2009-06-07
Can you plug in the drive and post the output of ```
mount
``` also could you post the output of ```
 ls -l /media/WDPASSPORT
```

---

