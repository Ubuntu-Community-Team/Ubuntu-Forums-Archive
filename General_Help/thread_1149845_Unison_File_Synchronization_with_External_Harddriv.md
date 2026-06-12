---
title: "Unison File Synchronization with External Harddrive"
date: 2009-05-05
forum: General Help
---

### Post by selahlynch on 2009-05-05
I'm using Unison to synchronize documents on my laptop with my external harddrive.  I have problems copying files.

I get the following message.

```
potential facebook/OLD/IMG_1344.JPG
Failed to set permissions of file /media/SimpleDrive/My Pictures/potential facebook/OLD/.unison.IMG_1344.JPG.9461147d6f5bff559204493a8d752729.unison.tmp to rwx------: the permissions was set to rwxrwxrwx instead. The filesystem probably does not support all permission bits. You should probably set the "perms" option to 0o1700 (or to 0 if you don't need to synchronize permissions).

```

---

### Post by dabang on 2009-05-05
I don't know about unison, but I guess your external drive is fat32 formatted? Linux can't set standard Unix file permissions on fat32/ntfs partitions and that's why you receive the warning (not actually an error).
(By the way, did you check "rsync"?)

---

### Post by wormbuntu on 2013-02-02
I get the same problem. Both partitions are NTFS. I don't even know where the "perms" option would be.

Any pointers gratefully received!

---

### Post by 2F4U on 2013-02-03
Look into your home folder. There should be a directory ".unison" (hidden folder). The profiles which unison uses end on ".prf". The perms option goes into the profile file.

---

### Post by sudodus on 2013-02-03
I use Unison too. And I have formatted the external drives with ext file systems (the most modern one is ext4, but you can use ext3 as well).

I suggest that you use an ext file system when you synchronize with Unison. This way you will not lose the permissions settings. It is particularly important if you sync system files of linux (in the root partition /, /home and or /boot). If it is 'only' personal files: documents, pictures etc, it is not necessary to get the permissions sync'ed.

---

### Post by sudodus on 2013-02-03
> **wormbuntu said:**
> I get the same problem. Both partitions are NTFS. I don't even know where the "perms" option would be.

Any pointers gratefully received!
Linux can not manage the permissions individually for each file or directory on Windows file systems (FAT and NTFS). The permissions are set when the partition is mounted, so to change it you need to unmount and re-mount with proper permissions.

---

### Post by oldos2er on 2013-02-03
wormbuntu: If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

