---
title: "Missing drive"
date: 2005-12-20
forum: Desktop Environments
---

### Post by ken_nic on 2005-12-20
Hi
I have installed ubuntu on my laptop with Xp aswel. I followed a guide and ended up shrinking my windows partition to 20GB and creating a FAT32 partition which was then divided up in to 15GB for ubuntu and about 60GB for all my files which I will want to get to from both ubuntu and Xp. 

All workes well exept for I cant se the 60GB (E drive) whilst in ubuntu. When im in windows i can.

How do I get to the E drive whilst in ubuntu?

Thanks

---

### Post by ken_nic on 2005-12-20
Any info greatly appreciated:)

---

### Post by cwaldbieser on 2005-12-20
[QUOTE=ken_nic]Any info greatly appreciated:)[/QUOTE]
What have you tried so far?

Basically, you need to mount the drive.  The steps to do that should be covered in the guide, but you said you had followed the guide, so I am not exactly sure where you ran into trouble...

Can you at least see the drive and partition if you type:
```

$ sudo fdisk -l

```
at the terminal prompt?

---

### Post by dcstar on 2005-12-20
[QUOTE=ken_nic]Hi
I have installed ubuntu on my laptop with Xp aswel. I followed a guide and ended up shrinking my windows partition to 20GB and creating a FAT32 partition which was then divided up in to 15GB for ubuntu and about 60GB for all my files which I will want to get to from both ubuntu and Xp. 

All workes well exept for I cant se the 60GB (E drive) whilst in ubuntu. When im in windows i can.

How do I get to the E drive whilst in ubuntu?

Thanks[/QUOTE]
Look in System-Administration-Disks and see if the partition is visible.

---

### Post by ken_nic on 2005-12-21
Ok
If I type $ sudo fdisk -l it says comand not found.

If i go to System-Administration-Disks Under the partitions tab I can see a list of partitions including the one I want to use (Partition 5)

It says
Device: /dev/hda5
Fillesystem: Windows Virtual Fat (vfat)
Access Paths: none
Size: 60.53 GiB (Free space not available)
Status: inaccessible

Thanks!

---

### Post by cwaldbieser on 2005-12-21
[QUOTE=ken_nic]Ok
If I type $ sudo fdisk -l it says comand not found.

If i go to System-Administration-Disks Under the partitions tab I can see a list of partitions including the one I want to use (Partition 5)

It says
Device: /dev/hda5
Fillesystem: Windows Virtual Fat (vfat)
Access Paths: none
Size: 60.53 GiB (Free space not available)
Status: inaccessible

Thanks![/QUOTE]
Sorry,  something like:
```

$ command

```
means you type "command" at the normal prompt (you don't actually type the "$").  If it is a "#", that means the root prompt.

The general way to access the drive is to mount it.  Manually, you can do something like:
```

$ sudo mkdir -p /mnt/hda5
$ sudo mount -t vfat -o 'iocharset=utf8,umask=000' /dev/hda5 /mnt/hda5

```
This creates a directory /mnt/hda5 if it doesn't already exist and mounts the drive there.

At this point, you will see the contents of the drive under /mnt/hda5.  You can unmount it with
```

$ sudo umount /mnt/hda5

```

If you want this drive permanently available, you can set this up in you /etc/fstab file like it says in the User Guide.  If you have trouble doing that, try posting the contents of /etc/fstab back here.

---

### Post by ken_nic on 2005-12-21
If i type sudo fdisk -l i can se all the drives
I have now mounted the drive so if I go System-Administration-Disks the partition is now avalible and i can browse it from there but I am yet to work out how to make it show up in the file browser (next to the cd drive and the one called filesystem)

Im going to have a read of some guides to try and get used to the diferences from xp.

---

