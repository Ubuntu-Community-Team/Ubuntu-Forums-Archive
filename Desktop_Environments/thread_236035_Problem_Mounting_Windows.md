---
title: "Problem Mounting Windows"
date: 2006-08-14
forum: Desktop Environments
---

### Post by buddy_krish on 2006-08-14
Hi,

Followed all the methods in [Wiki]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only") and [Documentation]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")   but still unable to Mount my Windows Drives....  :( 

==========
krish@vampiro:~$ for i in /dev/[hs]d[a-z]; do sudo fdisk -l $i; done
Password:

Disk /dev/sda: 160.0 GB, 1krish@vampiro:~$ for i in /dev/[hs]d[a-z]; do sudo fdisk -l $i; done
Password:

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40965718+   7  HPFS/NTFS
/dev/sda2            5101       17923   103000747+   f  W95 Ext'd (LBA)
/dev/sda3           17924       19457    12321855   83  Linux
/dev/sda5            5101       10200    40965718+   7  HPFS/NTFS
/dev/sda6           10201       12751    20490876    7  HPFS/NTFS
/dev/sda7           12752       15302    20490876    7  HPFS/NTFS
/dev/sda8           17854       17923      562243+  82  Linux swap / Solaris
/dev/sda9           15303       17853    20490876   83  Linux

Partition table entries are not in disk order
60040803840 bytes
===============================================================

This is the error message I get when I try to access from Media folder

The folder contents could not be displayed.

You do not have necessary permissions.....  :-(

Help me plz.....

---

### Post by baka_rob on 2006-08-14
What are the permissions on the folder(s) in question?

If you right-click on the folder (assuming Gnome is being used), and click on "Properties" and then click on the "Permissions" tab, it should show you information about 1) which user owns the folder. 2) which group has group-access to the folder and 3) what the permissions are for the owner, the group, and 'everyone else' as far as read/write/execute permissions go.

Alternatively, running the following in the console should give you similar output:

```
ls -ld /media
```

And:

```
ls -ld /media/windows
```

If your user needs to be in a certain group to access the folder(s) (note: I have only skimmed over the documentation so far, but it looks like they are using an 'ntfs' group), you may want to try adding your user to the group.  This can be found in the following menu:

```
System -> Administration -> Users and Groups
```

(Note: you will be prompted for the root password)

If you want to make a set of folders fully accessable to ALL users, which may be an insecure workaround to this issue, try the following, in a console:

```
sudo chmod -R 777 /media
```

(Note: you may be prompted for the root password)

If running the chmod command above does the trick, just note that it allows ALL users of the computer full access to the folder(s) in question, but on the positive side no permissions should stop you from navigating around. :p  Use with care!

Good luck!

---

### Post by buddy_krish on 2006-08-14
Worked....Thank You !!!!

---

