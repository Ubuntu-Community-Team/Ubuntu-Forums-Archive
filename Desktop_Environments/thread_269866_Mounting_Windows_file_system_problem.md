---
title: "Mounting Windows file system problem"
date: 2006-10-02
forum: Desktop Environments
---

### Post by marufsiddiqui on 2006-10-02
I need help on mounting windows file system

i'm using the live CD but dont know how to mount my windows FAT32/NTFS drive

Help me

---

### Post by taurus on 2006-10-02
Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo mkdir /mnt/windows
sudo mount -t vfat /dev/hda1 /mnt/windows
(assuming your Windows, fat32, is on /dev/hda1...)
-or-
sudo mount -t ntfs /dev/hda1 /mnt/windows
(assuming your Windows, NTFS, is on /dev/hda1...)

```

---

### Post by Cable on 2006-10-02
Read [this]("http://www.psychocats.net/ubuntu/mountwindows").

---

### Post by dannyboy79 on 2006-10-02
you can find out which hard drive is which thru the command line also, type in 
sudo fdisk -l

and then all you hard disks will come up with an identifier I am pretty sure, hda1, hda2, hdb1, sda1

hda1 is the first partition on ide0 channel, hda2 is the second partition on ide0 channel.
hdb1 is the first partition on ide1 channel, so on and so forth.
sata and usb drives are normally identified with sda etc etc., same thing, wehre the number designates the partition. good luck
oh, don't try to write to a ntfs partition unless you want to risk losing stuff, a lot of people may disagree with me because ntfs write support has really come along way but it's an add on feature and not really supported by the kernel.

---

### Post by aysiu on 2006-10-02
> **taurus said:**
> Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo mkdir /mnt/windows
sudo mount -t vfat /dev/hda1 /mnt/windows
(assuming your Windows, fat32, is on /dev/hda1...)
-or-
sudo mount -t ntfs /dev/hda1 /mnt/windows
(assuming your Windows, NTFS, is on /dev/hda1...)

``` Won't those commands mount it so that only root can open the drive?

First of all, you have to know where your drives are located and what filesystem it is. Paste this command in the terminal ```
sudo fdisk -l
``` and the output will tell you. For these examples, we'll assume it's /dev/hda1 for NTFS and /dev/hda2 for FAT32. Paste in modified versions of these commands to make mount points for your Windows partitions and mount them: ```
sudo mkdir /media/fat
sudo mkdir /media/ntfs
sudo mount -t ntfs /dev/hda1 /media/ntfs -o nls=utf8,umask=0222
sudo mount -t vfat /dev/hda2 /media/fat -o iocharset=utf8,umask=000
```

---

### Post by dannyboy79 on 2006-10-02
here is my fstab for my fat32 and ntfs drives and it works, i can even write to it from my winxp box over samba.

/dev/hdb5	/home/daniel/ntfs	ntfs	ro,uid=1000,gid=1000,nls=utf8,umask=0222	0	0
/dev/hdb1	/home/daniel/fat32	vfat	rw,uid=1000,gid=1000,iocharset=utf8,umask=0000	0	0

---

### Post by lawina on 2006-10-02
The above methods are good enough if you want to read from NTFS. 
If you want to write however you can use the following method from the Ubuntu Dapper howto website by installing NTFS 3G

 How to mount Windows partitions (NTFS) on boot-up, and allow users read and write access

Warning: Ntfs writing support is still experimental. You should not enable it on production machines and/or volumes you don't have backups of. Proceed at your own risk!

    * Read #General Notes 

sudo apt-get install libfuse2 fuse-utils

    * Download the latest ntfsprogs package (these are from the Dapper repositories, so they are safe to install.) 

libntfs8 ntfsprogs libfuse2 fuse-utils

    * Install the downloaded packages 

sudo dpkg -i libfuse2_*.deb fuse-utils_*.deb ntfsprogs_*.deb libntfs8_*.deb

    * Add fuse to the list of modules to load 

echo fuse | sudo tee -a /etc/modules

    * Create a user group to access the ntfs disks 

sudo addgroup ntfs

    * The output should look something like this, remember the GID (the number printed after the group name) as it may differ and we will need it later: 

    Adding group `ntfs' (1002)... 
    Done. 

    * Read #How to list partition tables 

    * Create the local mount folder and edit the fstab file to mount the disks to this folder. 

    e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS) 
    Local mount folder: /media/windows 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

    * Append the following line at the end of file, using the GID number previously. The umask following this GID allows write access just to owner (root) and group (ntfs), and read access to everyone. 

/dev/hda1    /media/windows    ntfs-fuse    auto,gid=1002,umask=0002    0    0

    * Save the edited file. 

    * Add users to the ntfs group, where "username" is the name of the user you would like to have write access 

sudo adduser username ntfs

    * Fix Dapper bug #29865 of the linux-ntfs package: 

sudo rm /sbin/mount.ntfs-fuse && sudo ln /usr/bin/ntfsmount /sbin/mount.ntfs-fuse

    * If you reboot now, the disk will be writable to the selected users when they logon. If you want the changes to take effect immediately without rebooting, execute the following command, ignoring the errors about "/" and others not being unmounted. You'll have to logout from all your user sessions for the new group to be acknowledged (usually a logout from your graphical session and login back again will do it). 

sudo modprobe fuse && sudo umount -a && sudo mount -a

---

### Post by marufsiddiqui on 2006-10-02
Thats will help I guess but there's another problem. I dont wanna make a new thread for this.

In one of my friends pc who is using Red Hat 9 on Samsung 80 GB HDD (notably only one drive), thats not the thing, I run Ubuntu Live on that PC & I can see thatdrive showing 74GB. but when I click the drive icon , it says i dont have permission or the drive is not mounted. my question that drive is a Linux file sys drive, Then why cant I access that drive

Now what I have to do to access that drive?

Thanks every1 4 support

---

### Post by dannyboy79 on 2006-10-02
well, the thing is that you said you are using a live cd. therefore it is running everything off the cd and that's it. what you need to do is find out what drive and partition you want to mount by doing, sudo fdisk -l. read thru those results and when you find the drive you want, you need to first make a mount point, in other words a directory for the info to show up. so you would do mkdir /media/friendzredhat or whatever you want the fodler to be. i would always mount it in the media folder but some people will tell you to mount in the mnt folder. hell you can mount whereever you want. then you need to change the permissions, the owner and the group owner of the folder you just created, so that you can do what you want with the files. then you shold be set. I have to be honest with you, you really need to read a website about the basics of linux. you'll learn about permissions, how data gets mounted and editable etc etc. i can't tell you how to edit the permissions because I forgot, i know it's something like chmod blah blah, then chown blah blah, then chgrp blah blah but you'll have to look it up in google. after do all this you will simply mount the drive by typing in, mount /dev/hdc2 /media/friendzredhat (that's if the partition and drive is hdc2), and then to see everything just go to the /media/friendzredhat folder and that's it. make sure you umount it before you take the drive out or unhook it!

---

