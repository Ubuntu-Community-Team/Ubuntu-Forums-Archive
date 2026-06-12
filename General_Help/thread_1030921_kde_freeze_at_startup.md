---
title: "kde freeze at startup"
date: 2009-01-04
forum: General Help
---

### Post by rubin_78 on 2009-01-04
Hello everyone,

I am using kde 8.10 two months now. Before a couple of days, all the sudden my KDE freeze at start up. I cant do nothing..I can only move the mouse on the screen..](*,)

However, I can login using the console and I am very happy because all my files are still in there and I can see them.

The thing is that I have 2-3 very important files from a task that i was doing in kde. All I ask is to tell me how to copy these folders on my USB memory stick using the console. Theproblem is that I am completely noob and I have no time to find out.

Lets say that I am in the directory Folder1/file1, how do i copy this file to my USB?

Thank u in advance, sorry for these dump questions..I will do my best to catch up :mrgreen:

---

### Post by Ahadiel on 2009-01-04
I guess first would be to identify your USB stick.
```
sudo fdisk -l
```
Once identified, create a mount point for the device
```
sudo mkdir /media/usbdrive
```
Then mount the drive
```
sudo mount /dev/sd?1 /media/usbdrive
```
And as for copying the file to the USB drive
```
sudo cp file1 /media/usbdrive/
```

When you're done, unmount the drive
```
sudo umount /media/usbdrive
```

---

### Post by abn91c on 2009-01-04
did you activate desktop effects, if so you may need to remove compiz
sudo apt-get remove compiz
sudo apt-get remove compiz-core

---

### Post by Skripka on 2009-01-04
> **abn91c said:**
> did you activate desktop effects, if so you may need to remove compiz
sudo apt-get remove compiz
sudo apt-get remove compiz-core


Compiz is not a KDE component or option in KDE4 (really).  All effects are integrated into Kwin.

---

### Post by rubin_78 on 2009-01-04
> I guess first would be to identify your USB stick.
```
sudo fdisk -l
```

After I am writing this command I am getting the following:

fdisk invalid option -- '1'
Usage: fdisk [-b SSZ] [-u] DISK Change partiotion table
       fdisk -|[-b SSZ] [-u] DISK List partition table
       fdisk -s PARTITION
       fdisk -v
Here DISK is something lime /dev/hdb or /dev/sda
and PARTITION is something like /dev/sda
etc..

> ```
sudo mkdir /media/usbdrive
```
Then mount the drive

> ```
sudo mount /dev/sd?1 /media/usbdrive
```

In the place above where you put the question mark, do I have to put something different? something from the above? becasue I tried exactly what u wrote and it is not working


EDIT: When I am getting into the directory of /media/usbdrive I can see the files that I copied but when I plug my USB into my XP machine there is nothing in there

---

### Post by rubin_78 on 2009-01-04
Hello again!

I just find out how to do it!!

I told you I am noob:biggrin:!!!

Ahadiel thank you very much for being patient with me :)

---

### Post by Ahadiel on 2009-01-04
Glad to see you got it working.

---

