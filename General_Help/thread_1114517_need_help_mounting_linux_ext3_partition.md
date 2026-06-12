---
title: "need help mounting linux ext3 partition"
date: 2009-04-02
forum: General Help
---

### Post by drewm1732 on 2009-04-02
Hey everyone, I'm trying to mount a partition i created named sda3 which has a ext3 file system and I'm using Ubuntu 8.04. I'm an undergrad computer science major and have been using an Ubuntu system for a while but I realized that I don't really know much about the way a linux system works. Thats when I stumbled upon a site, and a book, called linux from scratch that guides you through building a lightweight linux system. I obviously got through partitioning the drive but when it comes to mounting the instructions say the commands are

_create a mount point and assign it the LSF variable:_

export LFS=/mnt/lfs

_create the mount point and mount the LFS file system:_

mkdir -pv $LFS
mount -v -t ext3 /dev/sda3 $LFS 

when i run the mkdir command it says there is a missing operand, does anyone know how the code should really be implemented.

---

### Post by drewm1732 on 2009-04-02
anyone?

---

### Post by ptn107 on 2009-04-02
Ditch the variables.  Do it straight.

```
$ sudo mkdir -p /mnt/lfs
$ sudo mount -t ext3 /dev/sda3 /mnt/lfs
```

---

### Post by drewm1732 on 2009-04-02
Thanks, that worked, i guess it was the $LFS variable throwing it off. Is there a way to create the variable path to the folder the way it wants though? It would be convenient because the rest of the book uses the $LFS variable. Thanks again for the help.

---

### Post by ptn107 on 2009-04-03
```
$ FOLDER=/mnt/lfs
$ sudo mkdir -p $FOLDER
$ sudo mount -t ext3 /dev/sda3 $FOLDER
```

---

