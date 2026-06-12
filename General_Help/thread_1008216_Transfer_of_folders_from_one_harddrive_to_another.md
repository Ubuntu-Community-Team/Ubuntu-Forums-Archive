---
title: "Transfer of folders from one harddrive to another"
date: 2008-12-11
forum: General Help
---

### Post by manoka on 2008-12-11
Hello,

I can't transfer any folders or files from the harddrive I'm using now, to my second and also connected harddrive.
When I try to do so I'm getting the message:

> Failed to run /usr/bin/gnome-mount '--hal-udi' '/org/freedesktop/Hal/devices/volume_uuid_da5822d7_3363_43fd_ad10_4660edd64212' as user root.
Unable to copy the user's Xauthorization file.

Any help would be very much appreciated!

manoka

---

### Post by taurus on 2008-12-11
What filesystem is the other harddrive?  Are you trying to copy your $HOME to that drive?

```
sudo fdisk -l
mount
```

---

### Post by manoka on 2008-12-12
Thanks taurus,

I don't understand what you mean with "What filesystem". 
Because I couldn't format or erase some leftovers from my previously but no longer used Windows XP OS, I recently installed the new Ubuntu 8.10 on that bigger harddrive which I set as "slave" - while I set the smaller one as "master".

I would like to use the bigger harddrive only for my files and folders, and the smaller one only for the Ubuntu OS and the applications.
Thus I would like to move all my files and folders to my bigger harddrive, because the smaller one, where I have everything I'm using, is full.

After entering the command "sudo fdisk -l
mount", I got this response:
> 
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x802b81ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d2463

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36247   291153996   83  Linux
/dev/sdb2           36248       36481     1879605    5  Extended
/dev/sdb5           36248       36481     1879573+  82  Linux swap / Solaris

---

### Post by Peter09 on 2008-12-12
What does
```
df -h
```

show

---

### Post by manoka on 2008-12-12
Thanks Peter09,

df -h shows:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G   18G     0 100% /
varrun                316M   96K  316M   1% /var/run
varlock               316M  4.0K  316M   1% /var/lock
udev                  316M   84K  316M   1% /dev
devshm                316M     0  316M   0% /dev/shm
lrm                   316M   34M  282M  11% /lib/modules/2.6.22-16-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp

Would it be possible to work with the OS and the applications in one harddrive, and with the folders and files on the other, to preserve my personal files and settings?

In the meantime I was able at least to copy my Home Folder onto the bigger harddrive. 
I don't suppose this would be possible with my applications, so I could use them again after a clean install upgrade, so I wouldn't have to download and install them again?

---

### Post by Peter09 on 2008-12-12
What is the mount point for your second drive - I could not see it from your df -l output?

---

### Post by manoka on 2008-12-12
Where can I find this info?

---

### Post by Peter09 on 2008-12-12
How are you mounting your second drive, are you mounting it at all?

Here are some threads to help

[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

[http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)

[http://ubuntuforums.org/showthread.php?t=403650](http://ubuntuforums.org/showthread.php?t=403650)

---

### Post by manoka on 2008-12-12
Both harddrives are mounted, or connected, the same way: Inside the PC.

---

### Post by ezsit on 2008-12-12
> Filesystem Size Used Avail Use% Mounted on
/dev/sda1 18G 18G 0 100% /

This could be causing some problems, your / filesystem is completely filled. Your system will not run properly with the / filesystem filled up. If you are trying to move your /home directory, look at this guide to see if it helps:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Peter09 on 2008-12-12
mounting a hard drive is a software activity not a hardware thing. You will need to mount it using the mount command.

---

### Post by manoka on 2008-12-12
> What is the mount point for your second drive

I found some info which reads:

> Mounted on /media/disk-1

Otherwise I can't follow the instructions on [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Where I'm supposed to "select Resize/Move", this option isn't active (it's displayed in grey instead of black).

---

### Post by Peter09 on 2008-12-12
Thats all about making a separate home and partitioning your drive. You want to be able to mount your drive.

---

### Post by Peter09 on 2008-12-12
try this command

```
mkdir ~/Desktop/temporary
```

```
sudo mount /dev/sdb ~/Desktop/temporary
```

If that works post the output of

```
df -l
```

---

### Post by manoka on 2008-12-12
I'm getting the following responses:

> mkdir ~/Desktop/temporary

mkdir: cannot create directory `/home/vital/Desktop/temporary': No space left on device


> sudo mount /dev/sdb ~/Desktop/temporary

mount: mount point /home/vital/Desktop/temporary does not exist

---

### Post by Peter09 on 2008-12-12
The first command failed because you have no space left on your first disk. Try emptying your waste bin and cleaning up.

---

### Post by manoka on 2008-12-12
Now I'm getting the following responses:

> mkdir ~/Desktop/temporary

mkdir: cannot create directory `/home/vital/Desktop/temporary': File exists

> sudo mount /dev/sdb ~/Desktop/temporary

mount: /dev/sdb already mounted or /home/vital/Desktop/temporary busy

> df -l

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             18398028  17162704    300748  99% /
varrun                  322744        96    322648   1% /var/run
varlock                 322744         4    322740   1% /var/lock
udev                    322744        76    322668   1% /dev
devshm                  322744         0    322744   0% /dev/shm
lrm                     322744     34696    288048  11% /lib/modules/2.6.22-16-generic/volatile
overflow                  1024        24      1000   3% /tmp
/dev/sdb1            286584348  13820544 258206108   6% /media/disk-1

---

### Post by Peter09 on 2008-12-12
According to this line in your df -l output

/dev/sdb1 286584348 13820544 258206108 6% /media/disk-1 

your disk is already mounted at /media/disk-1

if you got to that directory you should see the contents of your disk. It should also be appearing in your places menu.

---

### Post by manoka on 2008-12-12
Now that this is finally sorted out, is it possible to move or to copy my personal files (and folders) - actually I already copied my Home Folder to the bigger harddrive - and possibly the settings and applications as well (to preserve them for a clean install upgrade), to the bigger harddrive, and if yes, how?

---

### Post by Peter09 on 2008-12-12
Best start new thread, this ones complete

---

