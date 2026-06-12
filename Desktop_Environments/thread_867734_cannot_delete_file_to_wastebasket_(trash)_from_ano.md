---
title: "cannot delete file to wastebasket (trash) from another partition"
date: 2008-07-23
forum: Desktop Environments
---

### Post by Gatemaze on 2008-07-23
Hi,

I am using 8.04 Heron.

I have a vfat (fat32) partition from which whenever I am trying to delete a file in Nautilus it comes a message saying:
"Cannot move file to the Deleted Items folder, do you want to delete permanently?"
"The file name-of-file cannot be moved to the wastebasket."

Now if I try to delete a file in Nautilus using root, the Trash folder is created just fine.

As such I created the trash folder manually:
```

drwxrwx---  4 root plugdev   16384 2008-07-23 02:11 .Trash-1001

```

and also in it there are:
```

drwxrwx---  2 root plugdev 16384 2008-07-23 02:19 files
drwxrwx---  2 root plugdev 16384 2008-07-23 02:19 info

```

And yes, the user is a member of the group plugdev.

The entry of the partition in the fstab file is:
```

UUID=xxxxx  /fat32          vfat    utf8,umask=007,gid=46 0       1

```

Any help? Thanks

---

### Post by Potatoj316 on 2008-07-23
where is the trash that is created when you delete files as root?

---

### Post by Gatemaze on 2008-07-23
on the same partition that the file existed... a similar folder should have been created for a normal user that belongs on the plugdev group, shouldn be?

---

### Post by Potatoj316 on 2008-07-23
It sounds like you dont have write permission for that disk but that dosent make sense, try this command
```
sudo chmod a+w MOUNTPOINT
```
where MOUNTPOINT is the root of the drive that is problematic

---

### Post by Gatemaze on 2008-07-23
cheers for the suggestion potato but the root mountpoint has exactly the same ownerships and permissions and i can write or delete pretty much anything i want, except that the deleted things don't go to the deleted items folder...

---

### Post by ACMiller on 2008-07-23
Gatemaze, I have exactly the same problem, none of my vfat partitions delete to trash, unless I'm working as root. I've tried creating trash folders manually, similarly to how you did, but I still get the same nautilus dialog telling me that the file cannot be moved to deleted items. 

I've reached a bit of a dead end, fortunately it's not a major problem. I'm interested to see what anyone's suggestions are.

---

