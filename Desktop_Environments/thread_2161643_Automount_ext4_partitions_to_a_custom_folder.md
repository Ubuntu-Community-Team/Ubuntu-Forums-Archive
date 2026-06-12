---
title: "Automount ext4 partitions to a custom folder"
date: 2013-07-11
forum: Desktop Environments
---

### Post by 87242013 on 2013-07-11
Hi, I am using Ubuntu 12.04 LTS. I want to mount my **/dev/sda8** and **/dev/sda9 **partitions on ** /mounted_partition/mix **and** /mounted_partition/personal **respectively.  I have edited /etc/fstab and added the following lines at the bottom-

[B]/dev/sda8  /mounted_partition/mix defaults 0 0
/dev/sda9  /mounted_partition/personal defaults 0 0[/B]

But when i restart the system it shows **"an error occurred while mounting on /mounted_partition/mix"** and **"an error occurred while mounting on /mounted_partition/personal"** while booting. The content of /etc/fstab file after editing-

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=22b9206c-ddb5-4e99-87a5-3ced84940bc8 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=2b5068a3-56f5-428e-97d1-3465b564f45e /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=4bba8a9a-d64c-4939-beb5-270022d80884 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=aa2c2155-ab81-4bc6-b9db-699882cf4e7c none            swap    sw              0       0
/dev/sda8 /mounted_partition/mix defaults 0 0
/dev/sda9 /mounted_partition/personal defaults 0 0
```

Please help me fixing this..

---

### Post by oldfred on 2013-07-11
Better to use UUID as sometimes drive order may change. Some BIOS may promote a flash drive to sda and then your mount points are wrong. I skipped a port on motherboard and depending on whether I plug in flash drive or boot with flash drive it is either last  or in missing port order and then all my other drives get reordered.

What format are partitions ext3, ext4 or NTFS? You must specify and then the options to use are different. See examples below.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

   For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

---

### Post by 87242013 on 2013-07-11
Thanks..this solved my problem..:p

---

