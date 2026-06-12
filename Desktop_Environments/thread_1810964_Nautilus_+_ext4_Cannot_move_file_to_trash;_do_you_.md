---
title: "Nautilus + ext4: Cannot move file to trash; do you want to delete immediately?"
date: 2011-07-24
forum: Desktop Environments
---

### Post by DrJohn999 on 2011-07-24
This is Natty x64 installed by in-place upgrade from 10.10 desktop. I only noticed this problem today. The system has 4 hdds. /dev/sda and /dev/sdc are a RAID 1 pair mounted at root. /dev/sdb is ext3 mounted on /home and not encrypted. /dev/sdd is a 1 GiB ext4 drive with a single partition occupying the entire drive, mounted to /media/shared0, also not encrypted. Sdd is a Samba share; deleting the associated share & restarting smbd did not affect this problem.
/etc/fstab:
```
proc            /proc           proc    defaults        0       0
# / was on /dev/md0 during installation
UUID=a2b43bbb-d04b-44e9-9794-8b00a99536cb /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=46fe1c5c-f77f-4964-8eb0-4b5651d748ac /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=0983f0e4-c3c4-4472-a37a-c9e5a70968f6 none            swap    sw              0       0
# swap was on /dev/sdc5 during installation
UUID=80f61635-f5f8-4604-b08c-2face19756a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# 1 GiB mediadrive volume installed 03-26-2011
UUID=7e4d0a14-8aa0-4ae6-96f4-0b43ef16cc37	/media/shared0  ext4 defaults,user      0       2

```
The problem: Delete from the /media/shared0 mount using Nautilus used to go to trashcan, but now I get "Cannot move file to trash, do you want to delete immediately?" The problem only appeared after Jun 19, 2011 which is the most recent date for files from this drive now in the trash. Today is the first time since then I've deleted anything there via Nautilus. 
/var/log/dpkg.log shows several changes to Nautilus on Jul-03:
```
2011-07-03 10:58:02 status installed libnautilus-extension1 1:2.32.2.1-0ubuntu13
2011-07-03 10:58:02 status installed nautilus-data 1:2.32.2.1-0ubuntu13
2011-07-03 10:58:11 status installed nautilus-sendto-empathy 2.34.0-0ubuntu3.1
2011-07-03 11:02:04 status installed nautilus 1:2.32.2.1-0ubuntu13
2011-07-03 11:03:38 status installed nautilus-share 0.7.2-14ubuntu1

```
and on Jul-13:
```
2011-07-13 20:44:27 status installed nautilus-sendto 2.32.0-0ubuntu1.1

```
This is similar to [Launchpad Bug #799474]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/799474") but not exactly so.

Has anyone else seen this behavior on drives mounted this way?

---

### Post by DrJohn999 on 2011-08-28
Solved: share's mount point was owned by root with read-only permission for groups, any, thus Nautilus was unable to create /media/mountpoint/.Trash-<uid> folder. 

Solution: Changed permissions on the mount point (/media/shared0 in this case):
```
~$ sudo chmod 777 /media/shared0
```
Then created / deleted a file in Nautilus. /media/shared0/.Trash-1000 is created. Deleted file now appears in Nautilus Trash, restore works too.
If other user accts access the share, then delete a file in Nautilus from login sessions for each user, to create the appropriate mountpoint/.Trash-<uid> hidden folder.

Last step, change permissions back to original 755
```
~$ sudo chmod 755 /media/shared0
```

---

