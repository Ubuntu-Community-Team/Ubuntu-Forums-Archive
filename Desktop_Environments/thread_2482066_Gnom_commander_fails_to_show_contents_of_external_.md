---
title: "Gnom commander fails to show contents of external HDD"
date: 2022-12-18
forum: Desktop Environments
---

### Post by py-ohayo on 2022-12-18
Hello,

Is NTFS, FAT32 are supported by gnome-commander 1.14.2 ?
When I select an external drive, the content doesn't change, it still display content of internal HDD.
Any comments ?
Thanks.
P.S. here is screenshot on what happens: the external HDD **DOC_1** is selected, but the content remains internal HDD
[https://i.postimg.cc/CLhcHP34/aaa.png](https://i.postimg.cc/CLhcHP34/aaa.png)

---

### Post by ActionParsnip on 2022-12-20
The kernel manages the file system. If the NTFS is mounted then you can simply access the data via the mount point used.

---

### Post by py-ohayo on 2022-12-23
NTFS mounted.
I can see external HDD with other managers: "Files" and "Double Commander", but not with "Gnom commander"

---

