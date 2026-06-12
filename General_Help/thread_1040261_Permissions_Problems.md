---
title: "Permissions Problems"
date: 2009-01-15
forum: General Help
---

### Post by c1rcu17 on 2009-01-15
I seem to be having some permissions problems with my external hard drive. It seems that anything I put into the Video folder, seems to be lost to the abyss. I have a sneaky suspicion that my permissions aren't set correctly. The hard drive is formatted in 1 partition as NTFS. I use NTFS because I dual boot and virtualize Window$, and need to get at my external there as well.

When I cd into the folder, and use ls, I get, 
```
ls: reading directory .: Input/output error
```

ls -lh
```
total 0
```

df -h
```
/dev/sdb1             699G  193G  506G  28% /media/External
```
This should be the correct amount of space as if my videos were all there.

mount
```
/dev/sdb1 on /media/External type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```

the ls -lha of the whole drive gives me,
```
drwxrwxrwx 1 root root  12K 2009-01-15 11:01 .
drwxr-xr-x 4 root root 4.0K 2009-01-15 11:17 ..
drwxrwxrwx 1 root root 4.0K 2009-01-15 11:01 Backup
drwxrwxrwx 1 root root 4.0K 2009-01-10 00:11 CD_Images
drwxrwxrwx 1 root root 8.0K 2009-01-15 11:01 Software
drwxrwxrwx 1 root root    0 2008-10-21 15:25 System Volume Information
drwxrwxrwx 1 root root  16K 2009-01-15 11:06 Video
```

dmesg didn't seem to show anything abnormal (maybe I missed it).When I drop anything into the folder, it just disappears. All the other folders on the drive seem to be working fine. Just Video...
Any ideas?

---

### Post by matey3 on 2009-01-15
Umm, I wonder if you'd use chmod -R on that video folder?
I cant think of any other reason except the file are somehow hidden?
did u look inside of video/ with -a ?
and I guess there are always the attribs and then there are rights on every file/folder.

---

### Post by hyper_ch on 2009-01-15
tried to access that one from windows again?

---

### Post by c1rcu17 on 2009-01-15
ls -a gives me,
> ls: reading directory .: Input/output error

Again, I just have a sneaky suspicion that this is a permissions problem. I might be wrong in that assessment.

---

### Post by c1rcu17 on 2009-01-15
Ok, I just booted into windows, ran a chkdisk which crashed (<3 u windows), booted back into Ubuntu, and now I can see my videos. I have no idea why, but it seems to be back to normal. (hopefully)

---

### Post by hyper_ch on 2009-01-15
very likely unproper shutdown of the ntfs volume

---

