---
title: "Problems with trying to remove partition-has keys by the name"
date: 2010-01-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by babitweety06 on 2010-01-04
I am trying to reinstall ubuntu on my computer. I am now trying to create partition but I accidently created one that I do not want. Next to the name of the partition is a set of keys so I am guessing that it is locked. How do I remove that.

---

### Post by wilee-nilee on 2010-01-04
> **babitweety06 said:**
> I am trying to reinstall ubuntu on my computer. I am now trying to create partition but I accidently created one that I do not want. Next to the name of the partition is a set of keys so I am guessing that it is locked. How do I remove that.

This post makes little sense, give a better description and what your using to partition.

---

### Post by babitweety06 on 2010-01-04
I am using gparted.

---

### Post by babitweety06 on 2010-01-04
I am really in need of help. I do not know exactly what happened to my computer. I just need help trying to install ubuntu again. So i have been trying to install ubuntu and i get to the partition page and its blank so i quit the installation and try to create a partition through gparted and i get stuck. I have this lock on this one partition. Its a key and i can not unmount because there is a message saying the server is busy.

---

### Post by wilee-nilee on 2010-01-04
A set of keys next to the partition is confusing. I have never had a encrypted partition, is this what has happened and can you post a screenshot of what your talking about and a screenshot of gparted from the live CD.

---

### Post by chewearn on 2010-01-04
I believe the "key" icon indicates the partition is mounted.  Right click on the partition and select unmount.

---

### Post by babitweety06 on 2010-01-05
i right clicked and it says that it is busy.

---

### Post by chewearn on 2010-01-05
> **babitweety06 said:**
> i right clicked and it says that it is busy.

That means the partition is in use.  You need to close everything that is using it.  If it's the swap, right-click and select "swapoff".

If unsure, post a screenshot and we might know something.

---

### Post by babitweety06 on 2010-01-05
here are the shots

---

### Post by chewearn on 2010-01-05
Run this command and post the output:
```

lsof /cdrom

```

---

### Post by babitweety06 on 2010-01-05
heres what it said

ubuntu@ubuntu:~$ lsof /cdrom
lsof: WARNING: can't stat() vfat file system /cdrom
      Output information may be incomplete.
lsof: WARNING: can't stat() vfat file system /casper-rw-backing
      Output information may be incomplete.
lsof: WARNING: can't stat() ext2 file system /cow
      Output information may be incomplete.
lsof: status error on /cdrom: No such file or directory
lsof 4.81
 latest revision: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/)
 latest FAQ: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ)
 latest man page: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man)
 usage: [-?abhlnNoOPRtUvVX] [+|-c c] [+|-d s] [+D D] [+|-f[gG]]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]] [-p s]
[+|-r [t]] [-s [p:s]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.

---

### Post by chewearn on 2010-01-05
I am a bit stumped.  By any chance, you are booting ubuntu off a USB key, and that partition you are trying to delete is said USB key?

How about output of:
```

mount

```

---

### Post by babitweety06 on 2010-01-05
I am trying to reinstall ubuntu on my laptop. When I would turn on my computer the meter that tells the progress of the load up will freeze for two min and then a screen will come up basically saying that there was no operating system. So someone on here recommended that I reinstall the ubuntu software on the laptop. So from a windows computer I downloaded the software online. The file that they offer is ISO file. So inorder to have this put into a USB you have to change the file so windows can read it. And thats what i did using pendrivelinx. Now i have the software on the USB and trying to get it properly installed on the laptop. When I get to the partition faze of the installment I have no options to choose from and I can not even create a new partition. So i quit installation and tried to create a partition from the gparted. So basically i just need help with the partition part of the installation. I have a basic dell mini 9, no upgrades.

---

### Post by chewearn on 2010-01-05
It appeared that the /dev/sda is actually the USB drive itself where you booted and is running Live Ubuntu from.  That's why you can't unmount or erase it.

In the top right corner of GParted, there is a drop down list.  See if you can find the actual laptop drive there.

If you are having difficulty, run the following commands, so that I can understand the drive configurations in your laptop:

```

mount

```and
```

sudo fdisk -l

```

---

### Post by babitweety06 on 2010-01-05
now the computer is not even reading the USB.

---

