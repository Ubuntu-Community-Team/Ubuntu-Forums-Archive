---
title: "I deleted windows from dual-boot system and now I have problems"
date: 2011-06-04
forum: Desktop Environments
---

### Post by hashcode on 2011-06-04
Hi, I had Ubuntu/Windows 7 dual boot. I decided not to use Windows anymore, so I deleted it's partition (using Gparted) and formatted it to ext4. Then I did update of grub.

Here are few issues I am having now:

1. The new partition won't automount
2. I can not use new partition. It has only one directory - lost and found. I can't copy data there.
3. Grub still has Windows 7 option (it doesn't work of course)
4. Grub fails to boot (it says it didn't find /windows partition), so I have to always skip that manually

Thanx for help!

---

### Post by Frogs Hair on 2011-06-04
Here is a link that has a section on repairing grub. If this was a Wubi installation this  will not apply because Wubi installs Ubuntu inside Windows .If Windows has been removed so has Ubuntu.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by oldfred on 2011-06-04
if windows is truly gone this will update the menu.

sudo update-grub

With ext4 partition you have to set ownership & permissions. Best to permanently mount with fstab.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

sudo mkdir /data
sudo mount /dev/sda5 /data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything below is changed, do NOT run on system partitions & be sure of mount point. 
sudo chmod -R 777 /data
sudo chown -R $USER:$USER /data
#where $USER should be your login name
#or to see user
echo $USER

---

