---
title: "Samba problems"
date: 2006-08-01
forum: Desktop Environments
---

### Post by oofnik on 2006-08-01
Hello, I'm having a problem with some samba shares. I have four shares - two of which work. One is my home directory, one is my printer, and the other two are folders on an external hard drive. The external drive seems to have some permissions set that I can't figure out. They are not allowing samba users (even me, locally) to access the shares. Here's what (the relevant part of) /etc/mtab looks like:
```
/dev/sdg1 /media/EXT1 vfat rw,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sdg2 /media/EXT2 vfat rw,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

```
I've also attached my smb.conf, if that helps. So if anyone would take the time to help me figure this out I would appreciate it :grin:

---

### Post by Zimmer on 2006-08-01
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Any info here that will help? 
I don't have experience of using external drives , but have used these instructions (and others!) to access Windows shares on a networked computer.

One thing I notice is the masking parameter in your mtab is 077, is that correct?(not sure on the reasons for that, but I am trying to put a quick reply  so I haven't investigated fully)  The masking parameters in the link above use 777 for allowing rw access for regular users.  Could that be part of the solution to this problem..
Regards

EDIT...
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by oofnik on 2006-08-02
Thanks for replying Zimmer.
All of the parameters in mtab are invoked automatically when the drive is plugged in. If I unmount the two partitions, and remount them with pmount, the same parameters are used. I'm pretty sure that either the uid, gid or umask setting is keeping samba access working on the shares, but I don't have a clue how to change these mount settings. I really would like to figure out how to get it to mount automatically correctly. I'm not very familiar with the mechanism by which mass storage is automatically mounted, so if someone could point me in the direction where I can read about that,  that would be nice 8-)

---

### Post by Zimmer on 2006-08-04
Have you tried mounting the folders on the drives using fstab file 
as per
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)
I quote from there(with a change to reflect one of your drives..)
> 
 How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write

    * Read #General Notes
    * Read #How to list partition tables 

    e.g. Assumed that /dev/sdg1 is the location of Windows partition (FAT) 
    Local mount folder: /media/windows 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

    * Append the following line at the end of file 

/dev/sdg1    /media/windows vfat  iocharset=utf8,umask=000  0    0

    * Save the edited file
Not sure if that applies to external drives, though.

---

### Post by oofnik on 2006-08-07
Yeah, I have another partition mounted that way. I tried to put an entry in fstab for the two external partitions with umask=000 and everything worked with samba, as I expected. I'm just trying to figure out how I can get the drives to automount when plugged in like they normally would without the fstab entries. Something is preventing them from automounting correctly and I have to mount them manually when I plug it in. Thanks so far though.

---

