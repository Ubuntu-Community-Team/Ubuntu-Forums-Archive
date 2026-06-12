---
title: "How do I open a Windows drive?"
date: 2009-06-02
forum: General Help
---

### Post by smartdude4ever on 2009-06-02
Hi everyone!
I just received my ordered CD in less than 4 weeks (9.04)! I just installed ubuntu through Windows and I'm quite happy with it.
The thing which is confusing me is that how do open a Windows drive in ubuntu?
For example, I have all my music in F Drive in Windows; but there doesn't seem to be an F drive in My Computer in ubuntu.
There are only 3 icons - 40GB Media, CD\DVD ROM Drive, Filesystem
Please help me! I want to play my music in ubuntu!
Thanks!

---

### Post by 73ckn797 on 2009-06-02
> **smartdude4ever said:**
> Hi everyone!
I just received my ordered CD in less than 4 weeks (9.04)! I just installed ubuntu through Windows and I'm quite happy with it.
The thing which is confusing me is that how do open a Windows drive in ubuntu?
For example, I have all my music in F Drive in Windows; but there doesn't seem to be an F drive in My Computer in ubuntu.
There are only 3 icons - 40GB Media, CD\DVD ROM Drive, Filesystem
Please help me! I want to play my music in ubuntu!
Thanks!

Ubuntu does not list drives the same way as Windows. There are no typical C:, D: and so forth. The ones you list, are those what you see when in the file browser? The 40GB is probably the Windows partition, then the obvious CD/DVD drive and filesystem is the Ubuntu partition. You should be able to read the Windows directories.

Do you have more than one hard drive?

If you open terminal and type:
```
sudo fdisk -l
``` it will list the drives and installed systems. You will have to enter your password when prompted.

---

### Post by smartdude4ever on 2009-06-02
i have only one hard disk
how can i browse F partition on ubuntu
F is the partition in windows

---

### Post by 73ckn797 on 2009-06-02
> **smartdude4ever said:**
> i have only one hard disk
how can i browse F partition on ubuntu
F is the partition in windows

Selecting Places/Computer will bring up the Nautilus File Browser. If Windows is on the 40GB partition then simply click on that and you should be able to see the contents of the Windows partition.

Post the results of the previous command I gave you.

---

### Post by colau on 2009-06-02
> **smartdude4ever said:**
> i have only one hard disk
how can i browse F partition on ubuntu
F is the partition in windows
Application>Accessories>Terminal
Type 
```

nautilus

```

---

### Post by smartdude4ever on 2009-06-02
40GB media is only the Windows Partition (C drive)
But i want my music which is in F Drive and its not there in Nautilus file browser....

---

### Post by Invincible23 on 2009-06-02
Dude open the 'host' folder in the Filesystem. That's the F drive on which i guess you used wubi to install ubuntu.

---

### Post by colau on 2009-06-02
> **smartdude4ever said:**
> 40GB media is only the Windows Partition (C drive)
But i want my music which is in F Drive and its not there in Nautilus file browser....
From nautilus>Edit>Preferences>Behaviour 
check the "Always open in browser window"

---

### Post by 73ckn797 on 2009-06-02
> **smartdude4ever said:**
> 40GB media is only the Windows Partition (C drive)
But i want my music which is in F Drive and its not there in Nautilus file browser....

Again, go to Applications/Accessories/Terminal and type the command:
```
sudo fdisk -l
``` and post the results of that. That will show all of the partitioning of the drive(s) you have.

---

### Post by smartdude4ever on 2009-06-02
This is what i get on typing sudo fdisk -l

kamaljeet@ubuntu:~$ sudo fdisk -l
[sudo] password for kamaljeet: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x891e891e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39060480    7  HPFS/NTFS
/dev/sda2            4864       19458   117228856+   f  W95 Ext'd (LBA)
/dev/sda5            4864        9726    39062016    b  W95 FAT32
/dev/sda6            9727       14589    39059456    7  HPFS/NTFS
/dev/sda7           14590       19457    39102178+   b  W95 FAT32

I want to browse the fourth partition (W95 FAT32) (sda7)
How can i do that?

---

