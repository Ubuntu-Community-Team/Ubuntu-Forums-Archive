---
title: "Mounting NTFS harddrive"
date: 2006-02-06
forum: Desktop Environments
---

### Post by nami on 2006-02-06
Hello

I have a second hard drive on my computer which has no operating system installed.  I use it to store important files and backups etc.  This appears as a second drive when viewing it through Windows XP.

How can I get access to this drive from Breezy?

---

### Post by frodon on 2006-02-06
You have to know that you won't have write support for NTFS under linux so i advice you to use another file system for your data partition if you want write access under linux, for exemple FAT32 offers write/read support on both windows and linux.
However if you want to mount your NTFS partition follow this link : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by ::DoGG:: on 2006-02-06
If the filesystem is NTFS You will be able only to read from it (there are some modules that can give you red/write access to ntfs partitions but it`s still HIGHLY dangerous, so i would suggest not mess with that)

If it`s your second hard Drive i assume it`s a Slave on a first controller so it would be /dev/hdb

If you are using stock kernel you will have ntfs read already compiled into so you just need to mount it, check out this one:
[http://www.linuxforum.com/linux_tutorials/1/1.php](http://www.linuxforum.com/linux_tutorials/1/1.php)

It`s very easy.
Good Luck.

---

### Post by nami on 2006-02-06
Thanks for the info!

Probably best to convert the drive to fat32 then! :D

Thanks again

---

### Post by Ramses de Norre on 2006-02-06
Or convert it to ext3 and use this program: [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by tico on 2006-02-06
[QUOTE=nami]Probably best to convert the drive to fat32 then![/QUOTE]

Is there a way to do that without losing data in NTFS partitions?

---

### Post by frodon on 2006-02-07
No, it's possible to convert a FAT32 partition to NTFS without losing datas but not NTFS to FAT32 so you should backup your datas before converting the partition.

Good luck ;)

---

### Post by shooterae5 on 2006-02-14
You do not have the permissions necessary to view the contents of "hda1".

this is the error displayed when I try to open my NTFS partition. the partition is mounting, I just can't open it. 

this is what I added to the fstab file:
/dev/hda1    /media/hda1 ntfs  nls=utf8,umask=0222 0    0

Can anyone help me. I just need to copy files from Windoze

Thanks

---

### Post by tlaloczint on 2006-02-14
[QUOTE=shooterae5]You do not have the permissions necessary to view the contents of "hda1".

this is the error displayed when I try to open my NTFS partition. the partition is mounting, I just can't open it. 

this is what I added to the fstab file:
/dev/[COLOR="Blue"]hda1 [/COLOR]   /media/hda1 ntfs  nls=utf8,umask=0222 0    0

Can anyone help me. I just need to copy files from Windoze

Thanks[/QUOTE]

try this 

sudo fdisk -l 
then take a closer look in the drives as shown in mine

tlaloczint@aztlan:~$ sudo fdisk -l
Password:

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/[COLOR="Blue"]hdc1 [/COLOR]  *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/hdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        6202    49817533+  83  Linux
/dev/hdd2            6203       30515   195294172+   5  Extended
/dev/[COLOR="Blue"]hdd5[/COLOR]            6469       29053   181405949    7  HPFS/NTFS
/dev/hdd6           29053       30515    11751516   83  Linux
/dev/hdd7            6203        6468     2136582   82  Linux swap / Solaris

Partition table entries are not in disk order
tlaloczint@aztlan:~$

 as you can see I have two hdd and have windows along with suse and of curse ubuntu.
you can see that first windows read HDC1 thats my primary windows hdd
and the other windows read  HDD5 this is my slave I save all my stuff from windows and then copy some from ubuntu.

this is the basic command, you need to replace where says hda1 with the one in your output. hope that this works.

/dev/([COLOR="Blue"]your output[/COLOR])[/B] /media/([COLOR="Blue"]your output[/COLOR]) ntfs nls=utf8,umask=0222 0 0

---

