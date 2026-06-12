---
title: "commnad to get file size in MB"
date: 2010-06-20
forum: Desktop Environments
---

### Post by vksingh on 2010-06-20
Hi,

Is there any command to get file size in MB in Ubuntu?


Thanks,


Vivek:confused:

---

### Post by karash on 2010-06-20
This probably isn't in the correct section, but from the command line, you could try:

ls -sh filename

The -s is size, the -h is human readable.

---

### Post by clrg on 2010-06-20
Most commonly used options of ls:

ls -lh --> Permissions and file size
ls -lah --> Permissions and file size on all files
ls -ltrh --> Permissions and file size, sorted on access time (newest is last)
ls -ld --> Permissions, only directories

---

### Post by hictio on 2010-06-20
And, if you want to get not only file, but directory sizes as well, you have to execute:

```

du -sh directory ENTER

```

---