### Post by colau on 2009-06-02
> **smartdude4ever said:**
> This is what i get on typing sudo fdisk -l

kamaljeet@ubuntu:~$ sudo fdisk -l
[sudo] password for kamaljeet: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x891e891e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39060480    7  HPFS/NTFS
/dev/sda2            4864       19458   117228856+   f  W95 Ext'd (LBA)
/dev/sda5            4864        9726    39062016    b  W95 FAT32
/dev/sda6            9727       14589    39059456    7  HPFS/NTFS
/dev/sda7           14590       19457    39102178+   b  W95 FAT32

I want to browse the fourth partition (W95 FAT32) (sda7)
How can i do that?
```

sudo mkdir /media/MYDRIVE
sudo mount /dev/sda7 /media/MYDRIVE
sudo cd /media/MYDRIVE
ls

```

---

### Post by Invincible23 on 2009-06-02
> **smartdude4ever said:**
> I want to browse the fourth partition (W95 FAT32) (sda7)
How can i do that?

kamaljeet open the 'host' folder in the filesystem. That's were you data from F drive is located.

---

### Post by smartdude4ever on 2009-06-02
what is MYDRIVE?
I type the same line but it doesn't accept it
sorry for being a noob

[edit] - see the 15th post

---

### Post by smartdude4ever on 2009-06-02
to invincible23
I opened the host folder but thats the E drive where ubuntu is installed
anyway, thanks for your help
i really appreciate it

---

### Post by smartdude4ever on 2009-06-02
kamaljeet@ubuntu:~$ sudo mkdir /media/MYDRIVE
[sudo] password for kamaljeet: 
kamaljeet@ubuntu:~$ sudo mount /dev/sda7 /media/MYDRIVE
mount: you must specify the filesystem type
kamaljeet@ubuntu:~$

---

### Post by colau on 2009-06-02
> **smartdude4ever said:**
> kamaljeet@ubuntu:~$ sudo mkdir /media/MYDRIVE
[sudo] password for kamaljeet: 
kamaljeet@ubuntu:~$ sudo mount /dev/sda7 /media/MYDRIVE
mount: you must specify the filesystem type
kamaljeet@ubuntu:~$
```

sudo mkdir /media/MYDRIVE
sudo mount -t vfat /dev/sda7 /media/MYDRIVE
cd /media/MYDRIVE
ls

```

---

### Post by smartdude4ever on 2009-06-02
Successful! Thanks to colau and others for the help!

kamaljeet@ubuntu:~$ sudo mkdir /media/MYDRIVE
mkdir: cannot create directory `/media/MYDRIVE': File exists
kamaljeet@ubuntu:~$ sudo mount -t vfat /dev/sda7 /media/MYDRIVE
kamaljeet@ubuntu:~$ cd /media/MYDRIVE
kamaljeet@ubuntu:/media/MYDRIVE$ ls
Backup     ehthumbs_vista.db  RecoveryBin   System Volume Information
Downloads  found.000          $recycle.bin
Drivers    Linkin Park        Recycled
e          Pics               resycled
kamaljeet@ubuntu:/media/MYDRIVE$ 
kamaljeet@ubuntu:/media/MYDRIVE$

Now I can browse my F drive!
My problem is solved!

---

### Post by colau on 2009-06-02
> **smartdude4ever said:**
> Successful! Thanks to colau and others for the help!

kamaljeet@ubuntu:~$ sudo mkdir /media/MYDRIVE
mkdir: cannot create directory `/media/MYDRIVE': File exists
kamaljeet@ubuntu:~$ sudo mount -t vfat /dev/sda7 /media/MYDRIVE
kamaljeet@ubuntu:~$ cd /media/MYDRIVE
kamaljeet@ubuntu:/media/MYDRIVE$ ls
Backup     ehthumbs_vista.db  RecoveryBin   System Volume Information
Downloads  found.000          $recycle.bin
Drivers    Linkin Park        Recycled
e          Pics               resycled
kamaljeet@ubuntu:/media/MYDRIVE$ 
kamaljeet@ubuntu:/media/MYDRIVE$

Now I can browse my F drive!
My problem is solved!
Welcome.

---

