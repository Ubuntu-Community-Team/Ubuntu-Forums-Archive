---
title: "How to remove files"
date: 2009-06-04
forum: General Help
---

### Post by ismialexis on 2009-06-04
When I try to delete the files in disk usage analyzer it says "Could not find a Trash folder on this system"
Pleas help, it says 100% of the disk space is being used.

---

### Post by colau on 2009-06-04
> **ismialexis said:**
> When I try to delete the files in disk usage analyzer it says "Could not find a Trash folder on this system"
Pleas help, it says 100% of the disk space is being used.
Can you post the result? 
```

sudo fdisk -l
sudo df -h

```

---

### Post by SuperSonic4 on 2009-06-04
You can also use rm to bypass trash when it comes to removing things but be **very** careful when using it

---

### Post by colau on 2009-06-04
> **ismialexis said:**
> When I try to delete the files in disk usage analyzer it says "Could not find a Trash folder on this system"
Pleas help, it says 100% of the disk space is being used.
To delete a file
```

rm -f filename

```
To remove a directory
```

rm -rf directory

```

---

### Post by ismialexis on 2009-06-04
alexis@alexis:~$ sudo fdisk -l

Disk /dev/sda: 3791 MB, 3791241216 bytes
255 heads, 63 sectors/track, 460 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           3       24066   de  Dell Utility
/dev/sda2   *           4         460     3670852+  83  Linux
alexis@alexis:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.5G  3.4G     0 100% /
varrun                247M  104K  247M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M   36K  247M   1% /dev
devshm                247M     0  247M   0% /dev/shm
lrm                   247M  1.9M  245M   1% /lib/modules/2.6.24-24-lpia/volatile
overflow              1.0M   24K 1000K   3% /tmp

---

### Post by ismialexis on 2009-06-04
> **colau said:**
> To delete a file
```

rm -f filename

```
To remove a directory
```

rm -rf directory

```

alexis@alexis:~$ sudo rm -r firefox
rm: cannot remove `firefox': No such file or directory

---

### Post by colau on 2009-06-04
> **ismialexis said:**
> alexis@alexis:~$ sudo rm -r firefox
rm: cannot remove `firefox': No such file or directory
It is
```

rm -f firefox

```

---

### Post by ismialexis on 2009-06-04
> **colau said:**
> It is
```

rm -f firefox

```

alexis@alexis:~$ rm -f firefox
alexis@alexis:~$

---

### Post by SuperSonic4 on 2009-06-04
> **ismialexis said:**
> alexis@alexis:~$ rm -f firefox
alexis@alexis:~$

It will only give an output if you pass the -v flag such as ```
rm -fv firefox
```

Since there is no output you may assume it was successful, if you want to test it type *ls* into a terminal and firefox should not appear

---

### Post by VMC on 2009-06-04
If you want to remove Firefox. A better way is to use Application > Add/Remove. Then select Firefox for removal.

---

### Post by _Purple_ on 2009-06-04
> **ismialexis said:**
> When I try to delete the files in disk usage analyzer it says "Could not find a Trash folder on this system"
Pleas help, it says 100% of the disk space is being used.

If it says disk is full, check this thread 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

