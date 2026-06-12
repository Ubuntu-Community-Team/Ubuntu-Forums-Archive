---
title: "Why is FAT32 Partition Not Writable ??"
date: 2009-06-15
forum: General Help
---

### Post by scythian on 2009-06-15
Hi, I have mounted a 10GB FAT32 partition on a 10GB IDE hard drive to my file system on Ubuntu 8.04LTS Desktop edition, but am unable to create a directory or copy a file to it.

I also have a FAT32 USB MP3 drive and it is OK - I can write files to it.

On running 'mount -t vfat' the output is :-

/dev/sdc1 on /media/SGTL MSCN type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb1 on /home/scythian/test1 type vfat (rw)

I see it says 'rw' so why isn't it writable ?

Thanks for any advice.

---

### Post by StGeorge on 2009-06-15
You may only need to CHMOD the directory in mnt/
SEE BOTTOM:
mkir is making a directory.
If it exists then just CHMOD.

Terminal:
********************************

sudo fdisk -l

********************************

sudo mkdir <your_mount_point>

********************************

sudo mount -t vfat -o defaults,user,exec,uid=1000,gid=100,umask=000 <device> <mount_point>

********************************

Let's say that using the fdisk command reveals that you want to mount /dev/sdb1 - run:
********************************

sudo mkdir /media/fat_partition
sudo mount -t vfat -o defaults,user,exec,uid=1000,gid=100,umask=000 /dev/sdb1 /media/fat_partition

********************************

Let's say that using the fdisk command reveals that you want to mount /dev/sdb1 - run:
********************************

sudo mkdir /media/fat_partition

********************************

sudo mount -t vfat -o defaults,user,exec,uid=1000,gid=100,umask=000 /dev/sdb1 /media/fat_partition

********************************

gedit /etc/fstab 

*******************************

Edit the file, save and close it. 

*******************************

Terminal:
*******************************

sudo mount -a

*******************************
*******************************

Taken From:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

I used the above and it worked for me.

However you can create a mnt/directory.

You would be best to get your fstab sorted, (as above).

I have also done below. 

You may only need to CHMOD the directory in mnt/

If you still have problems Create Directory and CHMOD:
********************************

Enter the following command into terminal:
***************************

mkdir /mnt/(YOUR DRIVE)

sudo chmod -R 777 /mnt/(YOUR DRIVE)

***************************

---

### Post by synapsys on 2009-06-15
You probably don't have permission to write to it.

Try writing to it as root and see if you can.
If you can, then you need to change permissions of the mount point.

---

### Post by scythian on 2009-06-15
Thanks for this info

I have tried the following in Terminal window :-

su (to change to root user - I have set the root user to have a password)
chmod -v a+w test1
OR
chmod -v o+w test1
OR
chmod -v g+w test1

(where test1 is my mount point to the FAT32 drive partition)

And every time, the -v verbose says the permissions have changes. ie to (respectively)

rwxrwxrwx (777)
rwxr-xrwx (757)
rwxrwxr-x (775)

BUT when I do 'ls -l' again the perms have NOT been changed and are still at :-

rwxr-xr-x

Also in Nautilus running under root, in Properties->Permissions tab for the mount point directory, when I change perms they are set back again ie I go back into the perms and they are back to what they were before. It won't let me change them.

BUT if I run Nautilus under 'root' I CAN create subdirectories and files under the mount point ie I DO have the write access.

So I am very puzzled.

---

