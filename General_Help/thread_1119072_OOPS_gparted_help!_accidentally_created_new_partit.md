---
title: "OOPS gparted help! accidentally created new partition table!"
date: 2009-04-07
forum: General Help
---

### Post by Hellstudios on 2009-04-07
I ran my ubuntu live CD to make a 1GB partition to test out a small OS, but instead of creating a partition I accidentally hit "create partition table" under the menu "device"


the second it was beginning I realised my mistake and quickly pressed cancel... but it was already to late apparently... and now it says the entire disk is "unallocated"


is there any way to recover from this? and if there isn't is there anyway to get my data off?

here is sudo fdisk -l (80GB is main drive that I screwed up..)
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System

```


OH GOD PLEASE HELP..!

---

### Post by taurus on 2009-04-07
Maybe TestDisk can do something about that, [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk).

---

### Post by Hellstudios on 2009-04-07
sorry if I seem like a noob, but how do I run the linux version?

---

### Post by WRDN on 2009-04-07
Please restart your system as soon as possible, and boot of a Live CD. This way, nothing will be written to the HDD.
Now, download the program [here]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") (for kernel 2.6.x) or [here]("http://www.cgsecurity.org/testdisk-6.10.linux24.tar.bz2") (for kernel 2.4.x), and extract the files. Open the terminal, and change to the directory ([directory]/testdisk-6.10/linux). For example, /home/user/Desktop/testdisk-6.10/linux. Finally, type

```
sudo ./testdisk_static
```

The application is also available in the repositories, and can be installed using the command:

```
sudo apt-get install testdisk
```

---

### Post by Hellstudios on 2009-04-07
I tried what you said and it comes up with errors.


I'm on the live CD, by the way.

---

### Post by Hellstudios on 2009-04-07
> **WRDN said:**
> Please restart your system as soon as possible, and boot of a Live CD. This way, nothing will be written to the HDD.
Now, download the program [here]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") (for kernel 2.6.x) or [here]("http://www.cgsecurity.org/testdisk-6.10.linux24.tar.bz2") (for kernel 2.4.x), and extract the files. Open the terminal, and change to the directory ([directory]/testdisk-6.10/linux). For example, /home/user/Desktop/testdisk-6.10/linux. Finally, type

```
sudo ./testdisk_static
```

The application is also available in the repositories, and can be installed using the command:

```
sudo apt-get install testdisk
```



OK I tried doing everything to install this program but it is still giving me errors.....**I am on a live CD, I don't know if this would work on there......**

are there any other programs I can use? testdisk doesn't like me and I just want to put my fist through my computer.

---

### Post by iponeverything on 2009-04-07
As a test a while back deleted the partition table on an old desk and then made it again exactly how it was before deleting it, and all the data was still there.

---

### Post by Hellstudios on 2009-04-08
that sounds interesting, but I don't know how exactly it was set up....

> 
Please restart your system as soon as possible, and boot of a Live CD. This way, nothing will be written to the HDD.
Now, download the program here (for kernel 2.6.x) or here (for kernel 2.4.x), and extract the files. Open the terminal, and change to the directory ([directory]/testdisk-6.10/linux). For example, /home/user/Desktop/testdisk-6.10/linux. Finally, type

Code:

sudo ./testdisk_static

The application is also available in the repositories, and can be installed using the command:

Code:

sudo apt-get install testdisk




I did what you said and it says no such file or directory, and I couldn't find it in the repository....

---

### Post by WRDN on 2009-04-08
If it gives you the error, "No such file or directory", then ensure the file is in the current directory, by typing:

```
ls
```

If not, change to the correct directory:

```
cd /[directory]
```

---

