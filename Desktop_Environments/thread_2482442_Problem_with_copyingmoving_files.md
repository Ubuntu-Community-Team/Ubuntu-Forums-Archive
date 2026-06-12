---
title: "Problem with copying/moving files"
date: 2022-12-31
forum: Desktop Environments
---

### Post by py-ohayo on 2022-12-31
Hello,

I ran into problems when trying to copy files from one external hard drive to another.
I've tried Double Commander as well as 'cp' command in Ubuntu terminal.
The problem is the same in both cases: the copy/move operation hangs on the 2nd...3rd file.

Other details:
Ubuntu 22.04
files: video 2 ... 4 Gb

Any suggestions ?
Thanks

---

### Post by ajgreeny on 2022-12-31
Could be that the destination filesystem is fat32 which has a maximum filesize limit of 4Gb.

---

### Post by py-ohayo on 2022-12-31
No, the two external HDDs have the NTFS file system.

---

### Post by py-ohayo on 2022-12-31
Finally I decided to do this operation on a Windows computer and it works without problem

---

### Post by ajgreeny on 2022-12-31
Perhaps this was all related to permissions which are of huge importance in Linux but generally mean nothing in Windows.

However, please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It can be a great help to other users searching the forum.

---

