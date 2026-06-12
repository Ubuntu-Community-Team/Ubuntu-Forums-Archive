---
title: "can not delete file (directory not empty)"
date: 2009-03-09
forum: General Help
---

### Post by wangjiajun on 2009-03-09
I have some old folders in my flash drive. 

In ubuntu, I can not delete them. 

rm -rf, rmdir both say directory not empty, how can I get them deleted?

---

### Post by whoop on 2009-03-09
sudo rm -rf?
Also what filesystem is the flash drive using.

---

### Post by wangjiajun on 2009-03-09
It is NTFS, by the way. 

Sudo is not helping, I already tried that. 

Also I tried in Windows, Mac to remove them. Still no luck!

Does that means bad block in the hard drive? If so, how can I get around them?

Thanks!

> **whoop said:**
> sudo rm -rf?
Also what filesystem is the flash drive using.

---

### Post by whoop on 2009-03-09
If there is only junk left on the drive you could consider (re)formatting the drive. You might also what to change the filesystem to fat32 which will be more compatible with other (default) operating systems.

---

### Post by networm1230 on 2009-03-09
possible file delete fix go to the file that you are trying to delete. 

lift click in the file than go down to properties.than file permissions (owner). 

folder access and change to create and delete files. 

next go to file access and change to read and right. 

now try to delete the file. some files on Linux you must have root/sudo access to delete file. experiment with this file security fetchers. 

mack a folder on you desktop name it what ever you wont like (nigh+fire) for example. 

play around with it you con even put emblems on you files so that you know the contents of the files.

note: mack shore you are root/owner/user

---

