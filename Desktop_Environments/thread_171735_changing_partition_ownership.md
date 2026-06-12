---
title: "changing partition ownership"
date: 2006-05-07
forum: Desktop Environments
---

### Post by jerrybee on 2006-05-07
The books say that one can use " sudo chown <username> <filename>" to change ownership of a file.  I assume that a partitionname would qualify for <filename>, such as /media/hdb6 or /dev/hdb6.  But it just flat doesn't work.  I've even tried it as root and got the same "permission denied" message.  Also tried unmounting the partition and re-mounting it -- same story.  
    This is a multi-boot system which includes the Windows partitions that were there before I started installing various Linux distros.
    As a Linux newbie, this is very frustrating.  Surely there's a way to change ownership of the Windows partitions so that I can at least write to them from Linux.
    Some patient assistance would be appreciated.

---

### Post by ruzle0 on 2006-05-07
if you want the partition mounted when the computer boots you need to put lines in the file
/etc/fstab
this can be edited with by
sudo gedit /etc/fstab
in there you put the options you want e.g
```
/dev/hdb6 /media/hdb6 vfat umask=000 0 0
or
/dev/hdb6 /media/hdb6 ntfs umask=0222 0 0
```

the first mounts a vfat partition to the hdb6 directory in media and allows everyone to read/write/execute, and the second mounts an ntfs partition as read only.
you can also specify the owner and the group of the partition at mount time with uid=# and gid=# respectively [where # is the number of the user]
eg
```
/dev/hdb6 /media/hdb6 vfat uid=0,gid=1000,umask=0007 0 0
```
so this makes the owner root and group 1000 [thats me on my system] and the umask gives owner and group full access and others no access.
if you are mounting from the command line you must use sudo but the -o option lets you specify the same options above.
if you tell me exactly what you want i'll help you with the commands.

edit: if you want to write to a windows partition make sure its fat as writing to ntfs from linux can ruin it, reading is fine [hence the umask=0222 option to make it read only]. on my computer i have a fat partition that both windows and linux can share

---

### Post by jerrybee on 2006-05-07
Thanks -- I'm off to give it a try (editing fstab, that is).  But I still don't understand why I can't do the ownership-change-thing after the box has booted, I've logged in, and am "doing stuff".
    I really appreciate your taking time to answer my problem.  I now have 6 Linux distros installed on this box, along with Win2000 and MS-DOS.  My computer-friend thinks I have a masochistic streak in me, wanting to hurt myself so much !  Right now I just want to try several different distros to see which one "clicks" with me, and then I'll concentrate on using and learning that one and forget about the rest.  Am using OSL-2000 to handle the multi-boot and I still can't get Debian to use it -- have to use a boot floppy.
    I fear for my sanity through all this.
                   Jerry

---

### Post by ruzle0 on 2006-05-07
you can change after you have booted.
if you mounted at boot time through fstab you have to unmount first
sudo umount /media/hdb6
then you can mount from the commandline 
sudo mount /dev/hdb6 -tvfat -ouid=xxx,gid=xxx,umask=xxxx /media/hdb6
-t filesytem type
-o options seperated by ,

see man mount for the options available for different filesystems

---

