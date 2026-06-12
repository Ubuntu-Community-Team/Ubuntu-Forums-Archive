---
title: "Automount fat32 with execute bit set"
date: 2012-01-24
forum: Desktop Environments
---

### Post by haho on 2012-01-24
Problem: automount does not set any execute permission bit for external usb drive. (permissions are always 600)

Solution:
Create a file in /etc/udev/99-usb-disks.rules and enter
```
ENV{ID_FS_TYPE}=="ntfs", ENV{ID_FS_TYPE}="ntfs-3g"
```unplug usb disk
replug usb disk
now all files should have 777 permissions

Detailed solution:
For some reason udev does not use the ntfs-3g driver but the ntfs driver. I do not know why and I do not know why it only supports 600. I thought the ntfs driver could only read the files... Then again to be honest I do not really care. :)



Original post:

Hello,

when automounting an external usb drive thunar recognizes it but mounts it using -rw------- which is extremely annoying as I have executable files there. I want -rwx------ but as this is a fat32 partition sudo chmod will not cut it.

Thanks

---

### Post by LewisTM on 2012-01-24
Maybe this [Q&A]("http://superuser.com/questions/134438/how-to-set-default-permissions-for-automounted-fat-drives-in-ubuntu-9-10") can point you in the right direction.

I had a similar problem with a networked Windows share that I wanted to use to sync all my important Linux files, including all permissions. I ended up creating a large btrfs-formatted loop file (a filesystem within a file) on the network drive, then mounting it on demand in Ubuntu. This can be done on a FAT32 pen drive if you don't plan to share those files with Windows users.

Cheers!

---

### Post by haho on 2012-01-24
I tried the udev "solution". Here is my udev rule

```
KERNEL=="sdb[0-9]", SYMLINK+="Ihateyou", MODE:="0777"
```I know that it is matched because the /dev/Ihateyou sysmlink exists. However it completely ignores MODE. No error message, no nothing.

I have tried naming the rules file 00-usb-disks.rules and 99-usb-disks.rules and have checked that it is either the first file parsed or the last one. (Unfortunately the docs are not clear as to what happens in the case of conflicting rules). The := means that the assignment is final. I also tried a simple =. I tried 0777 and 777 as MODE strings.

Under my old ubuntu setup automounting worked out of the box with this same usb disk. This is very frustrating and a rather big show stopper as being forced to cp every file to another partition before being able to work defeats the whole purpose of having an external drive in the first place.


Well it seems as fstab hacking is my only option... I'll see how this goes.

EDIT:
cat < /proc/mounts gives

```
/dev/sdb1 /media/name fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0
```

which is the same as for my internal windows partition where executable have the exec bit set... Seems as if fstab hacking will most likely not solve the problem either. This is sooooo frustrating.

---

### Post by haho on 2012-01-24
I tried the fstab version and it works partially:

```
UUID=DC4037774037580A /media/LaCie ntfs-3g rw,auto,user,umask=000 0 0 
```(Use gparted to find the UUID of the drive, I needed to create the mount point by hand)

automounting does not work because I get an error message, that I have to have root privileges... It works if I manually

```
sudo mount /media/LaCie
```Still far from what I want

EDIT:

Solved the problem. See first post for solution

---

