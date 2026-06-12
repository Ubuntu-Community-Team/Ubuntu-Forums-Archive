---
title: "Cannot figure out how to get autofs and NFS to allow me to view mount points"
date: 2009-04-28
forum: General Help
---

### Post by Lucid Smog on 2009-04-28
I have a server set up like so in /etc/exports:

```

/home    192.168.10.0/24(rw,sync,no_subtree_check)
# Must manually enumerate mounted filesystems on the local machine
/media/media    192.168.10.0/24(rw,sync,no_subtree_check)
/media/Backup    192.168.10.0/24(rw,sync,no_subtree_check)
/media    192.168.10.0/24(rw,sync,no_subtree_check)
/opt    192.168.10.0/24(rw,sync,no_subtree_check)

```Originally I only had the /media line and not the enumerated folders.
On the server /media/media is another hard disk and is mounted.  /media/Backup is an intermittently connected NTFS formatted USB drive.

On the client I have this for /etc/auto.master:
```

/mnt/nfs/cesium /etc/auto.cesium -rw,soft,intr

```And in /etc/auto.cesium:
```

*    cesium.lan:/&

```On the client machine I can successfully cd /mnt/nfs/cesium/media and I see the mountpoint and the directories within it, but the ls -l looks like this:
```

total 12
drwx------ 2 root root 4096 2009-04-22 20:56 Backup
lrwxrwxrwx 1 root root    6 2009-04-16 16:31 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-04-16 16:31 cdrom0
drwx------ 2 root root 4096 2009-04-22 20:58 media

```Whereas on the server ls -l /media looks like this:
```

total 8
drwxrwxrwx 1 root root  4096 2009-04-16 15:42 Backup
lrwxrwxrwx 1 root root     6 2009-04-16 16:31 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2009-04-16 16:31 cdrom0
drwxrwxr-x 3 root users    8 2009-04-22 20:59 media

```I have a suspicion that NFS will not "export" a mount point under the main export tree.  That's why I specifically enumerated the mount points I care about.  But I don't know how to make autofs use this information and continue to keep the /home and /opt autofs mountpoints.  As it is I still can't cd into media/Backup or media/media on the client machine.

Any ideas?

---

### Post by Lucid Smog on 2009-04-29
For the benefit of others, I figured this out on my own.

You have to use the 'crossmnt' option in the /etc/exports file on the server where you would like the NFS mount to cross mounted volumes.  'man 5 exports' has all the gory details, but it still took a while to find that option and decide that it was supposed to do what I wanted.

---

