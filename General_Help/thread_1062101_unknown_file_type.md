---
title: "unknown file type?"
date: 2009-02-06
forum: General Help
---

### Post by adasilva on 2009-02-06
In the process of mounting a windows shared folder, I created a directory,
```
$ sudo mkdir /media/new_dir
```
However, it now seems that my system has no idea what it is. For example,
```
$ cd /media/new_dir
$ ls
ls: cannot open directory .: No such file or directory

```

When I try to list the items in /media, the line associated with new_dir is:
```
d?????????      ? ?    ?      ?           ?   new_dir

```

Does anyone know what could have possibly caused this to happen and what I can do about it?

Note: I have since successfully mounted the windows share using a different mount point, so I would ultimately like to delete this unecessary directory(or whatever it is...)

---

### Post by geraldm on 2009-02-07
# to remove it
sudo rmdir /media/new_dir

---

### Post by adasilva on 2009-02-09
I tried this, and it did not work. However, upon rebooting, the file type became known, and I was able to delete it.

---

