---
title: "file permissions not working"
date: 2006-02-19
forum: Desktop Environments
---

### Post by davedaveh on 2006-02-19
I have read other posts on this subject, and the question does not seem to get answered.  I am using 5.10 on a machine with  other fat32 partitions.  Why doesn't the chmod command take effect?

dave@davenew:~$ sudo chmod 777 /media/hda7
dave@davenew:~$ ls -l /media/hda7
total 128
drwxr-xr-x   4 root root  8192 2005-11-10 19:22 finale nortepad 2005
-rwxr-xr-x   1 root root 16918 2006-02-15 20:54 good address.ldif
drwxr-xr-x  24 root root  8192 2003-03-12 01:10 MyDocuments
drwxr-xr-x   2 root root  8192 2005-09-16 01:57 New Folder (2)
drwxr-xr-x   2 root root  8192 2005-09-18 06:28 Open
drwxr-xr-x  43 root root  8192 2003-03-12 01:09 other
-rwxr-xr-x   1 root root  8540 2006-02-15 20:56 personal address.ldif
drwxr-xr-x   2 root root  8192 2004-10-09 23:25 pmap2w
drwxr-xr-x   7 root root  8192 2004-09-27 00:39 Program Files
drwxr-xr-x   2 root root  8192 2003-08-22 02:26 recycled
-rwxr-xr-x   1 root root   284 2006-01-30 10:06 Shortcut (2) to MyDocuments.lnk
-rwxr-xr-x   1 root root   244 2006-01-27 22:01 Shortcut to MyDocuments.lnk
drwxr-xr-x   2 root root  8192 2006-02-09 22:25 WUTemp

This does work, though:
dave@davenew:~$ sudo chmod 777 /dev/hda7
dave@davenew:~$ ls -l /dev/hda7
brwxrwxrwx  1 root disk 3, 7 2006-02-19 05:14 /dev/hda7

I still cannot write to the fat32 drive.

---

### Post by bernardfrancois on 2006-02-19
I think your fat32 drive is mounted in a way that you must be root to write to it...
You can search the forum on 'howto mount vfat partition' or something like that.

---

### Post by Mr Frosti on 2006-02-19
Try a slight variation on your command:

```
sudo chmod -R 777 /media/hda7/*
```

If this doesn't resolve the issue, then try "chown" on the partition to your user and try the same command again without sudo.

---

### Post by claes on 2006-02-19
The chmod command is not recursive meaning if you chmod a directory you only chmod that directory not files or sub directory. If you want chmod to be recursive use chmod with the -R options.

The fat filesystem doesn't have support for posix acl (linux permissions).

If you want to have your fat filesystem with a different owner than root then you have to mount the filesystem with a different owner. In your /etc/fstab file add the mount options uid=1000 or gid=100, ex:

/dev/hda7  /media/hda7 vfat defaults,uid=1000,gid=100 0 0 

ls -ld /media/hda7
drwxr-xr-x 2 claes users 4096 2006-02-12 23:23 /media/hda7


Hope this wil help you.

Claes

---

### Post by aysiu on 2006-02-19
You can't chmod or chown a FAT partition. FAT doesn't support permissions.

You have to mount it properly. See the fourth link of my signature for details.

---

### Post by knalle on 2006-02-19
[QUOTE=davedaveh]I have read other posts on this subject, and the question does not seem to get answered.  I am using 5.10 on a machine with  other fat32 partitions.  Why doesn't the chmod command take effect?
I still cannot write to the fat32 drive.[/QUOTE]

because you havent supplied mount with permission arguments for vfatfs;

sudo mount -t vfat -o gid=1000,uid=1000,umask=002 /dev/disk /mount/point

---

