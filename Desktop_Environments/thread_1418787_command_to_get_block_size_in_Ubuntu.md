---
title: "command to get block size in Ubuntu?"
date: 2010-03-01
forum: Desktop Environments
---

### Post by vksingh on 2010-03-01
Hi,

In a book, I read tha **cmchk** command is used to get the disk block size. But in Ubuntu, it is not allowed as command is not available.Can some body tell me what is its equivalent in Ubuntu.

Thanks,

Vivek

---

### Post by Kakers on 2010-03-01
You mean ?

```
sudo fdisk -l
```

---

### Post by fallenshadow on 2010-03-01
Try this really simple one in the terminal:

```

df

```

---

### Post by Pritamsng on 2010-03-01
i think the command is dumpe2fs ..
check the link for more info ..
[http://linuximagination.blogspot.com/2010/03/what-is-maximum-size-single-file-can-be.html](http://linuximagination.blogspot.com/2010/03/what-is-maximum-size-single-file-can-be.html)

---

### Post by tlroche on 2011-08-08
> **vksingh said:**
> [How] to get the disk [blocksize] in Ubuntu.

> **Kakers said:**
> ```
sudo fdisk -l
```

On my lucid box I get, e.g.,

```
  Disk /dev/sda: 250.1 GB, 250059350016 bytes
  255 heads, 63 sectors/track, 30401 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
* I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0x0009c48f

     Device Boot      Start         End      Blocks   Id  System
  /dev/sda1   *           1        1824    14648437+  83  Linux
  /dev/sda2            1824       30402   229550146    5  Extended
  /dev/sda5            1824        2294     3770507   82  Linux swap / Solaris
  /dev/sda6            2294       29618   219485368   83  Linux
```

Does "I/O size" == filesystem blocksize? Apparently not, since

> **fallenshadow said:**
> Try this[:]```
df
```

```

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             14418532  11754604   1931508  86% /
...
```

which seems to indicate that blocksize=1k, no? But

> **Pritamsng said:**
> i think the command is dumpe2fs

and that seems most definitive, for a filesystem (again, not a device):

```
tlroche@tlrPanP5:~$ sudo dumpe2fs /dev/sda1 | fgrep -e 'Block size'
dumpe2fs 1.41.11 (14-Mar-2010)
Block size:               4096

```

---

