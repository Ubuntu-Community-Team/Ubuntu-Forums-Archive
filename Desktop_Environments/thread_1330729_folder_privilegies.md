---
title: "folder privilegies"
date: 2009-11-18
forum: Desktop Environments
---

### Post by edioilha on 2009-11-18
Hi Guys!
Im newbie
I have just installed a Ubuntu 9.10.

I have a 80gb HD with a 50...Gb NTFS with a forder called Arquivos and 30Gb unalocated Partition. I choose to advanced partitioning when Installing Ubuntu.
That was
dev/sda

[LIST]
[*]dev/sda1 (Mounted at /)
[*]dev/sda2 as extended (dev/sda5 Swap)
[/LIST]

[LIST]
[*]dev/sda3 (Mounted at /windows)
[/LIST]
I have used for it a user called pc4
There is a group called pc4 too. I didnt create it.
I dont know if is everething ok I can chenge it its for tests pourpouse.
Now I want to get the folder /windows/Arquivos shared but I need to change the privilegies. 
It says the Owner is root and the Group is plugdev

When I try sudo chown -R $USER:$USER /windows asks for password I enter the password but nothing change, the folder continues with the same owner
When I try gksudo nautilus and try to change the owner it does not allow me, it is enabled to change but when I change it and go to the next field it come to root again.

Please help me
sorry about my English
Thx a million
EdioIlha

---

### Post by sisco311 on 2009-11-18
NTFS partitions do not support unix/linux file permissions.

You can set the permission, for all files/directories, at mount time.

By default Ubuntu mounts the partition with read/write permissions for the users in the plugdev group.

If you want to allow a user to write to the partition just add the user to the plugdev group. 

System -> Administration -> Users and Groups, click the unlock button -> Manage Groups -> select the plugdev group -> Properties and select the users you want to add to the group.

Or run this from a terminal (Applications -> Accessories -> Terminal) 
```
sudo adduser username plugdev
```
replace username with the user's login name.

---

### Post by edioilha on 2009-11-18
> **sisco311 said:**
> NTFS partitions do not support unix/linux file permissions.

You can set the permission, for all files/directories, at mount time.

By default Ubuntu mounts the partition with read/write permissions for the users in the plugdev group.

If you want to allow a user to write to the partition just add the user to the plugdev group. 

System -> Administration -> Users and Groups, click the unlock button -> Manage Groups -> select the plugdev group -> Properties and select the users you want to add to the group.

Or run this from a terminal (Applications -> Accessories -> Terminal) 
```
sudo adduser username plugdev
```replace username with the user's login name.

Thx a lot!
What could be a better solution? Format with fat32? And what about mounted at /windows? Is that Ok or better mount it at /etc/fstab after instalation?
I just need a partition that could be saw in a Windows box.
What I did was, put the drive in a windows machine and formated it with 1 patrition and 1 unpartitioned, and then put back at the machine and installed Ubuntu.

Man I need to learn a lot of about Ubuntu and unix/linux

Thx a million for you suport
EdioIlha

---

### Post by sisco311 on 2009-11-18
FAT partitions do not support file permissions at all (not even in Windows). You can set the permissions and ownership at mount time in the same manner you do it with NTFS partitions.

In my opinion, NTFS is the best filesystem format to share data between Linux and Windows on a dual-boot system. 

You can mount a partition anywhere in the filesystem hierarchy. Some people prefer to mount their data partitions directly in the home directory (i.e. /home/username/music). That's probably not the best location if you want to share it with other users.

If you want to share the partition with other users, I would recommend to mount it in /media (i.e. /media/data). Partitions in /media will show up in the file manager's *Places* menu, so users can access it easily.

The installer has already created an fstab entry for the partition(that's why it's mounted at boot time). 

If you want to change the mount point of the partition:
[list]
[*]backup the file:
```
sudo cp /etc/fstab /etc/fstab.old
```

[*]unmount the partition:
```
sudo umount /windows
```

[*]edit the file:
```
gksu gedit /etc/fstab
```

[*]the mount points are in the second column:
```
UUID=<....>     **/windows**     ntfs     defaults,gid=64....
```

replace **/windows** with the new mount point(i.e. /media/data). Save the file and exit.

[*]create the new mount point:
```
sudo mkdir /media/data
```

[*]mount the partition:
```
sudo mount -a
```

[*]now the partition should show up in /media/data
[/list]

[thread=283131]How to fstab[/thread]

---

### Post by edioilha on 2009-11-18
Thx Thx Thx

About Fat I new that but you make me remember about it.
Nice, but how can I share it if I cant change permissions?
Now I´m trying to do this in a vm. 
[http://www.youtube.com/watch?v=VhqRYDNzquE](http://www.youtube.com/watch?v=VhqRYDNzquE)
Do I need something more to share then, just right click in the folder and choose share and bla bla bla.

But any way the problem with permissions is done and I will make it solved.
I will search for the share issue.
Man I dont wanna be a MS Windows user forever. I cant figure out how to do things in Ubuntu.
Thx

---

