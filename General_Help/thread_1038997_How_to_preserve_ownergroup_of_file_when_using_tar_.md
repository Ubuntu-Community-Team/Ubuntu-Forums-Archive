---
title: "How to preserve owner/group of file when using tar and extract on other PC?"
date: 2009-01-14
forum: General Help
---

### Post by abcuser on 2009-01-14
Hi,
Using Ubuntu 8.10 I would like to tar directory and transfer files using FTP to other PC and untar files.

What I see is when using command: tar jcvf mynewfile.tar.gz2 mydirectory/
and after untar: tar jxvf mynewfile.tar.gz2 all files gets owner/group of this file instead of original owners/groups of this files.

How to tar the files to preserve owner/group of files after tar/untar?
Regards

---

### Post by bluefrog on 2009-01-14
tar with the user you want to preserve user.group and untar with sudo

---

### Post by abcuser on 2009-01-14
Hi,
the problem is I have many files in directory. One file has owner root, other user1, then user2 etc. Is there possible to preserve owner:group of files? I can preserve reard,write,execute, but what about ower:group?
Regards

---

### Post by bluefrog on 2009-02-26
if you use sudo to tar xf and if the users exists on your system then ownership will be preserved.

---

